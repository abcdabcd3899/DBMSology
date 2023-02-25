# MorphoSys: Automatic Physical Design Metamorphosis for Distributed Database Systems

> 本文三位作者都来自滑铁卢大学数据系统实验室，其中一作和二作的研究方向集中在使用 Machine Learning 优化系统。作者分别为： [Michael Abebe](https://cs.uwaterloo.ca/~mtabebe/), [Brad Glasbergen](https://cs.uwaterloo.ca/~bjglasbe/), [Khuzaima Daudjee](https://cs.uwaterloo.ca/~kdaudjee/)</br>
> 论文链接: <https://cs.uwaterloo.ca/~kdaudjee/DaudjeeMorphoSysVLDB21.pdf>

[[TOC]]

## 1. Introduction

### 1.1 Motivation

分布式数据库系统为了增强性能，最小化资源和数据竞争，需要考虑:

* 数据放在哪里？
* 哪些数据需要 partition
* 哪些数据需要 replication

决策它们非常困难，当前的分布式数据库管理系统大都采用静态方法做上述决策。静态方法的缺点是
很难适应工作负载 (workload) 的变化。

### 1.2 Main Contribution

MorphoSys 能够适应工作负载的变化，从而动态选择、改变物理设计。它实现了:

* SSSI and partition-based concurrency control algorithm
* Lazily update propagation strategy based on the partition-based redo log using Apache kafka.
* Model the workload on-the-fly;
* a set of physical design change operators
* Add a learned cost model to get the latency of different physical design
* Make decision based on the learned cost model
* An extensive evaluation that establishes MorphoSys’ efficacy to deliver superior performance over prior ap- proaches.

> 这里的物理设计 (Physical Design) 主要指的是 partition 和 replication

## 2. System Overview

<img width="374" alt="截屏2022-09-23 17 26 40" src="https://user-images.githubusercontent.com/13810907/191931308-9abd0e72-5d5a-4908-84cd-5afcec987a57.png">

## 3. Transaction Execution and Phsical Design Change

<img width="615" alt="截屏2022-09-23 17 28 28" src="https://user-images.githubusercontent.com/13810907/191931676-9a87c600-1b85-4e2e-adf1-76bbd0763236.png">

### 3.1 Transaction Isolation and Concurrency

MorphoSys uses the strong-session snapshot isolcaion combined with the multiversion
concurrency control techique.

* SSSI: (1) Each of client cannot see the stale data. **How to guarantee it?** (2)
It exists the write skew the same as SI.
* MVCC: How to implement it? Using the versioned data items.

### 3.2 Patition-Based MVCC

<img width="309" alt="截屏2022-09-23 17 27 23" src="https://user-images.githubusercontent.com/13810907/191931450-dcb2a908-befa-494f-87c4-451ba1a7df2e.png">

* read operation cannot block write;
* write operation cannot block read;
* write-write conflicts use the lock to prevention, which avoid the roll back.

### 3.3 Update Propagation

It uses partition-based redo log using kafka, which includes the (1) transaction write operations, and (2) physical design change operations. The replicas replay the redo logs to install changes compared with partition version (v(p)).

### 3.4. Physical Design Change Execution

本文提出了 5 中 physical design change strategies:

* Adding Replica

For read partition.

* Removing Replica

For low access frequence of partitions. 删除时需要注意采用 reference-count 确保正在访问的 tx 不受影响。

* Splitting Partitions

Fix the contention of w-w conflicts. split 时不产生新的 v(p), 在 split 过程中，所有 ongoing 的事务能访问原先的 partition，所有新的事务都不能访问旧的 partition.

* Merging Partitions

For low access frequence of partitions. merge 会产生新的 $v(p) = max(v(p_{L}), v(p_{H}))$，接着需要确保 merge 之后的版本为 master.

* Changing Partition Mastership

w-w tx occurs on the same nodes, which avoid 2PC.

## 4. Physical Design Strategies

本文最核心的部分。

### 4.1 Workload Model

1/. workload model = access pattern of partitions, 它可以分为两个部分:

* 单个 partition 的 R(p) 和 W(p)
* Partitions 之间的读写关系, 如 P(r(p2)|r(p1))、P(w(p2)|r(p1))、P(r(p2)|w(p1))、P(w(p2)|w(p1))，需要计算各种 partition access pattern
* 如果某个访问模式的概率远低于相同情况下的平均值，那么我们有理由破坏这种访问模式 (即可能会 split 或者 merge partition)

2/. 由于 transaction Router 是 in-memory，同时为了更好地建模 workload model，采用了 reservoir sampling 抽样 transactions。

### 4.2 Learned Cost Model

Q1: 如何量化 5 种 physical design operations?

A1: 将 5 种物理操作转换为 5 种系统延时，它们分别是：
（1）waiting for service; (2) wait for updatel; (3) accquire the locks; (4) r

Q2: 这五种延时如何表示一个 physical design operation?

<img width="587" alt="截屏2022-09-23 17 29 05" src="https://user-images.githubusercontent.com/13810907/191931813-771c051a-9d7d-4bf7-bc24-7aff9d2bfb24.png">

Q3: 这些 latency 分别代表什么含义？ 如何量化？

A3: 这里我们不去讨论所有的 latency ，用 waiting for service 举例说明。节点上的负载决定了响应用户请求的速度，

负载越高，响应请求的延时越高。因此，我们建模 waiting for service 建模为平均 CPU 利用率，transaction router 会定期轮询得到平均 CPU 利用率。因此，我们建模 $ F_{service}(C_{s} = cpu.util(S)) $，本文统一采用线性模型建模参数与 latency 之间的关系，所以，$F_{service} = WC_{s} + b$. 我们可以从系统中精确的得到 $F_{service}$ 延时，采用随机梯度下降，选择一种 loss 便可以训练得到 W 和 b 的值，从而刻画了 waiting for service 延时。**论文没有明确给出具体的 loss。** 其他指标这里将不再赘述，感兴趣的同学请看原文。

Q4: 这个表格我们如何使用?

A4: 以 split 操作为例，$$ Latency(split) = F_{service}+F_{lock}(w) + F_{commit}(r_p, w_p) $$，这里的 $Latency(split)$ 也能被 MorphoSys 精确刻画。

> 据此，我们得到了一组 latency 关系。接下来问题是，如何应用这一组 latency 决策是否要发生 physical design change?

### 4.3 Physical Design Change Decisions

Q5: 如何决策是否发生 physical design change?

A5: 引入两个度量标准，它们分别是$E(S)$ 和 $C(S)$. 其中 $E(S)$ 表示 Expected Benefits, $C(S)$ 表示执行操作符之和。以 split 为例， $C(S) = F_{service}(c1) + F_{lock}(W(0,9)) + F_{commit}(0, 3)$. $E(S) = L_{current} - L_{future}$， 其中 $L_{current} = f_{locks}(0,9)$, $L_{current} = f_{locks}(0,5) + f_{locks}(6, 10)$, 如果 $E(S) > 0$ 说明当前 plan 有可能包含一个 split 操作。 但是我们仍然需要检查其它的操作是否也能够满足 $E(S) > 0$, 因为 $E(S) > 0$ 表示当前 plan 能够改进系统性能。 当我们筛选出所有满足 $E(S) > 0$ 的 plan之后，满足 $net(S) = max{\lambda E(S) - C(S)}$ 即为最终选择出的 plan。

> net(S) 指的是最大化收益，经济学概念，在本文中并未详细介绍此概念。
> 这里实际上还存在一个问题，是否注意到，我们在求解 $E(S)$ 时实际上 L_{future} 我们无法从未来的访问模式中得到，因为它并未发生。该部分实际上是从历史数据中得到的，除此之外，MorphoSys 还会模拟一些 workload 的访问模式，从而是的建模更加准确。

## 5. Experimental Evalution

1/. Evaluated Systems

**clay**: dynamically partition based on the data access frequency, repartition per 10 seconds. Using 2PC to execute the transactions.

**ADR**: Adaptive replication. Dynamically determine what data to replicate, and where. Using 2PC to execute tranasaction.

**single-master**: all partition put on the master node. Update occur on the master node, read-only on the replicas.

**multi-master**: Common distributed database systems.

**DynaMast**: Transaction occurs on the single node by using remaster operation.

**VoltDB**: Static physical design.

2/. Benchmarks

16 data nodes, each having 12-cores 32 GB RAM, one transaction router machine, update propagation uses the Apache kafka. 每个结果都取 5 次平均值，5 分钟 OLTPBench， 置信区间 95%。

3/. datasets

* YCSB: 50 million data 顺序读 200-1000 keys

* TPC-C: update intensive transactional workload

* Twitter: read intensive workload (89%)

* SmallBank: bank application

4/. 实验结论就是一句话: MorphoSys 系统的 latency 最低、Throughput 最大.

## 6. Conclusion

* We presented MorphoSys, a distributed database system that automatically modifies its physical design to deliver excellent performance.
* MorphoSys integrates three core aspects of distributed design: grouping data into partitions, selecting a partition’s master site, and locating replicated data.
* MorphoSys makes comprehensive design decisions using a learned cost model and efficiently executes design changes dynamically using a partition-based concurrency control and update propagation scheme.

## 7. Expected

We expect MorphoSys ability to generate and adjust distributed physical designs on-the-fly without prior workload knowledge to pave the way for the development of self-driving distributed database systems.
