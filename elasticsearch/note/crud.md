update:  post indexName/_doc
{ 文档内容 }

create: put indexName/_doc/id?op_type=create
{
  文档内容
}
或者 put indexName/_create/id



get: get indexName/_doc/id
index: put indexName/_doc/id  先删除再写入

update: post indexName/_update/id ?
{
  "doc":{

  }
}

mget msearch bulk