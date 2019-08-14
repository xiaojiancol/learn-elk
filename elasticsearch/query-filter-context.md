
# Query and filter context

https://www.elastic.co/guide/en/elasticsearch/reference/current/query-filter-context.html

## Relevance scores
By default, Elasticsearch sorts matching search results by relevance score, which measures how well each document matches a query.

默认，Elasticsearch 搜索结果按照相关性评分排列。  

The relevance score is a positive floating point number, returned in the _score meta-field of the search API. The higher the _score, the more relevant the document. While each query type can calculate relevance scores differently, score calculation also depends on whether the query clause is run in a query or filter context.  

相关性评分是一个正小数。... 每个 query type 可以计算出不同的相关性评分，评分计算依赖查询短语执行在一个 query 中，还是一个 filter context 中。  

## Query context
In the query context, a query clause answers the question “How well does this document match this query clause?” Besides deciding whether or not the document matches, the query clause also calculates a relevance score in the _score meta-field.

Query context 中，一个 query clause 回答这样的问题 "文档有多匹配这个 query clause?"  

Query context is in effect whenever a query clause is passed to a query parameter, such as the query parameter in the search API.  

当 一个 query clause 传入 a query parameter 时，Query context 会生效

## Filter context

In a filter context, a query clause answers the question “Does this document match this query clause?” The answer is a simple Yes or No — no scores are calculated. Filter context is mostly used for filtering structured data, e.g.

在一个 filter context 中，一个 query clause 回答这样的问题 " 这个文档匹配整个 query clause 吗？"当然回答也不需要算法  

* Does this timestamp fall into the range 2015 to 2016?
* Is the status field set to "published"?
Frequently used filters will be cached automatically by Elasticsearch, to speed up performance.

常用的 filters 会被自动缓存  

Filter context is in effect whenever a query clause is passed to a filter parameter, such as the filter or must_not parameters in the bool query, the filter parameter in the constant_score query, or the filter aggregation.

当一个 query clause 传入 a filter parameter 时 Filter context 会生效，例如 filter 或者 must_not parameters in the bool query, 在 constant_score query 中的 filter parameter，或者 filter aggregation。  

## Example of query and filter contexts  

Below is an example of query clauses being used in query and filter context in the search API. This query will match documents where all of the following conditions are met:  

下面是一个 使用了 query 和 filter context 的 query clause 例子：  

The title field contains the word search.
The content field contains the word elasticsearch.
The status field contains the exact word published.
The publish_date field contains a date from 1 Jan 2015 onwards.

```
curl -X GET "localhost:9200/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { 
    "bool": { 
      "must": [
        { "match": { "title":   "Search"        }},
        { "match": { "content": "Elasticsearch" }}
      ],
      "filter": [ 
        { "term":  { "status": "published" }},
        { "range": { "publish_date": { "gte": "2015-01-01" }}}
      ]
    }
  }
}
'
```

	
* The query parameter indicates query context.

* The bool and two match clauses are used in query context, which means that they are used to score how well each document matches.

* The filter parameter indicates filter context. Its term and range clauses are used in filter context. They will filter out documents which do not match, but they will not affect the score for matching documents.

>Scores calculated for queries in query context are represented as single precision floating point numbers; they have only 24 bits for significand’s precision. Score calculations that exceed the significand’s precision will be converted to floats with loss of precision.


>Use query clauses in query context for conditions which should affect the score of matching documents (i.e. how well does the document match), and use all other query clauses in filter context.