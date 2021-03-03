### 实战

```sql
//  切换数据库
use admin

// 检查当前选择的数据库
db

// 查看所有用户
show users

// 查看所有的数据库
show databases
show dbs

// 添加超级管理员账号
db.createUser({
   user:"myadmin",
   pwd:"secret",
   roles:[{role:"root", db:"admin"}]
})

db.auth()

// 创建一个数据库
use runoob

// 刚创建，在数据库的列表中看不到，要显示它，需要想runoob数据库插入一些数据
show dbs

// 向数据库插入数据
db.runoob.insert({"name":"ck"})


// 再次查看数据库列表，就能看到新建的数据库了。把数据库中的数据删了后，还是能看到该数据库
show dbs
// MongoDB中默认的数据库为test，如果没有创建新的数据库，集合将存放在test数据库中

// 删除数据
db.runoob.deleteOne({"name":"ck"})
db.runoob.find()

// 删除数据库。删除的是当前的数据库
use runoob
db.dropDatabase()

// 创建集合，类似于数据库中的表
db.createCollection("mongocollection")

/**
 创建一个固定集合，整个集合的空间大小为6142800KB，文档最大个数为10000个。
 参数说明：
 capped: 布尔值，（可选）如果为 true，则创建固定集合。固定集合是指有着固定大小的集合，当达到最大值时，它会自动覆盖最早的文档。当该值为 true 时，必须指定 size 参数。
 autoIndexId:  布尔值，3.2 之后不再支持该参数。（可选）如为 true，自动在 _id 字段创建索引。默认为 false。
 size: 数值，（可选）为固定集合指定一个最大值，即字节数。如果 capped 为 true，也需要指定该字段。
 max: 数值，可选）指定固定集合中包含文档的最大数量。
*/
db.createCollection("mymongo", {capped: true, autoIndexId: true, size: 6142800, max: 10000})

// 在 MongoDB 中，不需要创建集合。当插入一些文档时，MongoDB 会自动创建集合。
// 如下面的例子，在执行之前，集合 testmongo 是不存在的，执行完后，就有了，同时也插入了文档。
db.testmongo.insert({"name":"ck"})

// 查看已有的集合
show tables
show collections

// 删除集合。删除完后再查看集合就看不到已经删除的集合了
db.mongocollection.drop()
show collections

// 插入文档
db.runoob.find()
db.runoob.insert({"name":"ck1", "age": 10})
db.runoob.insertOne({"name": "ck2", "age": 20})
db.runoob.insertMany([{"name": "ck3", "age": 30}, {"name": "ck4", "age": 40}])

// 将匹配到 name 为 ck1 的文档，修改 name 为 ck8，修改 age 为 80
db.runoob.replaceOne({"name": "ck1"}, {"name": "ck8", "age": 50})

// 查询主键 _id 为 603f1d18496a6f6fe5026216 的文档
db.runoob.find({"_id": ObjectId("603f7996496a6f6fe5026222")})



/** 角色说明
1. 数据库用户角色：read、readWrite;
2. 数据库管理角色：dbAdmin、dbOwner、userAdmin；
3. 集群管理角色：clusterAdmin、clusterManager、clusterMonitor、hostManager；
4. 备份恢复角色：backup、restore；
5. 所有数据库角色：readAnyDatabase、readWriteAnyDatabase、userAdminAnyDatabase、dbAdminAnyDatabase
6. 超级用户角色：root
// 这里还有几个角色间接或直接提供了系统超级用户的访问（dbOwner 、userAdmin、userAdminAnyDatabase）
7. 内部角色：__system
*/
/**
read:允许用户读取指定数据库
readWrite:允许用户读写指定数据库
dbAdmin：允许用户在指定数据库中执行管理函数，如索引创建、删除，查看统计或访问system.profile
userAdmin：允许用户向system.users集合写入，可以找指定数据库里创建、删除和管理用户
clusterAdmin：只在admin数据库中可用，赋予用户所有分片和复制集相关函数的管理权限。
readAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读权限
readWriteAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读写权限
userAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的userAdmin权限
dbAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的dbAdmin权限。
root：只在admin数据库中可用。超级账号，超级权限
*/


```



### 问题记录

###### 在datagrip中执行db.dropDatabase()时，报异常

> java.lang.Exception: TypeError: invokeMember (dropDatabase) on JavaObject[com.mongodb.mongosh.service.JavaServiceProvider@6bae3469 (com.mongodb.mongosh.service.JavaServiceProvider)] failed due to: Arity error - expected: 3 actual: 2 TypeError: invokeMember (dropDatabase) on JavaObject[com.mongodb.mongosh.service.JavaServiceProvider@6bae3469 (com.mongodb.mongosh.service.JavaServiceProvider)] failed due to: Arity error - expected: 3 actual: 2 at Proxy.<anonymous> (all-standalone.js:77453:67) at step (all-standalone.js:77314:23) at Object.<anonymous> (all-standalone.js:77295: ...

原因未知，找到了一个说法说是已知问题，修复中，后面更新驱动后再验证下

[Stack Overflow上提的同样的问题](https://stackoverflow.com/questions/64411218/drop-database-in-datagrip-jetbrains)

