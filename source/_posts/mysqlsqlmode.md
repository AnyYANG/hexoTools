---
title: 由Mydsql datetime的默认值不能为0000-00-00 00：00：00引出的sqlmode问题
date: 2017-08-08 13:02:52
tags: 
- mysql sqlmode
categories:
- mysql  
---

## sqlmode 的引起的异常
  最近在导入数据库的时候，一直没有成功， 没成功的原因在于mysql5.7.18（我所使用的版本）中不允许字段中的datetime或者timestamp格式的字段的默认值为0000-00-00 00：00：00。所以每次导入的时候，都提示非法的默认值 for  字段名。 

## 问题引起的原因
[sql_mode](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html) 
mysql数据库sqlmode中设置了严格模式。  这种模式mysql在执行前会进行严格的sql校验判断。所以会爆出这个错误。

>  Strict mode controls how MySQL handles invalid or missing values in data-change statements such as INSERT or UPDATE. A value can be invalid for several reasons. For example, it might have the wrong data type for the column, or it might be out of range. A value is missing when a new row to be inserted does not contain a value for a non-NULL column that has no explicit DEFAULT clause in its definition. (For a NULL column, NULL is inserted if the value is missing.) Strict mode also affects DDL statements such as CREATE TABLE.

## sqlmode的常见级别

TRADITIONAL模式：严格模式，当向mysql数据库插入数据时，进行数据的严格校验，保证错误数据不能插入，报error错误。用于事物时，会进行事物的回滚。 
* NO_ZERO_IN_DATE：在严格模式下，不允许日期和月份为零
* NO_ZERO_DATE：设置该值，mysql数据库不允许插入零日期，插入零日期会抛出错误而不是警告。
STRICT_TRANS_TABLES模式：严格模式，进行数据的严格校验，错误数据不能插入，报error错误。 
ANSI	更改语法和行为，使其更符合标准SQL。



## sqlmode 的设置
  查看当前系统的sql_mode:  select @@sql_mode;  
在my.cnf或者my.ini添加如下配置
[mysqld]
sql_mode='ONLY_FULL_GROUP_BY,NO_AUTO_VALUE_ON_ZERO,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,
ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION,PIPES_AS_CONCAT,ANSI_QUOTES'
或者
 set global sql_mode=''