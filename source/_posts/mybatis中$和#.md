---
title: mybatis标签
date: 2017年11月29日 21点46分
tags: 
-  mybatis  
categories:
- mybatis  
---

# mybatis中的#和$的区别


1. 将#传入的数据都当成一个字符串，会对自动传入的数据加一个双引号。如：order by #user_id#，如果传入的值是111,那么解析成sql时的值为order by "111", 如果传入的值是id，则解析成的sql为order by "id".

2. 将￥传入的数据直接显示生成在sql中。如：order by $user_id$，如果传入的值是111,那么解析成sql时的值为order by user_id,  如果传入的值是id，则解析成的sql为order by id.

3. 井方式能够很大程度防止sql注入。

4.$方式无法防止Sql注入。

5.$方式一般用于传入数据库对象，例如传入表名.
　　
6.一般能用#的就别用$.


MyBatis排序时使用order by 动态参数时需要注意，用$而不是#