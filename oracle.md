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
```



