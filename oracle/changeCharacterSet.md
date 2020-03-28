# 修改Linux上的Oracle12c编码集

查看字符集

```sql
select userenv('language') from dual;
```



```sql
SQL> shutdown
SQL> startup
SQL> alter system enable restricted session; 
SQL> alter system set job_queue_processes=0; 
SQL> alter system set aq_tm_processes=0; 
sql> alter database open; 
SQL> alter database character set internal_use AL32UTF8;
SQL> shutdown
SQL> startup
```

