Oracle 是甲骨文公司开发的一款[关系型数据库](https://baike.baidu.com/item/关系型数据库/8999831?fr=aladdin)，它一款系统可移植性好、使用简单、功能强大的关系型数据库。它为各行业在各类环境下（服务器、虚拟机、微机环境下）可以快速搭建一种高效率、可靠性好、高吞吐量的数据库解决方案。

## Oracle特点

- [Oracle数据库](https://baike.baidu.com/item/Oracle数据库/3710800?fr=aladdin)具有完整的数据库管理功能、完备关系的产品以及具有分布式处理能力的数据库。
- 它对数据的可靠性、大量性、持久性、共享性提供了一套可靠的解决方案、而且可以轻松支持多用户、大事务量的事务处理。
- 它的优点就是可用性强、可扩展性强、数据安全性强、稳定性高，以及现阶段12C支持分布式数据处理。
- 它提供了一套严禁的逻辑结构、文件结构、相关恢复技术的解释和实现。

## **Oracle体系结构**

Oracle数据库实际上是一个数据的物理储存系统，这其中包括数据文件（ora/dbf）、参数文件、控制文件、联机日志等。

实例：一个操作系统只有一个Oracle数据库，但是可以安装多个Oracle实例，一个Oracle实例对应着一系列的后台进程（Backguound Processes)和内存结构（Memory Structures)。

数据文件：Oracle数据文件是数据存储的物理单位，数据库的数据是存储在表空间中的。而一个表空间可以由一个或多个数据文件组成，一个数据文件只能属于一个表空间，一旦数据文件被加入到某个表空间后，就不能删除这个文件，如果要删除某个数据文件，只能删除其所属于的表空间才 行。

表空间：表空间是Oracle 对物理数据库数据文件（ora/dbf）的逻 辑映射。一个数据库在逻辑上被划分成一到若干个表空间，每个表空间由同一磁盘上的一个或多个数据文件（datafile）组成，一个数据文件只能属于一个表空间。

oracle用户：表当中的数据是有Oracle用户放入到表空间当中的，而这些表空间会随机的把数据放入到一个或者多个数据文件当中。oracle对表数据的管理是通过用户对表的管理去查询，而不是直接对数据文件或表空间进行查询。因为不同用户可以在同一个表空间上面建立相同的表名。但是通过不同的用户管理自己的表数据。

