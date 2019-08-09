

### 01

### 02

### 03

### 04

### 05

### 06

### 07

### 08

## 第三章 ES 入门

### 09 索引/文档/mapping/setting

### 10 可用性 / 扩展性

集群/ 节点即实例(uid) master eligible / 

data 节点，负责保存分片数据 / coordinating 节点，默认都是 coordinating  

分片（扩展性？） 主分片 副本分片（高可用）  



### 11 CURD

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

### 19 Mapping

### 20 多字段特性 使用自定义 Analyzer

### 21 index Template 和 Dynamic Template

### 22 Elasticsearch 聚合简析

### 23 第一部分总结

## 第四章 深入搜索

### 24 基于词项和基于全文的搜索

### 25 格式化数据搜索

### 26 相关性算分

### 27 Query 和 Filtering 与多字段查询

多字段查询: boolean 查询  
运算符: must / must not / should (可以出现) / avaliable (可以出现)  


### 28 单字段串多字段查询

### 29 单字符串多字段查询

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
  - 集群状态信息 所有节点信息，所有的索引，以及相关 Mapping 与 Setting 信息，分片路由信息
  - 每个节点都保存状态信息，但是只有 Master 可以修改状态信息 
- Eligible 节点。  
  - 通过 ID 比较来选取 master 节点。  当然对于有统一分配 ID 的集群来讲这个事情这是合理的且不错的方法，但是对于没有统一分配 ID 的集群，或者不相干的集群合并的时候，这个算法就不适用了，当然这种场景在我看来也是比较罕见的情况。  
  
### 38 分片与集群的故障转移  

节点 分片 主分片 副本分片  
通常是一个节点，只有一个主分片，可以有多个副分片（以便于故障转移）。  

### 39 文档分布式存储  

### 40 分片及其生命周期  

### 41 分布式查询及相关性算分  

### 42 排序及 Doc Values & Fielddata  

### 43 分页和遍历: From,size,Search After & Scroll API  

### 44 处理并发读写  

## 第六章 深入聚合分析

### Bucket & Metric 聚合分析以及嵌套聚合
### Pipeline 聚合分析
### 作用范围与排序
### 聚合分析的原理和精准度

## 第七章 数据建模

### 对象 nested 对象  
### 文档父子关系  
### Update By Query & Reindex  
### Ingest Pipeline  
### 数据建模最佳实践  
### 总结  

## 第八章 保护你的数据

### 集群身份认证  
### 群内安全通信  
### 与外部安全通信  

## 第九章 水平扩展集群

### 常见集群部署方式  
### Hot & Warm 与 Shard Filtering  
### 如何对集群进行容量管理  
### 分片设计及管理  
### 公有云上管理与部署集群  
### 私有云上管理与部署集群  

## 第十章 生成环境中的集群

### 集群监控与排查
### 生产环境常用配置和线上清单
### 监控 ES 集群
### 诊断集群潜在问题
### 解决集群 yellow 和 red 问题
### 集群压力测试
### 段合并优化和注意事项
### 缓存以及 Breaker 限制内存使用
### 一些运维建议

## 第十一章 索引生命周期管理
### shrink 与 Rollover  API
### 索引生命周期管理

## 第十二章 用 Logstash 和 Beats 构建数据管道
### logstash 介绍
### beats 介绍

## 第十三章 Kibana

## 第十四章 X-Pack

## 实战1 电影搜索服务

## 实战2 stockflow 调查问卷分析

## 备注 ES 认证

## TODO

- 副本故障是 yellow ，master故障是不是会自动切换？ 中间会有数据丢失吗？
- 副本同步会有延迟吗？
- 故障节点恢复之后会自动追回丢失的数据吗？
- 7.0 是如何避免脑裂的呢？