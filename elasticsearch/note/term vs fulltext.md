
## term 查询

term 不会做分词，查询会做评分
1. 转小写
2. 对 key word 做查询
  多字段，会增加一个 key word

查询取消评分过程

## 全文查询

match xxx / Query String Query

match 查询，可以做逻辑运算，
查询过程  分词 --> 倒排索引打分 --> 返回