![viewImages](https://raw.githubusercontent.com/mycf/it/master/assets/viewImages.png)



常用的SQL语句大致可以分为五类：

- 数据定义语言（DDL），包括 CREATE（创建）命令、 ALTER（修改）命令、 DROP（删除）命令等。
- 数据操纵语言（DML），包括 INSERT（插入）命令、 UPDATE（更新）命令、 DELETE（删除）命令、 SELECT … FOR UPDATE（查询）等。
- 数据查询语言（DQL），包括基本查询语句、 Order By 子句、 Group By 子句等。
- 事务控制语言（TCL），包括 COMMIT（提交）命令、 SAVEPOINT（保存点）命令、ROLLBACK（回滚）命令。   
- 数据控制语言（DCL）， GRANT（授权）命令、 REVOKE（撤销）命令。

```

sqlplus 用户名/密码@ip:host/实例名 as normal

```

 sysdba:数据库管理员身份。权限：打开（关闭）数据库服务器、备份（恢复）数据库、日志功能、会话限制、数据库管理功能等。

例如：sys用户必须用sysdba才能登陆，system用户用普通用户就可以登陆。

sysoper:数据库操作员身份 。权限：打开（关闭）数据库服务器、备份（恢复）数据库、日志功能、会话限制。

normal:普通用户。权限：操作该用户下的数据对象和数据查询，默认的身份是normal用户。

####  Oracle用户创建

```sql
-- Create the user 
create user student--用户名
  identified by "123456"--密码
  default tablespace USERS--表空间名
  temporary tablespace temp --临时表空间名
  profile DEFAULT    --数据文件（默认数据文件）
  account unlock; -- 账户是否解锁（lock:锁定、unlock解锁）
```

#### 用户权限

Oracle数据库用户权限分为：系统权限和对象权限两种。

系统权限：比如：create session可以和数据库进行连接权限、create table、create view 等具有创建数据库对象权限。

对象权限：比如：对表中数据进行增删改查操作，拥有数据库对象权限的用户可以对所拥有的对象进行相应的操作。

#### 数据库角色

oracle数据库角色是若干系统权限的集合，给Oracle用户进行授数据库角色，就是等于赋予该用户若干数据库系统权限。常用的数据库角色如下：

CONNECT角色：connect角色是Oracle用户的基本角色，connect权限代表着用户可以和Oracle服务器进行连接，建立session（会 话）。

RESOURCE角色：resouce角色是开发过程中常用的角色。 RESOURCE给用户提供了可以创建自己的对象，包括：表、视图、序列、过程、触发器、索引、包、类型等。

DBA角色：DBA角色是管理数据库管理员该有的角色。它拥护系统了所有权限，和给其他用户授权的权限。SYSTEM用户就具有DBA权限。

##### 授权

```sql
--GRANT 对象权限 on 对象 TO 用户    
grant select, insert, update, delete on JSQUSER to STUDENT;
 
--GRANT 系统权限 to 用户
grant select any table to STUDENT;
 
--GRANT 角色 TO 用户
grant connect to STUDENT;--授权connect角色
grant resource to STUDENT;--授予resource角色

-- Revoke 对象权限 on 对象 from 用户 
revoke select, insert, update, delete on JSQUSER from STUDENT;
 
-- Revoke 系统权限  from 用户
revoke SELECT ANY TABLE from STUDENT;
 
-- Revoke 角色（role） from 用户
revoke RESOURCE from STUDENT;


--修改用户信息
alter user STUDENT
  identified by ******  --修改密码
  account lock;--修改用户处于锁定状态或者解锁状态 （LOCK|UNLOCK ）
```

### 索引

1、Oracle 数据库会为表的主键和包含唯一约束的列自动创建索引，所以在建立唯一约束时，可以考虑该列是否必要建立。是否经常要作为查询条件。

2、如果某个表的数据量较大（十几二十万以上），某列经常作为where的查询条件，并且检索的出来的行数经常是小于总表的5%，那该列可以考虑建立索引。

3、对于两表连接的字段，应该考虑建立索引。如果经常在某表的一个字段进行Order By 则也经过进行索引。

4、不应该在小表上建立索引。上面也说过，小表之间查询的数据会比建立索引的查询速度更快，但是在某些字段，如性别：只有男、女和未知三种数据时，可以考虑位图索引，可以增加查询效率。

5、经常进行DML操作，即经常进行增删改的操作的表，创建表索引时就要权衡一下，因为建索引会导致进行DML操作时速度变慢。所以可以根据实际情况，选择某些字段建立索引，而不能盲目乱建。

## 索引的类别：

适当的使用索引可以提高数据检索速度，那Oracle有哪些类型的索引呢？

**1、b-tree索引：**Oracle数据中最常见的索引，就是b-tree索引，create index创建的normal就是b-tree索引，没有特殊的必须应用在哪些数据上。

**2、bitmap位图索引：**位图索引经常应用于列数据只有几个枚举值的情况，比如上面说到过的性别字段，或者我们经常开发中应用的代码字段。这个时候使用bitmap位图索引，查询效率将会最快。

**3、函数索引：**比如经常对某个字段做查询的时候经常是带函数操作的，那么此时建一个函数索引就有价值了。例如：trim（列名）或者substr(列名)等等字符串操作函数，这个时候可以建立函数索引来提升这种查询效率。

**4、hash索引：**hash索引可能是访问数据库中数据的最快方法，但它也有自身的缺点。创建hash索引必须使用hash集群，相当于定义了一个hash集群键，通过这个集群键来告诉oracle来存储表。因此，需要在创建HASH集群的时候指定这个值。存储数据时，所有相关集群键的行都存储在一个数据块当中，所以只要定位到hash键，就能快速定位查询到数据的物理位置。

**5、reverse反向索引：**这个索引不经常使用到，但是在特定的情况下，是使用该索引可以达到意想不到的效果。如：某一列的值为{10000,10001,10021,10121,11000,....}，假如通过b-tree索引，大部分都密集发布在某一个叶子节点上，但是通过反向处理后的值将变成{00001,10001,12001,12101,00011,...}，很明显的发现他们的值变得比较随机，可以比较平均的分部在各个叶子节点上，而不是之前全部集中在某一个叶子节点上，这样子就可大大提高检索的效率。

**6、分区索引和分区表的全局索引：**这两个索引是应用在分区表上面的，前者的分区索引是对分区表内的单个分区进行数据索引，后者是对分区表的全表进行全局索引。分区表的介绍，可以后期再做单独详解，这里就不累述了。

```sql
create[unique]|[bitmap] index index_name --UNIQUE表示唯一索引、BITMAP位图索引
on table_name(column1,column2...|[express])--express表示函数索引
[tablespace tab_name] --tablespace表示索引存储的表空间
[pctfree n1]    --索引块的空闲空间n1
[storage         --存储块的空间
 (
    initial 64K  --初始64k
    next 1M
    minextents 1
    maxextents unlimited
 
)];
```

**语法解析：**

1、UNIQUE:指定索引列上的值必须是唯一的。称为唯一索引，BITMAP表示位图索引。

2、index_name：指定索引名。

3、tabl_name：指定要为哪个表创建索引。

4、column_name：指定要对哪个列创建索引。我们也可以对多列创建索引，这种索引称为组合索引。也可以是函数表达式，这种就是函数索引。

**修改索引：**

1、重命名索引：

```sql
alter index index_old rename to index_new; --重新命名索引
```

2、合并索引、重新构造索引：我们索引建好后，经过很长一段时间的使用，索引表中存储的空间会产生一些碎片，导致索引的查询效率会有所下降，这个时候可以合并索引，原理是按照索引规则重新分类存储一下，或者也可以选择删除索引重新构造索引。

```sql
alter index index_name coalesce;--合并索引
alter index index_name rebuild;--重新构造
```



------

**删除索引：**

```sql
drop index index_name;
```

------

**查看索引：**

```sql
select t.INDEX_NAME,--索引名字    
t.index_type,--索引类型    
t.TABLESPACE_NAME,--表空间    
t.status,--状态    
t.UNIQUENESS--是否唯一索引 from all_indexes T  where t.INDEX_NAME='index_name';
```

#### 索引失效

1. 在索引列上使用函数时不会使用索引
2. 索引的列进行隐式的类型转换
3. WHERE 子句中使用不等于操作
4. 使用 IS NULL 和 IS NOT NULL
5. 组合索引

查看字符集

```sql
select userenv('language') from dual;
```

如果显示如下，一个汉字占用两个字节

SIMPLIFIED CHINESE_CHINA.ZHS16GBK

如果显示如下，一个汉字占用三个字节

SIMPLIFIED CHINESE_CHINA.AL32UTF8

可以用以下语句查询一个汉字占用的字节长度

select lengthb('你') from dual;



```
查看oracle实例名
ps -ef|grep ora_


查看监听
lsnrctl status
启动监听器
lsnrctl start
停止监听器
lsnrctl stop

导出指定用户下的表
exp mbank/mbank@mbank owner=mbank file=xxx.dmp
导出指定表
exp mbank/mbank@mbank tables=table_name file=xx.dmp
导入
imp mbank/mbank@mbank file=xxx.dmp full=y ignore=y

sqlplus / as sysdba
查看当前的连接用户
show user
创建用户
create user username identified by passwd;
create user username identified by password 
default tablespace user_data 
temporary tablespace user_temp; 
用户授权
grant dba to username；
使用新的用户连接数据库
connect mbank/mbank@mbank

删除实例
vi /etc/oratab 删除对应实例
删除对应文件夹 find /oracle -name sid_name|xargs rm -rf {}

set head off􏲐􏲨􏲨􏲩􏲪􏲫􏰏􏰡􏲬􏲭􏲮输出域标题，缺省为􏲩􏲪􏲫􏰏􏰡􏲬􏲭􏲮on
set linesize 20000􏲐
set echo off􏲐􏲸􏲹 显示命令行本身缺省为on
set feedback off    回显本次命令处理的记录条数
set pagesize 0    为避免分页，可设置0

set termout off
set trimout on
set trimspool on􏲐􏳈􏳉􏳏􏰽􏰈􏳐spool􏳑􏲨􏲩􏲺􏰣􏰋􏳋􏳌􏳍􏳎􏰡􏲬􏲭􏲮off


--查询默认表空间
select default_tablespace from user_users;


--查询当前用户下的所以表
select table_name,tablespace_name,status
from USER_TABLES;

--查询当前用户下的索引
select index_name,table_name,tablespace_name,status,table_owner from USER_INDEXES;

--导出指定用户下所有表
imp embank/embank@mbank file=czembank_20190912.dmp log=imp.log full=y ignore=y


--lob类型表空间、索引空间迁移
SELECT 'ALTER TABLE ' || T.TABLE_NAME || ' MOVE TABLESPACE EMBANKIDX LOB (' || L.COLUMN_NAME || ') STORE AS ' ||
       L.SEGMENT_NAME || ' (TABLESPACE EMBANKIDX);'
FROM user_TABLES T,
     user_LOBS L
WHERE T.TABLE_NAME = L.TABLE_NAME;

--普通表空间迁移
select 'alter table ' || table_name || ' move tablespace EMBANKDATA;'
from user_tables
where tablespace_name = 'USERS';

--普通索引空间迁移
SELECT 'alter index "'|| index_name ||'" rebuild online tablespace EMBANKIDX;'
FROM user_indexes
WHERE index_type = 'NORMAL'
  AND table_owner = 'EMBANK'
  AND dropped = 'NO'
  AND TABLESPACE_NAME = 'USERS';


-- 清空回收站
purge recyclebin;

-- 查询回收站内容
select * from user_recyclebin;
```

### 锁表

```plsql
select
    b.username,
    b.sid,
    b.serial#,
    logon_time,
    c.object_name
from v$locked_object a,
    v$session b,
    dba_objects c
where
  a.session_id = b.sid
    and c.object_id = a.object_id;

alter SYSTEM kill session 'sid,SERIAL#';
```

  查看当前用户下所有表

```sql
select table_name,tablespace_name from user_tables;
```

创建表空间

```
create tablespace mbank datafile '/oracle/oradata/mbank/mbank01.dbf' size 300m autoextend on;
```

