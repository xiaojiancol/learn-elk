

### 01

### 02

### 03

### 04

### 05

### 06

### 07

### 08

### 09 索引/文档/mapping/setting

### 10 可用性 / 扩展性

集群/ 节点即实例(uid) master eligible / 

data 节点，负责保存分片数据 / coordinating 节点，默认都是 coordinating  

分片（扩展性？） 主分片 副本分片（高可用）  

- TODO
 - 副本故障是 yellow ，master故障是不是会自动切换？ 中间会有数据丢失吗？
 - 副本同步会有延迟吗？
 - 故障节点恢复之后会自动追回丢失的数据吗？

### 11 CURD

### 12 倒排索引

Term Dictionary B+ 或者 hash 拉链

倒排索引列表:{id,tf,postion(以 word 为单位),offset(以字符为单位)}

### 13 analysis

tocken / character filter / tokenizer / tocken filter
analyzer

### 14 search api

