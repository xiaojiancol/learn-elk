
## TODO

- 为什么 GET 也可以发送 body ？

```
GET from index
select feild
match { feild1:value1,feild2:value2}
```

GET /bank/_search?q=*&sort=account_number:asc&pretty

GET _cat/indices

// 搜索某个 index
POST kibana_sample_data_ecommerce/_search?
{
  "size": 1
}

GET /kibana_sample_data_ecommerce/_search?pretty
{
  "query": { "match_all": {} },
  "from": 10,
  "size": 10
}

// 新建索引 mapping
PUT _index/my_index/mapping
{
  
}

// 查看索引的mapping
GET .kibana_1/_mapping

GET _search
{
  "query": {
    "match_all": {}
  }
}

### term 查询

- 跳过算分
- 数值范围搜索
- 日期计算搜索

{
  "profile":"true",
  "explain":"true",
  query:{
    "term":{
      "avaliable":true
    }
  }
}

- 多字段 是包含不是精确？

买视频，赠小册。  

### fulltext 查询

## 结果解释

```
{
  "took" : 63,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
        "value": 1000,
        "relation": "eq"
    },
    "max_score" : null,
    "hits" : [ {
      "_index" : "bank",
      "_type" : "_doc",
      "_id" : "0",
      "sort": [0],
      "_score" : null,
      "_source" : {"account_number":0,"balance":16623,"firstname":"Bradshaw","lastname":"Mckenzie","age":29,"gender":"F","address":"244 Columbus Place","employer":"Euron","email":"bradshawmckenzie@euron.com","city":"Hobucken","state":"CO"}
    }, {
      "_index" : "bank",
      "_type" : "_doc",
      "_id" : "1",
      "sort": [1],
      "_score" : null,
      "_source" : {"account_number":1,"balance":39225,"firstname":"Amber","lastname":"Duke","age":32,"gender":"M","address":"880 Holmes Lane","employer":"Pyrami","email":"amberduke@pyrami.com","city":"Brogan","state":"IL"}
    }, ...
    ]
  }
}
```

* took – time in milliseconds for Elasticsearch to execute the search
* timed_out – tells us if the search timed out or not
* _shards – tells us how many shards were searched, as well as a count of the successful/failed searched shards
* hits – search results
* hits.total – an object that contains information about the total number of documents matching our search criteria
  * hits.total.value - the value of the total hit count (must be interpreted in the context of hits.total.relation).
  * hits.total.relation - whether hits.total.value is the exact hit count, in which case it is equal to "eq" or a lower bound of the total hit count (greater than or equals), in which case it is equal to gte.
* hits.hits – actual array of search results (defaults to first 10 documents)
* hits.sort - sort value of the sort key for each result (missing if sorting by score)
* hits._score and max_score - ignore these fields for now

