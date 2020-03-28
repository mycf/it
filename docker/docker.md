列出本地主机的镜像

```
docker images
```

查找可用版本

```
➞  docker search redis
```

拉取最新镜像

```
docker pull redis:latest
```

运行容器

```shell
docker run -itd --name redis -p 6379:6379 redis
```

- **-i**: 交互式操作。
- **-t**: 终端。
- -d: 后台运行
- **-P :**是容器内部端口**随机**映射到主机的高端口。
- **-p :** 是容器内部端口绑定到**指定**的主机端口。

```bash
docker images


docker exec -it redis redis-cli

//启动zookeeper
docker run --name zookeeper --restart always -d -p 2181:2181 zookeeper
```



