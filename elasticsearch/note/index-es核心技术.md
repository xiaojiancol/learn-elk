
## 第一章 概述

### 01 介绍  

### 02 内容综述  

### 03 ES发展历史  

### 04 ES stack 及其 应用场景  

## 第二章 安装上手

### 05 安装配置  

- 最好不要在机器上设置 JDK
- 启动之前打开配置文件  
- 启动多个节点

### 06 kibana 安装和界面浏览

- dashboard
- 插件安装

### 07 docker 运行 elk
### 08 logstash 导入测试数据集

## 第三章 ES 入门

### 09 索引/文档/mapping/setting

CVS 在导入的时候，被自动的做了序列化，格式是 JSON，类型采用了推断方式，Mapping也是 Dynamic Mapping  
setting 定义分片  
Mapping 定义索引结构  
索引相当于表，节点相当于库，分片相当于分库分表，  


### 10 可用性 / 扩展性

集群/ 节点即实例(uid) master eligible / 

- master节点管理状态 ，每个节点可以保存状态 
- 副本分片数量是可以调整的，那么不一致的话会怎样？  
- data 节点，负责保存分片数据 / coordinating 节点，默认都是 coordinating  

分片（扩展性？） 主分片 副本分片（高可用）  
默认一个节点一个分片，那么增加节点是不能提高可用性的，一个节点多个分片，
因为不同同学的情况不一样，比如有人 996 有人 995 有人 885 ，那么学习速度是不一致的

### 11 CURD



#### 简单操作

- index  
  put my_index/_doc/1  
  {body}  
  这个操作是先删除再新建，具有幂等性,但是版本会增加  
- create  
  自己指定ID
  PUT my_index/_create/1  
  PUT my_index/_doc/1?op_type=create
  {body}
  或者自动生成ID
  POST my_index/_doc
  {body}
- read  
  GET my_index/_doc/id
- update
  POST my_index/_update/id  
  {body}  
  这个操作是直接更新  
- delete
  DELETE my_index/_doc/id

#### 批量操作

- Bulk API  
- mget
- msearch ？
- mmatch

### 12 倒排索引

Term Dictionary B+ 或者 hash 拉链

倒排索引列表:{id,tf,postion(以 word 为单位),offset(以字符为单位)}

### 13 analysis

tocken / character filter / tokenizer / tocken filter
analyzer

### 14 search api

### 15 URL search

### 16 DSL

### 17 Query String & Simple Query String

### 18 Dynamic mapping

### 19 显示设置Mapping

PUT index_name
{ mappings:{properties:{fileName:{type:"",index:false}}} }
- null 处理？
- copyto
- 数组

### 20 多字段特性 ，使用自定义 Analyzer



### 21 index Template 和 Dynamic Template

- index Template 是用在索引上的，对某类索引做设定
- Dynamic Template 用在具体某个索引上，对某类属性做设定

### 22 Elasticsearch 聚合简析

### 23 第一部分总结

## 第四章 深入搜索

### 24 基于词项和基于全文的搜索

- term 查询 不会做分词处理
  Term Query  
  Range Query  
  Exists Query  
  Prefix Query  
  Wildcard query  
  可以转为 Filter 查询
- 文本查询
  Match Query  
  Match Phrase Query  
  Query String Query  

### 25 格式化数据搜索

### 26 相关性算分

Relevance  
算法： TF-IDF BM25  
Term Frequency 频率 = 次数 / 总字数  
Stop word
IDF Inverser Document Frequency =  log( 全部文档数 / 出现的文档数)  
`TF-IDF = TF*IDF + TF*IDF + TF*IDF`  

### 27 Query 和 Filtering 与多字段查询

多字段查询: boolean 查询  
运算符: must / must not / should (可以出现) / avaliable (可以出现)  
更改查询算分  

### 28 单字段串多字段查询



### 29 单字符串多字段查询

TODO  

### 30 多语言及中文分词与检索  

### 31 Space Jam, 一次全文搜索实例  

### 32 Search Template 和 index alias

### 33 综合排序： Function Score Query 优化算分

### 34 Term & Phrase Suggester

### 35 自动补全与基于上下文的提示

### 配置跨集群搜索

## 第五章 分布式特性及分布式搜索机制

### 37 集群分布式模型及选主与脑裂问题

- 集群，可以有多个  
- 节点，一个集群下面可以挂多个节点，建议节点和主机是 1:1 对应关系，name,id  
- Coordinating 节点，负责处理请求，具有路由功能  
- master 节点， DDL 和 DML，以及维护集群状态  
  - 集群状态信息  
    所有节点信息，所有的索引，以及相关 Mapping 与 Setting 信息，分片路由信息  
  - 每个节点都保存状态信息，但是只有 Master 可以修改状态信息，并同步给其他节点  
- Eligible 节点。  
  - 通过 ID 比较来选取 master 节点。  当然对于有统一分配 ID 的集群来讲这个事情这是合理的且不错的方法，但是对于没有统一分配 ID 的集群，或者不相干的集群合并的时候，这个算法就不适用了，当然这种场景在我看来也是比较罕见的情况。  
  
- 脑裂处理  
  - 高版本是如何处理的？  


### 38 分片与集群的故障转移  

节点 分片 主分片 副本分片  
通常是一个节点，只有一个主分片，可以有多个副分片（以便于故障转移）。  
每个节点都可以存放主分片和副本分片，

### 39 文档分布式存储  

- 确保均匀分布  
- 潜在算法  
  - Round Robbin  
  - 维护文档与分片的关系
  - 通过 ID 计算出所在 sharding  
    shard = hash(_routing) % number_of_primary_shards  
    这也是 number_of_primary_shards 不能随意修改的原因  
    routing 默认是 id ，也可以自定义，以便于“分类”  

