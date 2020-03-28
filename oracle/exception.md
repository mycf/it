###### **ora-00257 archiver error. connect interval only,unit freed** 

```
rman target /
crosscheck archivelog all;
delete archivelog util time 'sysdate-1';
```

