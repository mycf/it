Apache反向代理session丢失

```
proxyPassReverse /mb  http://localhost:11200/mb
```

```
proxyPass        /mb  http://localhost:11200/mb
```

```
限制除了post请求
<LimitExcept POST>
    Require all denied #无条件禁止访问
</LimitExcept>
```

```
httpd yuchaofan$ docker run -p 8088:8088 -v ~/Documents/docker/httpd/conf/httpd.conf:/usr/local/apache2/conf/httpd.conf -v ~/Documents/docker/httpd/conf/extra/httpd-vhosts.conf:/usr/local/apache2/conf/extra/httpd-vhosts.conf -v ~/Documents/docker/httpd/logs/:/usr/local/apache2/logs/ --name httpd -d httpd

```