### 40 分片及其生命周期  

- 分片 对应 Lucene 的 index
- ES 的一些特性
  -  数据不丢失  
  -  实时查询  
  -  异步删除  
- 倒排索引的不可变性  
  - 无需考虑并发写的安全性问题，避免锁带来的性能问题
  - 索引全在内存中  
  - 缓存容易生成/压缩  
  - 挑战： 一个新文档需要被搜索，需要重建整个索引？  
- 倒排索引的文件 segment  
  - Lucene 的 index 1:n segment，对应 ES 的 Shared
  - commit point 记录了所有 segment
  - 在搜索结果中，用 .del 过滤
- 查询和 refresh  
  write --> index buffer，同时写入 Transaction log -- 每 1s 做一次 refresh --> segement，只有数据进入了 segment 才可以被查询到  
  index buffer 默认是 JVM 的 10%， 数据被沾满时也会 refresh  
  refresh 时会清空 index buffer，但是不会清空 Transaction log  
- flush  
  先调用 refresh (会清空 index buffer)  
  fsync，将缓存中的 Segment 写入磁盘，清空 Transaction log  
  默认 30 分钟执行一次 flush，或者 Transaction log 写满时 （默认512M）  
- Merge  
  定期合并 segment ，物理删除 .del 中的记录的文件  
  Lucene ES 会自动执行 Merge  
  人为执行 Merge POS index_name/forcemerge 


- FAQ
  - segment 是文档吗？  
  - index 和 commit point 是啥关系  
  - 查询的执行过程是啥样的？  

### 41 分布式查询及相关性算分  

- 执行流程
  - query  
  - fetch
    
- 问题
  - 性能问题
    数据数量 = number_of_shard * (from + size)   
  - 相关性的算分是基于分片本身的  
   search_type = dfs_query_then_fetch

### 42 排序及 Doc Values & Fielddata  

- doc values 列式存储，文本类型字段无效  
  发生在磁盘，且设定需要 reindex  
- fielddata
  发生在内存，且可动态设置  
  

### 43 分页和遍历: From,size,Search After & Scroll API  

- from，size  
  - search_after 不支持翻到指定页码  
- Scroll API
  - 查询快照

### 44 处理并发读写  

通过乐观锁，控制并发写，而我根本就不想用 ES 做写入操作，除非是文本内容  

## 第六章 深入聚合分析

### 45 Bucket & Metric 聚合分析以及嵌套聚合  
### 46 Pipeline 聚合分析  
### 47 作用范围与排序  
### 48 聚合分析的原理和精准度  

## 第七章 数据建模

### 49 对象 nested 对象  
### 50 文档父子关系  
### 51 Update By Query & Reindex  
### 52 Ingest Pipeline  
### 53 数据建模最佳实践  
### 54 总结  

## 第八章 保护你的数据

### 55 集群身份认证  
### 56 群内安全通信  
### 57 与外部安全通信  

## 第九章 水平扩展集群

### 58 常见集群部署方式  
### 59 Hot & Warm 与 Shard Filtering  
### 60 如何对集群进行容量管理  
### 61 分片设计及管理  
### 62 公有云上管理与部署集群  
### 63 私有云上管理与部署集群  

## 第十章 生成环境中的集群

### 64 集群监控与排查
### 65 生产环境常用配置和线上清单
### 66 监控 ES 集群
### 67 诊断集群潜在问题
### 68 解决集群 yellow 和 red 问题
### 69 集群压力测试
### 70 段合并优化和注意事项
### 71 缓存以及 Breaker 限制内存使用
### 72 一些运维建议

## 第十一章 索引生命周期管理
### 73 shrink 与 Rollover  API
### 74 索引生命周期管理

## 第十二章 用 Logstash 和 Beats 构建数据管道
### 75 logstash 介绍
### 76 beats 介绍

## 第十三章 Kibana
### 77 使用 Index Pattern 配置数据
### 78 使用 Kibana Discover 探索数据
### 79 基本可视化组件介绍
### 80 Visual Builder 介绍
### 81 构建 Dashboard

## 第十四章 X-Pack
### 使用 Monitoring 和 Alerting 监控 Elasticsearch 集群
### 使用 APM 进行程序性能监控
### 用机器学习实现时序数据的异常检测
### 85 用 ELK 进行日志管理
### 86 用 Canvas 做数据演示
### 87 用 Graph 进行数据分析
### 88 用 Timelion 分析时序型数据

## 实战1 电影搜索服务
### 89
### 90
### 91

## 实战2 stockflow 调查问卷分析
### 92
### 93
### 94

## 备注 ES 认证
### 95
### 96

## TODO

- 没有搞明白 filter query 差异是啥
- text 字段，EL 会自动增加 keyword 字段？
- 创建索引时，可以指定创建的分片数，以及副本数量？  
- 自动生成的ID，有助于做范围查询吗？  
  主要是考虑到是否采用 B 树策略  
- 副本故障是 yellow ，master故障是不是会自动切换？ 中间会有数据丢失吗？
- 副本同步会有延迟吗？
- 故障节点恢复之后会自动恢复故障期间丢失的数据吗？如果会，那么这个恢复过程会是不可用的状态吧。  
- 7.0 是如何避免脑裂的呢？  
- ingest 节点是个什么节点  https://www.elastic.co/guide/en/elasticsearch/reference/current/ingest.html
- doc values 和 fielddata 
- match_all vs ？
- 默认多字段，会增加一个 keyword?

https://blog.csdn.net/qq_20499001/article/details/89261583  ElasticSearch在数十亿级别数据下，如何提高查询效率？
https://www.cnblogs.com/0xcafedaddy/p/6522984.html  ElasticSearch搜索term和terms的区别