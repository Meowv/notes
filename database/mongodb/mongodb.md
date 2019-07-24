# MongoDB Shell 命令

更新列名

```sql
db.Stores.update({}, {$rename : {"StoreId" : "MetaId"}}, false, true)
```

查询长度

```sql
db.getCollection("Stores_Navigations").find({$where:'this.StoreId.length>2'},{Name:0})
```

查询总条数

```sql
db.getCollection("Stores_BusinessLogs").find({}).count()
```

区间查询

```sql
db.getCollection("Cards").find({'StoreId':1139,'CardNo':{'$gte':'90225001','$lte':'90295000'}})
```

排序 1升序 -1降序

```sql
db.getCollection("Stores_BusinessLogs").find().sort({"CreationTime":1})
```

更改字段类型

```sql
// 16代表int
db.Stores_Experts.find({'PicId' : { $type : 16 }}).forEach(function(x) {x.PicId = String(x.PicId);db.Stores_Experts.save(x); })
```

字段类型表

| 类型 | 对应数字 | 别名 |
| :--- | :--- | :--- |
| Double | 1 | double |
| String | 2 | string |
| Object | 3 | object |
| Array | 4 | array |
| Binary data | 5 | binData |
| Undefined | 6 | undefined |
| ObjectId | 7 | objectId |
| Boolean | 8 | “bool” |
| Date | 9 | “date” |
| Null | 10 | “null” |
| Regular Expression | 11 | “regex” |
| DBPointer | 12 | “dbPointer” |
| JavaScript | 13 | “javascript” |
| Symbol | 14 | “symbol” |
| JavaScript\(with scope\) | 15 | “javascriptWithScope” |
| 32-bit integer | 16 | “int” |
| Timestamp | 17 | “timestamp” |
| 64-bit integer | 18 | “long” |
| Min key | -1 | “minKey” |
| Max key | 127 | “maxKey” |
| - | - | - |

添加一个字段. table 代表表名 , 添加字段 content,字符串类型

```sql
db.table.update({}, {$set: {content:""}}, {multi: true})
```

删除一个字段

```sql
db.table.update({},{$unset:{content:""}},false, true)
```

清空数据

```sql
db.table.remove({})
```

查询指定列

```sql
db.news.find( {}, { id: 1, title: 1 } )
```

修改列表

```sql
db.getCollection('Orders_Scores').update({},{$rename:{"OId":'MetaId'}},false,true)
```

添加索引

```sql
db.test.createIndex({"username":1})
db.Users_MobileAuthCodes.createIndex({"Code":1,"Mobile":1,"ExpiresTime":1},{"name":"MobileAuthCodes_Validate"})
```

group分组

```sql
db.getCollection("Users_GaoKaoScores").aggregate([{$match:{"IsDeleted":false}},{$group : {_id : "$UserId", count : {$sum : 1}}},{$sort:{"count":-1}}])
```

按条件修改update

```sql
db.getCollection('Stores_Navigations').update( 
    // query
    {
        "MenuKey" : 28
    },

    // update
    {
        $set:{"Url":"/tzy/choosebatch?type=3"}
    },
    false,  
    true
);
```
