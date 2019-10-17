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

```
SELECT s.sid, s.serial# FROM v$locked_object lo, dba_objects ao, v$session s WHERE ao.object_id = lo.object_id AND lo.session_id = s.sid;
```

  


