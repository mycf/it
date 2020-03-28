

## 连接到Redis

* JedisConnectionFactory
* JredisConnectionFactory
* LettuceConnectionFactory
* SrpConnectionFactory

```java
@Bean
public RedisConnectionFactory rFactory() {
    return new JedisConnectionFactory();
}
```

## 使用RedisTemplate

* RedisTemplate
* StringRedisTemplate

```java
@Bean
public RedisTemplate redisTemplate(RedisConnectionFactory rFactory) {
    RedisTemplate redisTemplate = new RedisTemplate<>();
    redisTemplate.setConnectionFactory(rFactory);
    return redisTemplate;
}
```



