## Index

```
# 测试 Index
PUT /crud_index/_doc/1  
{
  "desc":"测试新建"
}
```

## create

仅使用第3中

```
# 测试 create
PUT /crud_index/_create/2
{
  "desc":"测试新建2"
}
PUT /crud_index/_doc/3?op_type=create
{
  "desc":"测试新建3"
}
POST crud_index/_doc/4
{
  "desc":"测试新建4"
}
```

## update

```
# 测试 UPDATE
POST /crud_index/_doc/1
{
  "desc":"测试修改"
}
```

## delete

```
# 测试 delete
DELETE /crud_index
DELETE /crud_index/_doc/pwfJjmwB7UPaZedsXca6
```

## get

```
# 查询所有
GET /crud_index/_search
# 查询单个
GET /crud_index/_doc/3
```

