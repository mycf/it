```
查看redis集群状态
redis-trib.rb check host:port

redis-trib.rb help

进入redis命令行

redis-cli -p localhost -h 7001 -a 3edc4RFV
查看redis集群状态
cluster nodes
cluster info


```

redis是通过docker安装的

##### 进入redis命令行

```
➞docker exec -it redis redis-cli
127.0.0.1:6379>
```

**提示** redis命令不区分大小写

#### 获得符合规则的键名列表￼         

#### `KEYS pattern`![](/assets/import5.png)

注意⚠️KEYS命令需要遍历Redis中的所有键，当键的数量较多时会影响性能，不建议在生产环境中使用。





