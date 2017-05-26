---
title: mysql中sql_mode设置
date: 2017-05-26 11:27:15
tags: MySQL
---

## 背景

 最近线上出了一个问题，把原来的php项目的一个功能迁移到Java后，有一个sql报错，报错如下
 ```
Caused by: java.sql.SQLException: Data truncated for column 'password' at row 1
```

根据异常信息应该是数据超过字段长度，但是同样的sql在php项目中没有问题，看数据库中内容发现原来超出字段长度的被自动截断。在Java 项目截断临时解决。


## 问题分析

MySQL 中有个sql_mode表示对于一些非法SQL的处理方式，默认是空值。
原来的PHP项目使用的ci框架db配置中有一项 ，是否强制使用 "Strict Mode" 连接,线上的db配置默认是false，所以超过字段长度的内容被db自动截断了。
   
```
    'stricton' => FALSE,
```
在Java中使用JDBC 执行SQL时，默认会设置会话SQL_MODE='STRICT_TRANS_TABLES'，这时候超过字段长度直接返回异常了。


## sql_mode

查看当前sql_mode

```
SELECT @@GLOBAL.sql_mode;
SELECT @@SESSION.sql_mode;
SET GLOBAL sql_mode = '';
SET SESSION sql_mode = '';
```

重要的mode

1. ANSI

    使SQL语法满足标准的SQL规范

2. STRICT_TRANS_TABLES

   如果一个值不能插入到一个事务表，则中止操作。对于非事务表，如果是发生在单独一行插入或者多行的第一行则中止插入


3. TRADITIONAL

   当插入不正确的值时，使用错误代替警告




参考：[https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html)

