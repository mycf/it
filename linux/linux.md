### while

```shell
while true;do ll;sleep 2;done;
```

### crontab

添加crontab用户

```shell
vi /etc/cron.allow
```

添加定时任务

```shell
crontab -e #进入编辑模式
0 1 * * * /home/mbank/log.sh	
wq #保存退出
```

