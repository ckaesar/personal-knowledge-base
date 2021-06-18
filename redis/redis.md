## redis

## 使用场景

比如集合计算



## 数据结构与对象

Redis数据库的每个键值对都是由对象组成，数据库键总是一个字符串对象，数据库的值有五种对象类型：

字符串对象（string object）

`127.0.0.1:6379> set msg "hello world"`

列表对象（list object）

`127.0.0.1:6379> RPUSH numbers 1 3 5 7 9`

哈希对象（hash object）

集合对象（set object）

有序集合对象（sorted set object）



查看所有的key

`127.0.0.1:6379> keys *`



#### 简单动态字符串（simple dynamic string，SDS）

SDS是Redis的默认字符串表示。除了用来保存数据库的字符串值之外，SDS还被用作缓冲区（buffer）：AOF模块中的AOF缓冲区，以及客户端状态中的输入缓冲区，都是有SDS实现的。

SDS的数据结构

```c
struct sdshdr {
		// 记录buf数组􏰪已使􏰻用字节的􏱄􏱞数量
		// 􏰿􏱰等于SDS所保存字符串的长度
		int len;
		// 记录buf数组中未使用字节的数量
		int free;
		// 字节数􏱄组，用于保存字符串
    char buf[];
   };
```

![image-20210616000635548](/Users/chengkai/Library/Application Support/typora-user-images/image-20210616000635548.png)

SDS比C字符串相比的优点

- 因为记录了长度信息，可以在常数复杂度获取字符串长度
- 杜绝缓冲区溢出，因为SDS在进行修改时，会检查SDS的空间是否满足要求，如果不满足，首先扩展空间，然后再进行修改
- 减少修改字符串时带来的内存重分配次数

#### 链表

#### 字典

#### 跳跃表

#### 整数集合

#### 压缩列表

#### 对象

## 单机数据库的实现

#### 数据库的实现原理

#### RDB持久化

#### AOF持久化

#### 事件

文件事件

事件事件

#### 客户端的运行机制

#### 服务器端的运行机制

## 多机数据库的实现

#### Sentinel

#### 复制（replication）

集群（cluster）

## 独立功能的实现

#### 发布与订阅

#### 事务

#### Lua脚本

#### 排序

#### 二进制位数组

#### 慢查询日志

#### 监视器

