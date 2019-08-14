https://www.elastic.co/guide/en/elasticsearch/reference/current/joining-queries.html

在像 Elasticsearch 这样的分布式系统中执行一个 join 代价通常是昂贵的。 Elasticsearch 提供了两种形式的 join 旨在水平扩展？ 

- nested 查询  
  文档可能包含类型的字段nested。这些字段用于索引对象数组，其中每个对象都可以nested作为独立文档查询（带有查询）  

- has_child和has_parent查询  
  一个 join 字段关系可以在单个索引中的文档之间存在。该has_child查询返回其子文档与指定查询匹配的父文档，而 has_parent查询返回其父文档与指定查询匹配的子文档。

https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-nested-query.html

