Apache反向代理session丢失

```
proxyPassReverse /mbank  http://172.21.8.12:11200/mbank_srcb
```

```
proxyPass        /mbank  http://172.21.8.12:11200/mbank_srcb
```

```
<LimitExcept POST>
  Require valid-user
</LimitExcept>
```



