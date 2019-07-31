Apache反向代理session丢失

```
proxyPassReverse /mbank  http://172.21.8.12:11200/mbank_srcb
```

```
proxyPass        /mbank  http://172.21.8.12:11200/mbank_srcb
```

```
限制除了post请求
<LimitExcept POST>
    Require all denied #无条件禁止访问
</LimitExcept>
```



