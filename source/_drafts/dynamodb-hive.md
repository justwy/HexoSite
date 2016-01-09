---
title: 如何用EMR批量加载Dynamodb
date: 2016-01-07 21:35:32
tags:
    - aws
    - DynamoDB
    - Amazon
    - cloud
categories: tech
---

最近在做一个关于DynamoDB的项目。

>Amazon DynamoDB 是一项快速灵活的 NoSQL 数据库服务，适合所有需要一致性且延迟低于 10 毫秒的任意规模的应用程序。

每天要从一个feed load到DB. 一共差不多有4千万条数据。之前一直在用`Oracle DB`。 Oracle限制了现有服务的horizental scalability。有两个方案代替Oracle DB， 一个是类似于Berkeley DB的私有的只读数据库，另外一个是DynamoDB。

之前一直看好DynamoDB。维护成本低，性能满足要求。但有一个问题使我放弃了DynamoDB。
