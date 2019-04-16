表误删

```
spool flush.sql
select 'flushback table '|| original_name||' to before drop;' from user_recyclebin where type='TABLE'；
spool off
```

导出指定用户下的表

exp mbank/mbank@mbank owner=mbank file=xxx.dump

导入

imp mbank/mbank@mbank file=xxx.dump full=y

