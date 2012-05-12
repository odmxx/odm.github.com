---
layout: post
title: timesheet
description:
- timesheet
categories:
- 无 
tags:
- 
---
2012-05-01
windows下玩了玩redis,java连接了一把
http://blog.nosqlfan.com 看些文章

NoSQL是什么？NoSQL的发展史。NoSQL的主流产品有哪些？NoSQL何传统关系型数据库相比有什么优缺点？

这些内容都被很多文章讨论过很多遍，但是不同的描述方式可能能触到不同人的思维G点。
=========
Redis 运维实际经验纪录之一
http://blog.nosqlfan.com/html/324.html
赞，特别是里面的为什么要调到每30分钟有一次写，才写数据
==========
hadoop的1TB排序 看不懂
http://blog.nosqlfan.com/html/417.html
＝＝＝＝＝＝＝＝＝＝
Redis容量及使用规划
主要讨论Redis未启用VM支持情况

1. Schema

MySQL: 需事先设计
Memcached: 无需设计
Redis: 小型系统可以不用，但是如果要合理的规划及使用Redis，需要事先进行类似如下一些规划

    数据项: value保存的内容是什么，如用户资料
    Redis数据类型: 如String, List
    数据大小: 如100字节
    记录数: 如100万条(决定是否需要拆分)
    ⋯⋯

上面的规划就是一种schema，为什么Redis在大型项目需要事先设计schema？因为Redis服务器有容量限制，数据容量不能超出物理内存大小，同时考虑到业务数据的可扩充性，记录数会持续增多、单条记录的内容也都会增长，因此需要提前规划好容量，数据架构师就是通过schema来判断当前业务的Redis是否需要“分库分表”以满足可扩展需求。


2. 容量及带宽规划

容量规划
MySQL: < 硬盘大小
Memcached: < RAM
Redis: < RAM

带宽规划
由于Redis比MySQL快10倍以上，因此带宽也是需要事先规划，避免带宽跑满而出现瓶颈。
3. 性能规划(QPS)

当系统读写出现瓶颈，通常如何解决？
MySQL
写: 拆分到多服务器
读: (1) 拆分 (2) 写少也可以通过增加Slave来解决

Memcached
读写: 都通过hash拆分到更多节点。

Redis:
写：拆分
读: (1) 拆分 (2) 写少也可以通过增加Slave来解决
4. 可扩展性

MySQL: 分库分表
Memcached: hash分布
Redis：也可以分库，也可以hash分布
小结

通过以上分析，Redis在很多方面同时具备MySQL及Memcached使用特征，在某些方面则更像MySQL。
由于Redis数据不能超过内存大小，一方面需要进行事先容量规划，保证容量足够；另外一方面设计上需要防止数据规模无限制增加，进而导致Redis不可扩展。
Redis需要象MySQL一样预先设计好拆分方案。
小问题

在MySQL中，通过预先建立多表或者库可以在业务增长时候将这些表或库一分为二部署到更多服务器上。
在Redis中，“分库分表”应当如何实现？有什么好的设计模式？
＝＝＝＝＝＝＝＝＝＝＝＝＝
视觉中国的NoSQL之路：从MySQL到MongoDB
http://blog.nosqlfan.com/html/1155.html
＝＝＝＝＝＝＝＝＝＝＝＝＝＝
射手分支项目-基于MongoDB的开源短网址服务
简单的应用与海量请求的组合
http://blog.splayer.org/index.php/2010/12/seso-me-shorten-url/
＝＝＝＝＝＝＝＝＝＝＝＝
NoSQL架构实践（一）——以NoSQL为辅

NoSQL为镜像（代码完成模式 ）

//写入数据的示例伪代码
//data为我们要存储的数据对象
data.title=”title”;
data.name=”name”;
data.time=”2009-12-01 10:10:01”;
data.from=”1”;
id=DB.Insert(data);//写入MySQL数据库
NoSQL.Add(id,data);//以写入MySQL产生的自增id为主键写入NoSQL数据库
在某些可以根据主键查询的地方，使用高效的NoSQL数据库查询，这样就节省了MySQL的查询，用NoSQL的高性能来抵挡这些查询。
等等
=========
Redis资料汇总
http://blog.nosqlfan.com/html/1282.html
一.redis 环境搭建
二.redis 数据类型
三.redis 排序
四.redis 事务
五.redis pipeline
六.redis 发布订阅
七.redis 持久化
八.redis 主从复制
九.redis学习笔记之虚拟内存
十. redis java client
========
事务和两阶段提交
http://blog.nosqlfan.com/html/3007.html