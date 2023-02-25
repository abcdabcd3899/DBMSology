# Introduction

该部分包括 2001 年作者发表在 VLDB Conference 上的 《weaving relations for cache performance》和 2002 年发表在 VLDBJ 上的 《Data Page Layouts for Relational Databaseson Deep Memory Hierarchies》。2001 年 VLDB 论文提出的 PAX (partition attribute across **属性间交叉划分或属性间交叉分组**) 是出于高效利用缓存的目的，PAX 通过将每一页内部的数据重新按照每个属性聚集到一起。

* 传统的 NSM (N-ary Storage Model) 按照 tuple 来组织 page 内部的数据，当某个查询只需要每个 tuple 内的部分属性时，NSM 存储模型不能更好地利用缓存。
* DSM 模型在单个属性的查询中表现出比 NSM 更好的性能，**但是 DSM 模型在涉及到多个属性的查询中性能存在显著下降，因为多属性查询时必须要 join 不同的属性。**

PAX 是 Partition Attributes Across，它实际上包含：

* Partition Attrbutes 在一个 page 内部将 Attributes 分区，这实际上是一个字 “分”
* Attributes Across 将一个 page 内部不同 tuple 的相同 Attributes 合并到一起，这实际上一是一个字 “合”
所以 PAX 就是在一个 page 内将每一个 tuple 的属性 “分”开，然后将一个 tuple 内相同属性 ”合“ 到一起。

这样（1）最小化了一个 page 内部每一列内部的空间利用率；（2）tuple 重构的代价也达到最小。

**本文没有使用压缩技术，在 future work 中提到了可能压缩会使 PAX 性能更好。**

## Q&A

1/. 在当前的 NSM 存储模型中，如何减少 NSM stall 时间？
当前的 NSM 模型中已经很好地优化了 IO 性能，但是由于 NSM page 中的 tuple 组织方式导致在 AP 场景下较差的 cache 性能，该论文提出 PAX 存储模型，经过实验对比， （1）PAX 比 NSM 减少了 75% 的 stall 时间；（2）如果关系全部能够加载到内存中， 使用 PAX 数据组织模型的range selection 、range update 比 NSM 有 17% ～25% 的性能提升；（3）在涉及到 IO 的 TPC-H 查询有 11% ～ 48% 的性能提升。 **从这些数据中，我感受到对于数据量很大的查询，PAX 数据组织模型性能提升范围更大。**

2/. 出于何种需求或者何种观察提出 PAX 数据组织模型？
要回答这个问题，应该从两个方面入手：

* 传统数据组织方式
  * NSM
NSM 数据将全部数据组织成 page，使用 page table 在内外存之间完成映射，在 page 内部，分为 header、slot number、  entries 区域，在entries 区域按照每个 record 的方式叠放，并将每条 record 的地址记录在 slot number 中，因此，在查询过程中根据 page ID 和 slot number 便能精确定位到 record。常见的数据库有：PostgreSQL
* 查询特征
  * 当查询只需要每个 record 中的少量字段时，NSM 的组织方式会造成一定程度的读写放大。
  * 为了能够适应上述查询特征，提出了 DSM 数据组织模型。
DSM 数据组织模型也就是我们通常所说的纯列式模型，这种模型会将每一个relation 拆分成为 sub-relation，sub-reation再通过 page 的方式组织数据，对于只有单列的查询时，显然该模型能更加高效。但是当查询中存在多个属性（字段）时，DSM 需要 join 不同的 sub-relation。为了更够将拆分后的关系还原成原来的 NSM 模型，实际上会有一些额外的存储代价，比如每个列在拆分后需要记录它属于那个记录等信息，在 sub-relation join 时需要使用这些额外的“键“。常见的数据库有：SybaseIQ

出于 NSM 和 DSM 模型各自的缺点，因此提出 PAX 模型。

3/. Wokload 存在哪些特征？
已经有文献证明，对于决策支持 （AP）或者空间数据访问类型，这些 wordload 的性能经常受限于处理器和内存子系统 （memory + cache），而不是IO，如何更高效地利用 cache 存储层次，成为解决 AP 型存储系统性能的关键。

4/. 可以一句话总结 PAX 的优势在哪里吗？
可以。一句话总结 PAX 就是 PAX 保留了 NSM 优于 DSM 的部分，同时比 NSM 模型更加的缓存友好。 **或者说 PAX 是一种结合了 NSM 和 DSM 优点的新的 data record 布局方式**。

* PAX 按照 NSM 的方式将数据以 page 形式存储
* 在每个 page 内部，PAX 将每个属性的值组织成为一个 minipage
当一个查询涉及到多个属性时，在每个 page 内部将不同属性组织成为 minipage 的方式会设计在**这个 page**上的 **mini-join**操作，但是这远比 DSM 模型代价小得多。

5/. PAX 还有其它附加的优点吗？

* PAX 由于只是改变了 page 内部的数据组织方式，因此在代码修改中，只需要修改 page level 即可
* 可以根据查询属性的数目将 PAX 作为一种可选的 page 内部组织方式
* 相同属性上可以压缩

6/. 能否简洁地总结常见的数据组织方式
![data layout](https://user-images.githubusercontent.com/13810907/138561816-a3c7e15d-3f08-429d-b79a-8598202c73e3.png)

7/. PAX 和 NSM 占用空间相同吗？
因为 PAX 在 page 之间是按照 NSM 的方式组织的，因此总的 page 数目几乎是相等的，只是在 page 内部的结构不同，整体上可能会由于实现不同有微小的差异。
![PAX](https://user-images.githubusercontent.com/13810907/138561825-9186e878-e2ca-4b14-b915-31959d757436.png)

8/. PAX、NSM、DSM 对比？

* PAX 与 NSM：当 查询的 selectivity 大于等于 50% 时，PAX 的性能完全不输 NSM，因为 PAX 本身数据局部性比 NSM 好，而且NSM 总计会有 50% 的时间污染 cache buffer，这样子算下来 PAX 优于 NSM；
* PAX 与 DSM：当查询只涉及到 1 到 2 个属性时，二者的查询性能几乎没有太大的差距，但是当查询涉及到较多的属性时，DSM 性能存在明显抖动，因为 DSM 需要执行大量的 join 操作组重构 tuple。

给出了 page 如何从 row 过渡到 pax：

* 如果 tuple 数据都是定长，在不考虑压缩的情况下，从 row 到 pax 变化非常小；
* 如果tuple 数据是变长，实际上能够通过下述方式变长定长，只是需要牺牲一些空间；

![two-pointer](https://user-images.githubusercontent.com/13810907/138561843-a57d8cec-18c6-4d80-b95c-50a0b7bba341.png)

对于变长数据 page 内部还能像下图这样组织：

![vpax](https://user-images.githubusercontent.com/13810907/138589114-77c69e74-e5cb-4b12-a171-b6e3b075d30a.png)

这部分内容是我自己设想出来从 row 到 pax 的合理性，该故事纯属虚构 😅，如有雷同，纯属巧合 😅
