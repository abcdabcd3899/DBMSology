# Database Systems Reading List

![Github stars](https://img.shields.io/github/stars/abcdabcd3899/DBMSology-Darkness.svg)
![License](https://img.shields.io/github/license/abcdabcd3899/DBMSology-Darkness.svg)
![Stars](https://img.shields.io/github/forks/abcdabcd3899/DBMSology-Darkness.svg)

I'm interested in the intersection between machine learning and systems. You are welcome to make a pull request!

## Paper Survey

### Workload Management

***
[The workload features include workload types, workload shifts, workload patterns (e.g., periodic pattern and arrival patterns),
and the performance is measured by one of the metrics (response time, throughput, reliability, etc.) or their combination.](http://chunbinlin.com/publication/icde_2021_tutorial.pdf) And I think workload pattern should includes **workload access pattern**.
Therefore, I have collected and organized the following list, and will analyze these papers in detail later.

> our approach uses the logical composition of queries in the workload rather than the amount of physical resources used for query execution. - Query-based Workload Forecasting for Self-Driving Database Management Systems. (**So, this means that workload has twofolds: 1. the logical composition of workload; 2. the resources used for query execution**)

Workload features may include:

- workload types
- workoad shift
- workload pattern
  - periodic pattern
  - arrival pattern
    - arrival rate
    - next query/ next query composition
    - volume of the queries
  - access pattern of physical composition (e.g. pages)
- resource metrics (resources user for query execution. e.g. disk utilization)
- logical composition (SQL template)
- raw SQL

Tasks include for demonstrate workload model effectiveness:

- index select and index recommendation
- performance tuning
  - parallel execution schedule
  - query schedule
  - query performance prediction
- physical design metamorphosis
- predictive caching/prefetch
- query recommendation
- resource scaling

![survey1231-2](https://user-images.githubusercontent.com/13810907/210230121-6ccd07fe-d994-49cc-802f-c6bf53cfdae6.png)
***

#### Predictive Caching using Query Correlations

***

- [Apollo: Learning Query Correlations for Predictive Caching in Geo-Distributed Systems](https://cs.uwaterloo.ca/~bjglasbe/papers/apollo.pdf) **EDBT 2018 CCF B** 🌟🌟🌟🌟🌟

- [ChronoCache: Predictive and Adaptive Mid-Tier Query Result Caching](https://dl.acm.org/doi/abs/10.1145/3318464.3380593) **SIGMOD 2020 CCF A** 🌟🌟🌟🌟🌟
- [Maxson: Reduce Duplicate Parsing Overhead on Raw Data](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9101499) **ICDE 2020 CCF A** 🌟🌟🌟🌟🌟
- [Revisiting Reuse in Main Memory Database Systems](https://cs.brown.edu/~kayhan/papers/hashstash.pdf) [demo](https://blog.pythian.com/issues-plan-cache-reuse-row-goal-optimization/) [plan caching](https://help.sap.com/docs/SAP_HANA_PLATFORM/bed8c14f9f024763b0777aa72b5436f6/bed20ba0bb57101483ffa333cf3e55c8.html) [SQL](https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/zh/cn/top_10_tips_for_optimizing-final_cn.pdf)

#### Workload Access Pattern [Tutorial PPT](https://cs.uwaterloo.ca/~bjglasbe/presentations/mw_tutorial.pdf) [Tutorial paper](https://cs.uwaterloo.ca/~kdaudjee/AdaptiveTutorial.pdf) 🌟🌟🌟🌟🌟

- [Tiresias: enabling predictive autonomous storage and indexing](https://dl.acm.org/doi/abs/10.14778/3551793.3551857) **VLDB 2022 CCF A** 🌟🌟🌟🌟🌟

- [MorphoSys: Automatic Physical Design Metamorphosis for Distributed Database Systems](http://vldb.org/pvldb/vol13/p3573-abebe.pdf) **PVLDB 2020 CCF   A** 🌟🌟🌟🌟🌟
- [Proteus: Autonomous Adaptive Storage for Mixed Workloads](https://cs.uwaterloo.ca/~mtabebe/publications/abebeProteus2022SIGMOD.pdf) **SIGMOD 2022 CCF A** 🌟🌟🌟🌟🌟

#### Workload Time Series Analysis

- [Database Workload Capacity Planning using Time Series Analysis and Machine Learning](https://dl.acm.org/doi/pdf/10.1145/3318464.3386140) **SIGMOD 2020 research track CCF A**
- ~~Morkov Modeling for Workload Shift~~ 🌟 ❌
  - [~~Towards workload shift detection and prediction for autonomic databases~~](https://dl.acm.org/doi/abs/10.1145/1316874.1316892) **CIKM 2007 CCF B**
  - [~~Autonomic databases: Detection of workload shifts with n-gram-models~~](https://dl.acm.org/doi/10.1007/978-3-540-85713-6_10) **2008**
  - [~~Towards workload-aware self-management: Predicting significant workload shifts~~](https://ieeexplore.ieee.org/document/5452738) **ICDE workshop**

#### Encoder to Vector 🌟🌟🌟🌟🌟

- [Database Workload Characterization with Query Plan Encoders](https://dl.acm.org/doi/pdf/10.14778/3503585.3503600) **VLDB 2022 research track** **CCF A**
- [LSched: A Workload-Aware Learned Query Scheduler for Analytical Database Systems](https://dl.acm.org/doi/pdf/10.1145/3514221.3526158) **SIGMOD 2022 research track CCF A**
- [Query2Vec: An Evaluation of NLP Techniques for Generalized Workload Analytics](https://arxiv.org/pdf/1801.05613.pdf) **arxiv**
- [Flexible Operator Embeddings via Deep Learning](https://arxiv.org/pdf/1901.09090.pdf) **arxiv**
- [Database-Agnostic Workload Management](https://faculty.washington.edu/billhowe//publications/pdfs/jain_cidr_2019.pdf) **CIDR 2019 CCF B**

#### ~~Workload Synthesis~~ 🌟🌟

- [~~Stitcher: Learned Workload Synthesis from Historical Performance Footprints~~](https://openproceedings.org/2023/conf/edbt/paper-19.pdf) **EDBT 2022 CCF B**
- [~~Relational Data Synthesis using Generative Adversarial Networks: A Design Space Exploration~~](http://iir.ruc.edu.cn/~fanj/papers/vldb2020-p1962-fan.pdf) **VLDB 2020 CCF A**

#### Next Query

- [Workload-Aware Query Recommendation Using Deep Learning](https://openproceedings.org/2023/conf/edbt/paper-173.pdf) **EDBT 2023 CCF B** 🌟🌟🌟🌟
- [~~Evaluation of Machine Learning Algorithms in Predicting the Next SQL Query from the Future~~](https://dl.acm.org/doi/pdf/10.1145/3442338) **TODS 2021 CCF A** 🌟🌟🌟🌟🌟

#### Workload Arrival rate and Trend Pattern Forecasting 🌟🌟🌟🌟🌟🌟🌟

- [Query-based Workload Forecasting for Self-Driving Database Management Systems](https://www.pdl.cmu.edu/PDL-FTP/Database/sigmod18-ma.pdf) **SIGMOD 2018 research track CCF A** 🌟🌟🌟🌟
- [MB2: Decomposed Behavior Modeling for Self-Driving Database Management Systems](https://dl.acm.org/doi/pdf/10.1145/3448016.3457276) **SIGMOD 2021 CCF A**
- [~~DBAugur: An Adversarial-based Trend Forecasting System for Diversified Workloads~~](https://dbgroup.cs.tsinghua.edu.cn/ligl/papers/workload-forecast-icde23.pdf) ~~**ICDE 2023 CCF A** 🌟🌟🌟🌟🌟🌟🌟
- [~~LightPro: Lightweight Probabilistic Workload Prediction Framework for Database-as-a-Service~~](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9885759) ~~**ICWS 2022 CCF B**
- [~~OtterTune: Automatic Database Management System Tuning Through Large-scale Machine Learning~~](https://www.cs.cmu.edu/~ggordon/van-aken-etal-parameters.pdf) **SIGMOD 2017 CCF A** 🌟
- [Intelligent Automated Workload Analysis for Database Replatforming](https://dl.acm.org/doi/pdf/10.1145/3514221.3526050) **SIGMOD 2022 Indursty track CCF A** 🌟🌟 Expert Experience + Feature Cost Modeling
- [~~Active Learning for ML Enhanced Database Systems~~](https://dl.acm.org/doi/pdf/10.1145/3318464.3389768) **SIGMOD 2020 research paper CCF A**
- [SWIRL: Selection of Workload-aware Indexes using Reinforcement Learning](https://openproceedings.org/2022/conf/edbt/paper-37.pdf) **EDBT 2022 research paper CCF B**
- [~~Self‑driving database systems: a conceptual approach~~](https://d-nb.info/1211224805/34)
- [Facilitating SQL Query Composition and Analysis](https://15799.courses.cs.cmu.edu/spring2022/papers/12-workload2/zolaktaf-sigmod2020.pdf) **SIGMOD 2020 CCF A**
- [Performance and Resource Modeling in Highly-concurrent OLTP Workload](https://dl.acm.org/doi/10.1145/2463676.2467800)

#### Modeling  System Load as Workload

- [P-Store: An Elastic Database System with Predictive Provisioning](https://rytaft.github.io/pstore.pdf) **SIGMOD 2018 Industry paper CCF A** 🌟🌟🌟🌟🌟
- [Moneyball: Proactive Auto-Scaling in Microsof Azure SQL Database Serverless](https://dl.acm.org/doi/pdf/10.14778/3514061.3514073) **CCF A VLDB** 🌟🌟🌟🌟🌟🌟🌟🌟
- [Seagull: An Infrastructure for Load Prediction and Optimized Resource Allocation](http://vldb.org/pvldb/vol14/p154-poppe.pdf) **CCF A VLDB** 🌟🌟🌟🌟🌟🌟🌟🌟
- [Resource Central: Understanding and Predicting Workloads for Improved Resource Management in Large Cloud Platforms](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/10/Resource-Central-SOSP17.pdf) **SOSP 2017 CCF A**
- [Automated Demand-driven Resource Scaling in Relational Database-as-a-Service](https://dl.acm.org/doi/10.1145/2882903.2903733) **SIGMOD 2016 CCF A**

#### Query Performance Predict

- [Query Performance Prediction for Concurrent Queries using Graph Embedding](http://www.vldb.org/pvldb/vol13/p1416-zhou.pdf) **VLDB 2020 research track CCF A** 🌟🌟🌟🌟
- [Plan-Structured Deep Neural Network Models for Query Performance Prediction](https://www.vldb.org/pvldb/vol12/p1733-marcus.pdf) **VDB 2019 CCF A** 🌟🌟🌟🌟
- [Towards Predicting Query Execution Time for Concurrent and Dynamic Database Workloads](http://www.vldb.org/pvldb/vol6/p925-wu.pdf) **VLDB 2013 CCF A**
- [Predicting query execution time: Are optimizer cost models really unusable?](https://ieeexplore.ieee.org/document/6544899) **ICDE 2013 CCF A** 🌟🌟🌟🌟

#### Tutorial

- [Make Wise Decisions for Your DBMSs: Workload Forecasting and Performance Prediction Before Execution](https://tuhat.helsinki.fi/ws/portalfiles/portal/210925634/Tutorial_DASFAA_2022_Proposal.pdf) **DASFAA 2022 CCF B** [Video](https://www.youtube.com/watch?v=vA3UcJuO2Fc) 🌟🌟🌟🌟🌟
- [Workload-Aware Performance Tuning for Autonomous DBMSs](http://chunbinlin.com/publication/icde_2021_tutorial.pdf) **ICDE 2021 CCF A** 🌟🌟🌟🌟🌟
- [Tutorial: Adaptive Replication and Partitioning in Data Systems](https://cs.uwaterloo.ca/~kdaudjee/AdaptiveTutorial.pdf) **Middleware 2018 CCF A** 🌟🌟🌟🌟🌟

#### System includes Workload Profile

- [Make Your Database System Dream of Electric Sheep: Towards Self-Driving Operation](https://db.cs.cmu.edu/papers/2021/p3211-pavlo.pdf) **PVLDB 2021 CCF A**
- [Self-Driving Database Management Systems](https://app.oarklibrary.com/file/2/562c59df-0e06-47f8-9ee7-10858c27f740/abd195b1-9081-4e03-b204-70abd3b0656e.pdf)

#### PhD Thesis

- [Adaptive Data Storage and Placement in Distributed Database Systems](https://uwspace.uwaterloo.ca/handle/10012/18704)

#### Master Thesis

- [PROMISE: Modeling and PredictingUser Behavior for Online Analytical Processing Applications](https://d-nb.info/962681628/34)

#### Tools

- [https://www.exact-solutions.com/ireplay](https://www.exact-solutions.com/ireplay)
- [Amazon WLM](https://docs.aws.amazon.com/redshift/latest/dg/cm-c-implementing-workload-management.html)

#### Caching and Prefetch based Workload Modeling

- [Netco: Cache and I/O Management for Analytics over Disaggregated Stores](https://www.microsoft.com/en-us/research/uploads/prod/2018/08/socc18-final129.pdf) **SoCC 2018 CCF B** 🌟🌟🌟🌟🌟🌟
- [Sharing Buffer Pool Memory in Multi-Tenant Relational Database-as-a-Service](https://dl.acm.org/doi/pdf/10.14778/2752939.2752942) **CCF A VLDB 2015**

#### Automation Diagnosis

- [APOLLO: Automatic Detection and Diagnosis of Performance Regressions in Database Systems](https://taesoo.kim/pubs/2020/jung:apollo.pdf) **PVLDB 2019 CCF A**
- [Diagnosing Root Causes of Intermittent Slow Queries in Cloud Databases](http://www.vldb.org/pvldb/vol13/p1176-ma.pdf) **PVLDB 2020 CCF A**
- [SQLCheck: Automated Detection and Diagnosis of SQL Anti-Patterns](https://dl.acm.org/doi/10.1145/3318464.3389754) **SIGMOD 2020 CCF A**
- [A Top-Down Approach to Achieving Performance Predictability in Database Systems](https://dl.acm.org/doi/pdf/10.1145/3035918.3064016) **SIGMOD 2017 CCF A**
- [DBSherlock: A Performance Diagnostic Tool for Transactional Databases](https://web.eecs.umich.edu/~mozafari/php/data/uploads/sigmod_2016.pdf) **SIGMOD 2016 CCF A**
- Adaptive Data Storage and Placement
  - MorphoSys: Automatic Physical Design Metamorphosis for Distributed Database Systems</br>
    [论文介绍](https://github.com/abcdabcd3899/DBMSology/edit/master/MorphoSys.md)

### Index

- SuRF: Practical Range Query Filtering with Fast Succinct Tries
2018 sigmod best paper，该论文出自andy pavlo的学生。andy在数据库方面有独特的见解。bloom filter在disk-oriented database management system中有特别的作用：在内存快读判断一个key是否存在，这些key就是存储的磁盘上的数据本身。该结构存在两个主要问题：（1）bloom filter存在“one-side error”也就是说：if key is present, then bloom filter returns true. 该命题的逆否命题是：如果bloom filter返回false，那么说明key一定不存在。（2）bloom filter只支持point query，但是不支持range query。针对bloom filter存在的第一个问题，要从设计合适的hash function等角度入手解决，比较难。针对第二个问题，SuRF采用了FST数据结构解决了不支持范围查询的问题，能够给出开区间[key, +inf）,[key1, key2], (-inf, +inf)上的range query问题。

- SAL-Hashing： A Self-Adaptive Linear Hashing Index for SSDs</br>
The Case for Learned Index Structures</br>
Google在系统索引与Deep Learning结合的研究，ML for Sytstem是当前的研究热点。缺点是不能执行update操作。
  - ALEX: An Updatable Adaptive Learned Index</br>
上篇文章的作者改进Update操作的文章。
  - Learning Multi-dimensional Indexes</br>
上篇文章作者在多维索引上的工作进展。
  - XIndex: A Scalable Learned Index for Multicore Data Storage</br>
    - XIndex： A Scalable Learned Index for Multicore Data Storage - extention </br>
上海交通大学陈海波组在学习型索引上的研究进展。
- The Ubiquitous B-Tree</br>
- The Bw-Tree: A B-tree for New Hardware Platforms</br>
Bw-Tree 是 2013 年 Microsoft 发表在 ICDE 上的工作，该工作主要是面向 Flash 设备的 Lock-free 的 B+tree 变种。falsh 设备具有高效的随机读和顺序读特性，但是由于 flash 写操作需要先擦后写，因此写性能较差，针对 flash 的特性，本文提出了 delta update，即所有的修改都会生成一个 delta 部分，并且将 delta 部分和 base page 通过指针链起来，同时记录修改日志，同样遵循 delta 部分刷盘之前需要先将日志刷盘，并且我们注意到：当发生修改操作时，由于开辟了新的空间记录了 delta 修改，因此刷盘时只需要将 delta 刷回去即可。这样一方面减少了写放大，还减少了 flash 设备的垃圾（因为base page 在后续部分将会被GC，如果频繁启动 GC，会导致磁盘压力过大，影响 flash 读写性能）。同时在写负载很大的情况下，每个写操作都会产生 delta，使得同一个 base page 的修改链过长，本文提出：当链长度达到某个阈值之后会启动 page merge 过程 （论文中说这个 page merge 可以由任意访问线程来做，访问线程就是任意的读写线程，但是我觉得后台有一个 merge 线程可能会更好一些）。整个lock-free 都要能保证 “我不阻塞、别人不傻等” 的原则。本文隐藏了很多实现细节，由于是 GC 过程，如果有机会，希望能实现该算法。
- BzTree: A High-Performance Latch-free Range Index for Non-Volatile Memory</br>
- Modern B-Tree Techniques</br>
- Efficient Locking for Concurrent Operations On B-Trees</br>
CMU大佬巨作 B-Link tree。
- Easy Lock-Free Indexing in Non-Volatile Memory</br>
- Persistent Bloom Filter Membership Testing for the Entire History
- LSM-based Storage Techniques: A Survey</br>
该文的特点是简单易懂。
  - Evaluation of High Performance Key-Value Stores</br>
学习leveldb很好的指导论文。

### Sorting

- Implementing Sorting in Database Systems</br>
Goetz Graefe老爷子大作，他写了关于B-tree、Volcano查询处理模型等。

### Architecture

- Weaving Relations for Cache Performance</br>
本文充分吸取了 NSM 和 DSM 数据组织模型的优势，提出了对缓存更加友好的 page 内数据组织方式 PAX，该部分 story 参见 <https://github.com/abcdabcd3899/DBMSology/blob/master/PAXStory.md>

- F1 Lighting: HTAP as a Service

- Are You Sure You Want to Use MMAP in Your Database Management System? </br>
andy 在 2020 年的讲座中说自己要写一篇关于 MMAP 的文章，2 年后终于见面了，文章发表在 CIDR 2022 上，7 页很短，但是内容很丰富，结论是 **不要在数据库中使用 mmap 代替手动 buffer pool 管理**.
- To BLOB or Not To BLOB: Large Object Storage in a Database or a Filesystem?<br>
本文主要讲述对于Binary Lager OBject（BLOB）究竟应该存储在database中使用DBMS管理还是应该用Filesystem来管理，即究竟BLOB应该作为一个数据库record还是file？
文章支持当文件系统是NTFS，DBMS是SQL Server 2005时，当文件大小下雨256KB时，DBMS管理更加高效，当对象大于1MB时，采用filesystem管理更加高效。文章还提出数据库
设计者应该考虑加入文件系统的碎片整理过程。**注：现今，当我们在存储视频等比较大的文件时，尽量不要直接用BLOB存储在数据库中，而是应该用filesystem管理，在数据库中可用只存储文件链接。**

- Architecture of database system </br>
数据库体系结构最好的文章。作者图灵奖得主Stonebraker。包括processes model、query processing、storage and transaction、others，其中的事务存储部分严格区分了lock和latch，一个是higher level的概念，一个是lower lavel的概念。这两个改变在实现buffer pools时非常重要，latch在使用上，实际上用mutex来实现。lock是higher level事务层面用到的抽象。

- The Snowflake Elastic Data Warehouse  (sigmod 2016)</br>
本文是一种标准的shared disk的架构。体现在两个方面：1、（1）整体架构分为三层：Storage layer由Amazon S3提供，仅仅能够提供put、get、delete操作，并且put操作只能是全量（in full）操作。get操作可以指定文件读取的范围。（2）stateless VM是，之所以说该层是stateless是因为：实际上该层的disk是cache的作用，用于系统的冷启动问题。该层可以和storage层独立扩展。（3）cloud service层，该层提供传统的数据库服务：事务管理、元数据管理（元数据持久到S3上），查询解析，查询优化等数据库传统的功能，但是不提供索引。列存数据库的列其实本身就是索引。底层为了避免全文件扫描，还实现了zone map（google、oracle对zone map可能拥有商标权）可以实现skip scan。该层也是stateless。2、online-upgrade时，实际上VMs层也是shard disk的架构，这样能够保证不同版本的系统在读取数据时，能够访问到相同的热数据。snonflaker实现了很多数据库中的经典技术，如MVCC并发控制方法（请注意MVCC不是并发控制协议，它需要和其它的如2PC、TO结合才能称为协议）、time travelling这是数据仓库中比较有用的技术，能够访问指定时间段的数据，snowflake指定只能访问90天以内的数，不过你能够自行实现backup、基于MVCC的SI隔离级别，在此基础之上保证了ACID事务等等。

- FlashKV Accelerating KV Performance with Open-Channel SSDs (2017)</br>
- MapReduce：Simplified Data Processing on Large Clusters</br>
MapReduce一文确实是一篇极好的文章，按照其思想，它的输入输出全部存储在GFS（开源实现下，将数据存储在HDFS之上）上。从用户的角度看，不需要考虑load balance、communication等，只需要写业务
端程序，也就是只需要设计合适的map和reduce函数即可，当然为了减少network communication代价，也可以写combiner function，实际上map和reduce阶段的操作就是两次hash。map tasks+reduce tasks= job，
也就是说多个map tasks 和 多个reduce tasks构成一个job，map生成的intermmidiate key/values会存储在当前map节点的non-volatile存储设备上。接着master会调度将这些结果重新shuffle，然后将结果
调度给reduce tasks，尽量保证不同reduce任务之间减少network communication。
- GFS: The Google file system</br>
Google经典三篇文章之一，GFS是google真正对工业界在数以千计的廉价商业化机器上实现的分布式文件系统，其设计包含一个master节点（为了保证reliable等特性，该机器通常会有replicas），一次写操作
成功不仅需要在所有的chunkserver上写入数据，还需要master节点的operation logs落盘，master节点与传统单机DBMS的设计一样。master节点不真实存储任何client数据，client数据全部存储在chunkserver上，
master节点保存三件事情：（1）filename -> array of chunk handler, （2）chunkhandler -> list of chunkserver, （3）logs and checkpoints，可以看出第一点和第二点主要是为了能够找到文件的真实位置，
第三点主要是为了实现可靠性和可恢复性。当client节点将请求发送到master之后，master会将用户请求的所在的chunkserver位置发送给client，并且client端会缓存这些信息，以便于当client再次请求相同的数据时，
不需要再次请求master，那么此时就有一个数据的一致性问题，一旦映射关系发生变化（比如某个chunkserver fails），这个cache信息就会失效，或者设计一个lease，给定时间窗口内有效，一旦过时cache就立即
停止服务。在GFS中假设发生追加写操作的可能性远远大于随机写操作。
- Bigtable: A Distributed Storage System for Structured Data</br>
Google经典三篇文章之一，在Bigtable基础之上，Google实现了leveldb。bigtable实际上是一张”宽表“，我们知道，在经典的关系数据库范式理论中，首先数据库的表设计应该满足第一范式，也就是表中的属性不能再分，
但是Bigtable使用了column family的特性，使得表的列属性实际上是可分的，同一个column family中可以有多个不同的列，这样子构成了bigtable的宽表模式。row-key按照字典序排序，并且row-key组合成了bigtable的tablet，每个tablet中
可能包含很多个row-key，然后这些在内存中被组织成为memtale，当memtable达到一定的大小以后，就变为immutable memtable，接着被compaction成为SSTable，SSTtable也会被major compaction，当生成更大的SSTable之后，就会删除
原来的SSTable，所以这个过程实际上存在非常多的写放大。为了出现fails时能够恢复，还存在了redo log，这一设计完全是从关系数据库的ARIES中迁移而来。最后还介绍了不少优化，我认为想要真正读懂这个文章
的所有优化，尽量结合着leveldb的源码，并做一些实验。
- Dynamo: Amazon’s Highly Available Key-value Store</br>
Dynamo是Amazon在2007年SOSP上发表的关于键值对存储的分布式系统，主要强调高可用、强扩展，使用读操作之后的最终一致性方案，这在2020年看来并不是一个好的选择，
强一致性仍然是当前的需求。但是这不影响Dynamo成为高引用文章，其中很多的技术都成为很多数据库设计的规范。Dynamo的强扩展性（scale-out）采用了consistent hashing，
当在其中增加或者删除node时，不要执行reshuffle（rehash）的操作，当然consistent hasing不是Dynamo提出的技术，早在2000年就提出consistent hashing。
读操作和写操作都松散的希望能得到系统中至少半数点的回应，但是考虑到可能存在网络分区等错误，所以仅仅是一个松散的建议，在写操作时，如果某个ring中的节点失去了联系，
那么就讲备份数据写到下一个ring中，并记录好，等待该节点恢复后，再将数据拷贝过去。
Dynamo在读操作也希望能有半数以上的节点返回数据，读出的数据会带有数据版本（文章中称为vector clock），如果发现数据不一致，允许在系统层面进行规约，但是不强制，
因为Dynamo允许业务逻辑层处理数据的不一致性（比如在Amazon中，用户的购物车可以由用户自己来维护其一致性）。其中Grossip-based的协议实现信息在节点中的传播，
这些古老的技术都在Dynamo得到了很好的应用。可以说Dynamo是结合了很多优秀实现技术的一个原型产品，堪称教科书式的实现。
- Amazon DynamoDB: A Scalable, Predictably Performant, and Fully Managed NoSQL Database Service </br>
- (SPARK)Resilient Distributed Datasets：A Fault-Tolerant Abstraction for In-Memory Cluster Computing</br>
- Granularity of Locks and Degrees of Consistency in a Shared Data Base</br>
jim gray首次在提出granularity of lockable object，也就是被锁对象的粒度，粒度这个词很抽象，在这里granularity = size指的是被锁对象的大小。该文提出了intension lock，使得在系统的并发度和overhead of lock manager
上做了trade-off，本质上，在被锁对象层次结构下，意向锁的提出了解决了这样两个问题：（1）如果low level层次对象加了锁，那么其祖先节点现在想要做某个查询，如何快速判断是否能够获取到锁执行相应的操作？（2）如果high level
节点获取了某种锁，接着另外一个事务想要在其孩子节点上做某些操作，是否能够直接获取到某种锁并执行相应的操作？因为本文提出了意向锁+root到leaf的加锁顺序，规范了整个lock protocol。
- Spark SQL: Relational Data Processing in Spark</br>
- [Spanner: Google’s Globally-Distributed Database](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/65b514eda12d025585183a641b5a9e096a3c4be5.pdf)<br>
- Spanner: Becoming a SQL System</br>
- F1: A Distributed SQL Database That Scales</br>
- Amazon Aurora: Design Considerations for High Throughput Cloud-Native Relational Databases</br>
- HadoopDB: An Architectural Hybrid of MapReduce and DBMS Technologies for Analytical Workloads or Integration of LargeScale Data Processing Systems and Traditional Parallel Database Technology</br>
- Soft Updates: A Solution to the Metadata Update Problem in File Systems</br>
- Rethinking Database High Availability with RDMA Networks</br>
- CockroachDB: The Resilient Geo-Distributed SQL Database (SIGMOD 2020)
- C-Store: A Column-oriented DBMS</br>
- Morsel-Driven Parallelism: A NUMA-Aware Query Evaluation Framework for the Many-Core Age (SIGMOD 2014)</br>
 该论文由 TUM 和 CWI 合作完成，其中 CWI 参与老师是 MonetDB 和 Vectorwise 的创始人。这篇文章的背景是如何高效利用 many-core 硬件，当前数据库的查询处理引擎在设计上没有充分发挥出硬件的价值，该文在 Hyper-db 上重写了查询执行模块，包括：聚集、hash join、排序等典型的操作符。本文提出了以 Morsel 为基础的查询执行过程，Morsel 实际上就是 batch 或者 vector，这是当前数据库管理系统在向量化设计上的一大亮点，称为 batch-at-a-time 的计算模型。

### Consensus

- [The Part-Time Parliament](https://www.microsoft.com/en-us/research/uploads/prod/2016/12/The-Part-Time-Parliament.pdf)
- Paxos Made Simple</br>
- Paxos Made Live</br>
- raft: In Search of an Understandable Consensus Algorithm </br>
- (raft-ATC)In Search of an Understandable Consensus Algorithm</br>

### Distributed Transaction

- Linearizability : A Correctness Condition for Concurrent Object</br>
- Sequential consistency versus linearizability</br>
- Strong and Efficient Consistency with Consistency-Aware Durability (FAST 2020 best paper)</br>
该篇文章是FAST 2020 best paper，主要讲述了在分布式存储系统中durable数据时，如何在保证strong consistency的前提下，实现higher throughput 和 lower latency，在传统的强一致性模型下，由于每一次数据修改操作都需要immediately将数据从master同步到follower上，这个过程在分布式场景下，会严重降低系统性能。本文作者观察到：在强一致模型下，如果能够保证一个cross-client 单调读的特性，那么我们就可以采用乐观的方式进行写后的读操作。本文的的方法我认为叫做optimistic read会更加的贴切，当我某个出follower中的数据时，会和durable index比较，就能够得出是否当前该数据版本是最新的，如果不是，那么系统就会在此时锁定将数据从主节点复制过来并且完成持久化，并返回结果给客户端；如果是最新的，那么直接返回给客户端结果。乍看来，这样子系统的性能岂不是会很差？但是其实不是，因为就像乐观并发控制协议一样，作者假设大部分情况下分布式系统的后台进程会将数据从master持久到replicas中，并且在存在follower的情况下，你请求到replica，并且这个数据恰好不是最新的可能性不大，**除非系统在频繁更新数据，并且也在频繁读取更新过的数据，这样性能的性能会发生抖动**。本人还解决了存在网络分区情况下的数据的读取，如果存在网络分区，那么系统会原子地保证分区节点从active set中剔除出去，这样在分区节点上的读操作就会被锁定，不允许从这个节点读取数据，等待分区情况解决之后，会重新持久最新的数据到分区节点上，并将其加入到active set中，保证单调读特性。本文的实现很优美，我觉得是durable和consistency实现中的一股清流。
- Hermes: a Fast, Fault-Tolerant and Linearizable Replication Protocol</br>
该篇文章出自ASPLOS'2020，基于广播的member-ship协议，时间复杂度为O(logn)，和Dynamo中的gossip-based确认ring中节点是否alive方法很像，实现比较经典。

### Distributed Systems

- Time, Clocks and Ordering of events
  - Time, Clocks, and the Ordering of Events in a Distributed System</br>
论文主要讲述了Lamport Clocks，并且区别了time-of-day（wall） clock， monotonic clock, and logical clock inicluding Lamport clock and vector clock。
  - detecting causal relationships in distributed computations in search of the holy grail</br>
vector clock在分布式系统中是一个更重要的概念，可以用来解释happened before relations、causal order and FIFO order。

### Lock-free data structure

- Lock-Free Data Structures</br>
对于熟悉多线程编程的programmer来说，大家很熟悉应该使用各种lock（shared lock、exclusive clock、unique lock）等锁定critical section部分，这种方法通常称为latch-full，使得可能发生race condition的critical section部分能够被串行化访问，实际上这是一种非常低效的访问方式，比如：当两个线程访问相同的B+-tree的叶子节点做范围扫描，并且两者分别向相对（如 ->  B+-tree leaves  <-）的方向访问，这样的情况下很容易造成死锁，我们需要更多的机制来避免这样的情况的发生，最简单的方法是在访问开始时，获得所有需要访问的资源的锁，当然这种实现是低效的，其中有包括2PC、S2PC等方法。但是实际上在多线程编程社区还有一种lock-free的编程模式，实际上我更倾向于叫latch-free，锁是一个较为higher level的结构，在ctitical section部分叫latch-free更加合适。本文主要是讲解如何应用latch-free技术实现基本的数据结构，近五年来（2015年至今）很多的DBMS实现技术中，大部分都开始采用latch-free的数据结构，比如andy pavlo的peleton等。在latch-free的编程世界中，你几乎不能原子的做大部分的操作，只有仅仅一小部分能够被原子的完成，这加大了latch-free编程的难度。但实际上从2004年开始世界上就陆续有很多人在接触latch-free技术。CoW、MVCC都是经典的lock-free的实现，并且由于实现这些技术的系统中都有很强的GC机制，所以使得lock-free的内存资源回收变得简单。在这篇文章中，最终实现了一种lock-free的map，但是实际上，在update操作中还是加了隐形的锁，在大量并发读操作请求下，导致update操作产生饥饿，本文没有能解决这个问题，在Lock-Free Data Structures with Hazard Pointers文章中，真正解决了lock-free结构实现下产生的update饥饿问题，并且整个实现非常优雅。本文给出了两种不是很优雅的lock-free的是方法：（1）采用DCAS（double Compare and Swap）原语，实际上在大部分的CPU指令中并没有实现，DCAS的本质是能够原子的交换两个指针的值；（2）基于两次CAS原语的map实现，该种实现方法能够解决lock-free存在的问题，但是带来了新的问题：写饥饿问题，也就是仅仅适合read not many的场景。
- Lock-Free Data Structures with Hazard Pointers</br>
hazard pointer能够优雅的实现lock-free的内存回收，hazard pointer实际上是一个single-writer multi-reader shared pointer。这个指针会被reader thread拥有（reader writer会在要读的数据上分配一个hazard pointer），一旦reader pointer拥有了这个指针，就会告知其它writer thread我正在读这个数据，你可以替换它，但是你不能改变它的内容，也不能删除它（也就是说你只能读取到这个数据，但是writer thread不能做任何的修改操作，这对于writer thread来说也是一种progress。也可以说是保证了所有线程尽量wait-free）。hazard pointer是一个复杂的结构，它会保存系统中所有线程（all threads）的读请求中访问的存储区域，当一个写线程copy了一个新的存储区域的副本，并且做了修改之后成为了“新”的副本（也就是之后的读写操作应该建立在该副本之上），然后这个写线程必须要将旧的副本删除，这显然会导致一个极其危险的操作，因此，实际上hazard pointer要求在删除时，扫描整个hazard结构，做一个集合的差运算，如果这个要淘汰的旧的副本不在这个结构中，说明该副本能够被安全的删除，这就是其核心思想。至于hazard point可以采用链表来维护其结构，也可以采用hash table来维护，不同的结构，性能不同。
- Hazard Pointers Safe Memory Reclamation for Lock-Free Objects</br>
hazard pointer(危险指针)，为什么叫做“危险指针”？本文给出了一些简单的理由：读线程将要读取的存储地址加入到所有线程的“危险指针”结构中，也就告诉其他线程，该读线程之后的所有读写内容的操作将不会对该存储地址进行任何验证。这个操作被认为是“危险”的。其他的线程在看到该存储内容是“危险”的，将不会删除或者重用该地址的内容。从代码中我们能够看出**将存储引用部分将入到hazard pointer中的动作必须要早于其他线程执行retired操作之前**。本文给出了hazard pointer如何解决ABA问题的证明，实际上在hazard pointer method中直接避免了ABA问题的发生。早期的文献已经证明，在存在GC的系统中一直是ABA-safe，本文证明在hazard pointer方法中也是ABA-safe。
- Hazard Pointers: Safe Resource Reclamation for Optimistic Concurrency</br>
- Wait-free synchronization</br>
- C++ and the Perils of Double-Checked Locking </br>
- How to Copy Files (FAST 2020)</br>
该文是如何优雅的实现lock-free的copy操作和内存区域deallocation操作当前最新的研究。采用了树形结构来维护一个hazard pointer结构，较早之前的研究都是采用了single-linked list 或者 hash table。本文第一作者非常擅长lock-free数据结构的设计与实现。
- Latch-free Synchronization in Database Systems Silver Bullet or Fool's Gold</br>
图灵奖得主stonebreker的学生Abadi的文章，文章的一作是Abadi的博士，获得了2020 jim gray优秀博士论文奖，该文是对Latch-free的批判文章。我认为本文存在的问题是：立意不正确。latch-based存在就是假设对临界资源的访问存在大量竞争，而latch-free存在本身就是假设对临界资源的访问竞争发生可能性很小。本文得出的结果是：high contention condition，latch-free不合适，这个结论显得过于苍白，甚至感觉有些滑稽。

### Query processing or query plan

- Encapsulation of Parallehsm in the Volcano Query Procesing System </br>
- LEO: DB2’s LEarning Optimizer </br>
- Neo: A Learned Query Optimizer</br>
- Review of Algorithms for the Join Ordering Problem in Database Query Optimization </br>

### Benchmarking

- OLTP-Bench: An Extensible Testbed for Benchmarking Relational Databases</br>

### Recovery

- aries: A Transaction Recovery Method Supporting Fine-Granularity Locking and Partial Rollbacks Using Write-Ahead Logging</br>
ARIES是1992年的文章，目前所有的数据库管理系统都采用ARIES算法作故障恢复，但是每个系统的实现可能略微有些差距。ARIES依赖WAL日志，并且规定数据真正写入到磁盘之前，日志必须首先写入磁盘，其引入了pageLSN，recoLSN、flushLSN、MasterRecord概念，使得log能够完整的追踪整个日志的状态，还提出了CLR等强有力的日志回滚机制，能够保证在log中如何实现回滚操作。LSN（log sequence number）是一个强大的机制，它本身是一个单调递增的counter，如何实现这个counter是一个比较重要的技术，尤其在分布式数据库中。很多当前最新的与事务相关的文章都借鉴了这个思想，比如Strong and Efficient Consistency with Consistency-Aware Durability (FAST 2020 best paper)中的durable index和persist index、update index也都是借鉴了log的LSN机制。该文较长，并且数学抽象较好，需要花费不少时间才能完全理解。
- Why Do Computers Stop and What Can Be Done About It?</br>
<https://www.hpl.hp.com/techreports/tandem/TR-85.7.pdf>
- Concurrency Control and Recovery [M. J. Franklin 1997]</br>
<https://courses.cs.washington.edu/courses/cse544/11wi/papers/franklin97.pdf> 本文对并发控制和恢复给出了一个详细的综述，并且涉及到了ACID的发展历史。对于并发控制和恢复存在很多的解决办法，
但是ACID模型将自己与其他模型分别开来，主要是由于两点：（1）在 ACID 模型中加入了隔离性和容错机制；（2）ACID模型将多个对不同对象的读写操作作为一个原子的、隔离的执行单元。ACID的这些方面都对数据
提供了强有力的保护。当然实现这些特性的代价是增加了系统实现的复杂性，并且也产生了性能代价（其实就是一定程度上降低了并发度，但是保证了系统执行的逻辑正确性）。这些特性最终给使用DBMS的用户提供
高可用和可靠性。本文也给出了“notion of correctness for concurrenct execution of transactions is serializability”，其中conflict serializability是最广泛被接受的事务正确性的概念。因为冲突可串行化
不论是检测（detect）还是实现（enforce）都很高效并且容易实现。另外一个被广泛接受是view serializability，它比conflict serializability有更少的限制，因此会得到更多合法的调度结果。但是视图可串行化需要一个
“上帝视角”，因此其只有理论价值，这主要是因为他们实现起来非常困难。前半部分都是再讲concurrency control，后半部分都是再讲解recovery，给出了ARIES的basic idea和基本的工作流程.

### Isolation

- A Critique of ANSI SQL Isolation Levels</br>
<https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf> 详细描述了基于不同concurrency control protocol下可能出现的anomoly以及对应的解决办法。我们平常所见的dirty read/unrepeatable read/phantom都是在
基于locking的并发控制方法下得到的，在乐观并发方法和基于mvcc的并发方法中存在其他的异常，为什么ANSI还要将基于locking的anomaly和isolatin写入标准是因为现代的商业化数据库管理系统几乎都采用了基于锁的并发控制方法。文章开篇首先形式化地定义了ANSI SQL委员会给出的三个anomaly（Read Uncommitted、un-repeatable read、phantom）和对应的四个
隔离级别，文中指出，这种形式化地定义比ANSI给出的英文描述更加清晰，也就是说本文的作者认为ANSI给出的Isolation level非常模糊。

### Serverless

- Catalyzer: Sub-millisecond Startup for Serverless Computing withInitialization-less Booting.(ASPLOS 2020)</br>
文章主要为了降低serverless场景下应用启动的时间，作者认为该时间应该分为三个部分：kernel启动时间；application依赖环境启动时间；application运行时间，除了app运行时间以外的两个时间都应该降下来，通过设计了合理的image机制，采用mmap将image映射到内存中，并建立合适的template，加速整个启动过程。第一篇serverless的文章，比较粗浅，希望以后多看一些这方面内容吧。</br>
- Cloud Programming Simplified: A Berkeley View on Serverless Computing </br>
该文是serverless最基础论文。
- Boki: Stateful Serverless Computing with Shared Logs </br>
Boki 独立解决了 log-based 机制中存在的三大问题: (1) totally ordering (2) consistency (3) durability。

### In-memory database

- Survey
  - Main memory database systems：an overview (H.G. Molina文章)</br>
文章发表在1992年，但是对于main-memory问题的总结在今年看来仍然很适用，对比今天的main-memory db也都基本讨论了本文提出的所有问题，非常值得精读。对in-memory中transaction、data storage、
index、cache locality、log、lock manager都有比较经典的总结和思考。
- Transactions
  - Staring into the Abyss: An Evaluation of Concurrency Control with One Thousand Cores</br>
该文发表在2014年VLDB上，文章中主要揭示in-memory database在面临hundred of cores时，什么样的并发控制协议性能最好，扩展性最强，文章的结论是：目前存在的并发控制协议，都有局限性。
因此对于当今硬件，应该from ground up进行software and hardware codesign。
- Architecture
  - NVRAM\-aware Logging in Transaction Systems</br>
  - Scalable Logging through Emerging NonVolatile Memory</br>
  - Let's Talk About Storage & Recovery Methods for Non-Volatile Memory Database Systems</br>
CMU的Andy Pavlo的文章，写的非常好，很多技术，实验内容都做了笔记。主要描述了纯NVM数据库的data storage 和 recovery 技术。
  - Better I/O Through Byte-Addressable, Persistent Memory</br>
BPFS是在PCM DIMM上的第一篇in-memory file system的文章，作者来自微软。该文针对PCM DIMM设计了新型非易失性内存文件系统BPFS，BPFS的数据结构同经典的Disk-based Block file System，采用tree structure来管理三种类型的文件，分别是inode file、directory file、data file。
首先要注意的一个问题是，在经典的文件系统设计中，每个问价都会对应一个directory file，比如/A/B/1.txt，那么对于1.txt这个文件，就对应一个directory文件，分别记录了文件的名字并且分配了一个inumber，inumber为0表示该文件对应的inode失效。并且/A/B/1.txt也对应一个data file文件
，里面存放了1.txt的用户数据，并且每一个directory file 或者data file都会对应一个inode节点，整个inode组织成tree structure。BPFS’s data structures, which are inspired by WAFL[7], consist of three kinds of files, each of which is represented by the same tree data structure. The inode file is a single file containing an array of fixed-size inodes, each uniquely representing a file or directory in the file system. The root of the inode file represents the root of the file system as a whole, and this root pointer is stored in a well-known location in persistent memory. Inodes contain file metadata including the root pointer and size of the associated file. An entry in the inode file is only considered valid if it is referred to by a valid directory entry. Directory files contain an array of directory entries that consist of an inumber (i.e., the index of an inode in the inode file) and the name of the corresponding file. Directory entries are only considered valid if they contain a non-zero inumber. Data files contain user data only.
非常重要的一段内容。该文还描述了如何实现update等操作以及如何保证atomicity write等。
  - System Software for Persistent Memory</br>
提出了能够充分利用PM设备的文件系统PMFS，并将其集成到Linux内核中。在data layout部分中，结构和传统的文件系统类似，主要包含三个文件：data file、directory file和inode file。提出了三种粒度下的consistency方案，结合了处理器特征的8byte原子写、journaling和CoW的混合一致性方案。
针对stray write提出了write protection方案，PMFS之后的PM文件系统都充分考虑了stray write问题。设计了pm_wbarrier原语，用于将数据真正刷回到PM设备，设计该原语的主要原因是在各种硬件设备中都具有write-combining buffer，这会导致乱序排序写操作，当出现crash时会造成不一致。这篇文章
作者设计很精细，是高效利用PM设备不可多得的文章。
  - NOVA: A Log-Structured File System for Hybrid Volatile/Non-Volatile Main Memories</br>
NVSL组的文章，现在NOVA正在进入Linux的主线版本中，本文分别从数据组织、一致性方法、write protection以及文件操作等各个方面进行了详细的设计，并且在在内存中做了像radix tree、red-black tree（一种平衡树）等加速PM上的操作，这显然是在混合main memory和NVMM下的最优的方式。
  - Shortcut-JFS: A Write Efficient Journaling File System for Phase Change Memory</br>
发表在MSST上的文章，很简洁，只有6页，但是清晰地传达出file system在做consistency时，结合in-place update+CoW+journaling时会得到最优的性能。当对一个block的修改大于1/2 block size时，采用CoW会得到更高的收益，避免了大量的double write，当对一个block的修改<1/2 block size时，采用journaling会得到更大的收益。
  - Managing Non-Volatile Memory in Database Systems</br>
德国慕尼黑大学数据库团队的文章，在main memory database system上一直属于领跑地位。这篇文章是他们在nvm数据库上的探索，相比于Let's Talk About Storage & Recovery Methods for Non-Volatile Memory Database Systems中提出的纯nvm数据库（在存储层次中没有DRAM层次），该数据库采用了三层（DRAM NVM SSD），并且提出
将热数据放到DRAM中（保留了main memory数据库的性能），将温数据放到nvm上，将冷数据放到SSD上，并且数据原始存放在SSD上，提出了三种策略，分别用于DRAM Eviction（采用clock algorithm）、NVM Admission（从DRAM中eviction出的数据首先进入到admission set中，当有page从DRAM中淘汰出时，首先检查是否在admission set中，如果不在，则将page放入admission set中，同时数据保留在SSD中，
如果在admission set中命中，那么将数据转移到NVM中，同时从admission set移除，这些数据被识别为温数据，该方法在2003年被提出）和NVM Eviction（采用clock algorithm），同时还采用了pointer swizzling技术和conbined page mapping table（本质上是一个hash table），将nvm和DRAM的page mapping table同时管理。该数据库比main memory能承载更大的数据量，在性能上只比main memory数据库差不多。
本文也对比了纯NVM数据库（Andy Pavlo在Let's Talk About Storage & Recovery Methods for Non-Volatile Memory Database Systems中详细描述）和DRAM+NVM数据库（FOEDUS），同时本文为了更好的利用NVM的byte addressable能力，创新性地提出cache-grained-page-size和full-page-size两种模式，能更好的利用DRAM的存储空间，同时利用了NVM的byte addressable能力减少了读放大。
  - Storage Management in the NVRAM Era </br>
- Properties of Optane DIMM
  - An empirical guide to the behavior and use of scalable persistent memory</br>
该文详细测试了Optane DIMM的延时、带宽、访问类型、访问粒度、并发度等对性能的影响，并给出了4条最佳实战策略。Optane DIMM的性能不只是单单看成是延迟较高、吞吐较小的DRAM那么简单，其很多的性质并未像DRAM
一样表现出单调性。本文同时指出，过去几十年在NVMM上的研究，应该被重新审视。
  - A Survey of Non-Volatile Main Memory Technologies: State-of-the-Arts, Practices, and Future Directions</br>
华中科技大学金海团队文章，从当前热点的nvmm研究角度入手写的，比如如何做wear leveling，如何保证consistency等。也综述了当前比较热门的混合架构。

- Multi-Version Concurrency Control of Main-Memory DBMS(Protocols)
  - T. Neumann, et al., Fast Serializable Multi-Version Concurrency Control for Main-Memory Database Systems, in SIGMOD, 2015
  - H. Lim, et al., Cicada: Dependably Fast Multi-Core In-Memory Transactions, in SIGMOD, 2017
  - P.-A. Larson, et al., High-Performance Concurrency Control Mechanisms for Main-Memory Databases, in VLDB, 2011
  - Efficient Transaction Processing in SAP HANA Database - The End of a Column Store Myth

### Awesome Distributed Systems

- [Time, Clocks, and the Ordering of Events in a Distributed System](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)
- [Consensus: Bridging Theory and Practice](https://github.com/ongardie/dissertation#readme)
- [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)
- [Paxos Made Live - An Engineering Perspective](https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf) [PODC'07](https://sci.bban.top/pdf/10.1145/1281100.1281103.pdf#view=FitH)
- [Diego Ongaro](https://ongardie.net/)
- [Leslie Lamport](http://lamport.azurewebsites.net/pubs/pubs.html)
- [Advanced Distributed Systems](https://www.cse.iitd.ac.in/~srsarangi/courses/2021/col_819_2021/index.html)
- [CMU 15-440 Distributed Systems](http://www.cs.cmu.edu/~srini/15-440/2016.Fall/syllabus.html)
- [Software Engineering for Systems Hackers](http://www.cs.cmu.edu/~dga/systems-se.pdf)
- [Distributed Transaction](https://github.com/seata/seata)
- [Database Monthly](http://mysql.taobao.org/monthly/)
- [Raft Visualization](https://thesecretlivesofdata.com/raft/)
- [Raft Go Implementation](https://eli.thegreenplace.net/2020/implementing-raft-part-0-introduction/)

### MISC

[Code As Design](https://www.developerdotstar.com/mag/articles/PDF/DevDotStar_Reeves_CodeAsDesign.pdf)
