数据库误删表

```
spool flush.sql
select 'flushback table '|| original_name||' to before drop;' from user_recyclebin where type='TABLE'；
spool off
```



