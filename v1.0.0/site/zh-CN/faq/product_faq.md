---
id: product_faq.md
---

# 产品问题


<!-- TOC -->

- [Milvus 会收费吗？](#milvus-会收费吗)
- [Milvus 支持非 x86 平台吗？](#milvus-支持非-x86-平台吗)
- [Milvus 支持对向量的插入、删除、更改和查询操作吗？](#milvus-支持对向量的插入删除更改和查询操作吗)
- [Milvus 可以处理百亿或千亿级数据吗？](#milvus-可以处理百亿或千亿级数据吗)
- [Milvus 数据存储在哪里？](#milvus-数据存储在哪里)
- [为什么我在 SQLite / MySQL 找不到向量数据？](#为什么我在-sqlite--mysql-找不到向量数据)
- [Milvus 的元数据存储可以使用 SQL Server 或者 PostgreSQL 吗？](#milvus-的元数据存储可以使用-sql-server-或者-postgresql-吗)
- [Milvus 的 Python SDK 有连接池吗？](#milvus-的-python-sdk-有连接池吗)
- [Milvus 是否支持 “边插入边查询” ？](#milvus-是否支持-边插入边查询-)
- [Milvus 是否有可视化管理工具？](#milvus-是否有可视化管理工具)
- [Milvus 有没有数据导出的功能？](#milvus-有没有数据导出的功能)
- [为什么我通过 `get_entity_by_id` 获取的向量精度损失了？](#为什么我通过-get_entity_by_id-获取的向量精度损失了)
- [向 Milvus 中导入数据时，应该自己指定 entity ID 还是由 Milvus 自动生成 entity ID？](#向-milvus-中导入数据时应该自己指定-entity-id-还是由-milvus-自动生成-entity-id)
- [Milvus 可以插入重复 ID 的向量吗？](#milvus-可以插入重复-id-的向量吗)
- [Milvus 中自定义 ID 有没有长度限制？](#milvus-中自定义-id-有没有长度限制)
- [Milvus 中单次插入数据有上限吗？](#milvus-中单次插入数据有上限吗)
- [为什么向量距离计算方式是内积时，搜索出来的 `top1` 不是目标向量本身？](#为什么向量距离计算方式是内积时搜索出来的-top1-不是目标向量本身)
- [对集合分区的查询是否会受到集合大小的影响，尤其在集合数据量高达一亿数据量时？](#对集合分区的查询是否会受到集合大小的影响尤其在集合数据量高达一亿数据量时)
- [如果只是搜索集合中的部分分区，整个集合的数据会全部加载到内存吗？](#如果只是搜索集合中的部分分区整个集合的数据会全部加载到内存吗)
- [对各个数据段的检索是并行处理的吗？](#对各个数据段的检索是并行处理的吗)
- [Milvus 中如何选择向量索引的类型？](#milvus-中如何选择向量索引的类型)
- [Milvus 可以在同一个集合中的不同分区上建立不同索引吗？](#milvus-可以在同一个集合中的不同分区上建立不同索引吗)
- [Milvus 中支持新增向量后再建索引吗？](#milvus-中支持新增向量后再建索引吗)
- [索引 IVF\_SQ8 和 IVF\_SQ8H 在召回率上有区别吗?](#索引-ivf_sq8-和-ivf_sq8h-在召回率上有区别吗)
- [Milvus 中 FLAT 索引和 IVF_FLAT 索引的原理比较？](#milvus-中-flat-索引和-ivf_flat-索引的原理比较)
- [创建索引立即查询，为什么内存会突然增长？](#创建索引立即查询为什么内存会突然增长)
- [建立集合后，`index_file_size` 和 `metric_type` 还支持修改吗？](#建立集合后index_file_size-和-metric_type-还支持修改吗)
- [向量插入后自动落盘间隔时间是多少？](#向量插入后自动落盘间隔时间是多少)
- [如果设置了 `preload_collection`，必须是等集合全部加载到内存，服务才能访问吗？](#如果设置了-preload_collection必须是等集合全部加载到内存服务才能访问吗)
- [Milvus 的数据落盘逻辑是怎样的？](#milvus-的数据落盘逻辑是怎样的)
- [Mishards 推荐的配置是什么？](#mishards-推荐的配置是什么)
- [Mishards 支持 RESTful API 吗？](#mishards-支持-restful-api-吗)
- [什么是归一化？Milvus 中为什么有时候需要归一化？](#什么是归一化milvus-中为什么有时候需要归一化)
- [为什么欧氏距离和内积在计算向量相似度时的结果不一致？](#为什么欧氏距离和内积在计算向量相似度时的结果不一致)
- [Milvus 对集合和分区的总数有限制吗？](#milvus-对集合和分区的总数有限制吗)
- [为什么搜索 `topk` 向量，结果不到 k 条向量？](#为什么搜索-topk-向量结果不到-k-条向量)
- [Milvus 支持的向量维度的最大值是多少？](#milvus-支持的向量维度的最大值是多少)
- [仍有问题没有得到解答？](#仍有问题没有得到解答)

<!-- /TOC -->

#### Milvus 会收费吗？

Milvus 会坚持开源路线，现有的版本都不会收费。

项目开源，请遵循 [Apache 2.0 协议](http://www.apache.org/licenses/LICENSE-2.0) 使用。

#### Milvus 支持非 x86 平台吗？

目前不支持。

#### Milvus 支持对向量的插入、删除、更改和查询操作吗？

支持。其中，对向量的修改可以通过先删除再插入来实现。

#### Milvus 可以处理百亿或千亿级数据吗？

Milvus 提供了集群分片中间件 Mishards，可以实现集群分片部署，满足百亿或者千亿级数据的处理需求。


#### Milvus 数据存储在哪里？

向量数据导入 Milvus 后，将自动存储在本地磁盘的 **milvus/db/tables/** 这个路径下。

元数据可以存储在 MySQL 或 SQLite 上。详见 [使用 MySQL 管理元数据](data_manage.md)。


#### 为什么我在 SQLite / MySQL 找不到向量数据？

SQLite / MySQL 只是存放原始向量数据的元数据。向量和索引直接以文件的形式存在磁盘上，不存放在 SQLite 或 MySQL里。详见 [存储相关概念](storage_concept.md)。

#### Milvus 的元数据存储可以使用 SQL Server 或者 PostgreSQL 吗？

不可以，目前仅支持 SQLite 和 MySQL。

#### Milvus 的 Python SDK 有连接池吗？

Milvus v0.9.0 及更高版本对应的 Python SDK 有连接池。连接池的默认连接数量没有上限。

#### Milvus 是否支持 “边插入边查询” ？

支持。

#### Milvus 是否有可视化管理工具？

从 Milvus v0.7.0 开始有 [Milvus Enterprise Manager](https://zilliz.com/products/em) 提供图形管理功能。

#### Milvus 有没有数据导出的功能？

目前没有专门的工具实现该功能。你可以通过 `get_entity_by_id` 得到指定 ID 对应的向量。


#### 为什么我通过 `get_entity_by_id` 获取的向量精度损失了？

Milvus 将向量的每个维度以单精度（精确到小数点后 7 位）存储和计算。所以如果原始数据为双精度（精确到小数点后 16 位），经过 Milvus 的处理后就会出现精度损失。

#### 向 Milvus 中导入数据时，应该自己指定 entity ID 还是由 Milvus 自动生成 entity ID？

两种方法均可。但是，在一个集合内的向量必须全部使用用户指定的 entity ID 或者全部使用自动生成的 entity ID。


#### Milvus 可以插入重复 ID 的向量吗？

可以，这样在 Milvus 中会存在相同 ID 的多条向量。

#### Milvus 中自定义 ID 有没有长度限制？

ID 类型是非负的 64 位整型。

#### Milvus 中单次插入数据有上限吗？

单次插入数据不能超过 256 MB。

#### 为什么向量距离计算方式是内积时，搜索出来的 `top1` 不是目标向量本身？

向量距离计算方式用内积时，如果向量未归一化，会出现这样的情况。

#### 对集合分区的查询是否会受到集合大小的影响，尤其在集合数据量高达一亿数据量时？

不会。如果你在搜索时指定了分区，Milvus 只会在相应分区进行搜索。

#### 如果只是搜索集合中的部分分区，整个集合的数据会全部加载到内存吗？

不会，只加载指定的分区里的数据。


#### 对各个数据段的检索是并行处理的吗？

一般而言，Milvus 对单个数据段内的查询是并行的，多个数据段的处理根据发行版本略有不同。

假设一个集合存在多个数据段，当查询请求到达时：

- CPU 版 Milvus 会对数据段读取任务和段内查询任务进行流水线处理。

- GPU 版 Milvus 会在 CPU 版的基础上，将多个数据段分配给各个 GPU 处理。

可参阅文章：[Milvus 开源向量搜索引擎 ANNS](https://zhuanlan.zhihu.com/p/110332250)。

#### Milvus 中如何选择向量索引的类型？

索引需要根据具体场景和需求去选择。详见 [如何选择索引类型](https://milvus.io/cn/blogs/2019-12-03-select-index.md)。

#### Milvus 可以在同一个集合中的不同分区上建立不同索引吗？

不可以。同一个集合在某一刻只能有一种索引。


#### Milvus 中支持新增向量后再建索引吗？

支持。Milvus 中数据是分文件存储的，后续新增向量会存在新的数据文件中。该文件达到一定量后会自动触发建立索引，生成一个新的索引文件，不会影响之前已经建立过的索引。


#### 索引 IVF\_SQ8 和 IVF\_SQ8H 在召回率上有区别吗?

对于相同的数据集，IVF\_SQ8 和 IVF\_SQ8H 的召回率一致。

#### Milvus 中 FLAT 索引和 IVF_FLAT 索引的原理比较？

把 FLAT 和 IVF_FLAT 做比较，可以这么估算：

已知 IVF_FLAT 索引是把向量分成 `nlist` 个单元。假设用默认的 `nlist` = 16384，搜索的时候是先用目标向量和这 16384 个中心点计算距离，得到最近的 `nprobe` 个单元，再在单元里计算最近向量。而 FLAT 是每条向量和目标向量计算距离。

所以当总的向量条数约等于 `nlist` 时，两者的计算量相当，性能也差不多。而随着向量条数达到 `nlist` 的 2 倍、3 倍、n 倍之后，IVF_FLAT 的优势就越来越大。

可参阅 [如何选择索引类型](https://milvus.io/cn/blogs/2019-12-03-select-index.md)。

#### 创建索引立即查询，为什么内存会突然增长？

这是因为 Milvus 在进行搜索时会将新生成的索引文件加载到内存，由于加载的索引文件和用于生成索引文件的原始向量文件总和小于 `cache.cache_size` 的上限，原始向量数据暂未被系统从内存释放。


#### 建立集合后，`index_file_size` 和 `metric_type` 还支持修改吗？

不支持。

#### 向量插入后自动落盘间隔时间是多少？

1 秒。

#### 如果设置了 `preload_collection`，必须是等集合全部加载到内存，服务才能访问吗？

是的。如果是在 **server_config.yaml** 里设置的，那在启动 Milvus 时就会加载好数据后才开始提供服务。


#### Milvus 的数据落盘逻辑是怎样的？

插入时把数据写到内存，定时地把缓存里的数据落盘。如果调用 `flush` 方法，也会触发落盘的动作。

详见 [存储操作 > 数据落盘](storage_operation.md#数据落盘)。

#### Mishards 推荐的配置是什么？

推荐写节点用 GPU 版 Milvus，读节点用 CPU 版 Milvus。比如现在只能用单个写节点，这个写节点可以配置 GPU 资源用来建索引，读节点都配置成 CPU 节点。

#### Mishards 支持 RESTful API 吗？

目前不支持。

#### 什么是归一化？Milvus 中为什么有时候需要归一化？

归一化指的是通过数学变换将向量的模长变为 1 的过程。如需使用点积计算向量相似度，则必须对向量作归一化处理。处理后点积与余弦相似度等价。

可参阅文章 [向量搜索的简明数学基础](https://zhuanlan.zhihu.com/p/88117781)。

#### 为什么欧氏距离和内积在计算向量相似度时的结果不一致？

如果欧氏距离和内积返回不一致的结果，需要检查数据是否已经归一化。如果没有，请先对数据进行归一化。理论上可以证明，对于未归一化的数据，欧氏距离和内积的结果是不一致的。


#### Milvus 对集合和分区的总数有限制吗？

collection 数量没有限制。每个 collection 内的 partition 总数不能超过 4096 个。


#### 为什么搜索 `topk` 向量，结果不到 k 条向量？

在 Milvus 支持的索引类型中，IVF_FLAT 和 IVF_SQ8 是基于 k-means 空间划分的分单元搜索算法。空间被分为 `nlist` 个单元，导入的向量被分配存储在基于 `nlist` 划分的文件结构中。搜索发生时，只搜索最近似的 `nprobe` 个单元。

如果 `nlist` 和 k 比较大，而 `nprobe` 又足够小，有可能出现 `nprobe` 文件中的所有向量总数小于 k。当搜索 `topk` 向量时，就会出现搜索结果小于 k 条向量的情况。

想要避免这种情况，可以尝试将 `nprobe` 设置为更大值，或者把 `nlist` 和 `k` 设置为更小值。

详见 [索引类型](index.md)。


#### Milvus 支持的向量维度的最大值是多少？
Milvus 最多能够支持 32,768 向量维度。


#### 仍有问题没有得到解答？

如果仍有其他问题，你可以：

- 在 GitHub 上访问 [Milvus](https://github.com/milvus-io/milvus/issues)，提问、分享、交流，帮助其他用户。
- 加入我们的 [Slack 社区](https://join.slack.com/t/milvusio/shared_invite/enQtNzY1OTQ0NDI3NjMzLWNmYmM1NmNjOTQ5MGI5NDhhYmRhMGU5M2NhNzhhMDMzY2MzNDdlYjM5ODQ5MmE3ODFlYzU3YjJkNmVlNDQ2ZTk)，与其他用户讨论交流。

