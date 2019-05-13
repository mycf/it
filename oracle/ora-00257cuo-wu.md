

```
归档日志满了
rman target/
crosscheck archivelog all;
delete archivelog util time 'sysdate-1';
```



