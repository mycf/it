



###### Spring 3.1内置了五个缓存管理器实现

* SimpleCacheManager
* NoOpCacheManager
* ConcurrentMapCacheManager
* CompositeCacheManager
* EhCacheCacheManager

Spring 3.2引入了另外一个缓存管理器，这个管理器可以用在基于JCache（JSR-107）的缓存
提供商之中。除了核心的Spring框架，Spring Data又提供了两个缓存管理器：

* RedisCacheManager（来自于Spring Data Redis项目）
* GemfireCacheManager（来自于Spring Data GemFire项目）



```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:cache="http://www.springframework.org/schema/cache" 
    xmlns:jee="http://www.springframework.org/schema/jee" xsi:schemaLocation="http://www.springframework.org/schema/jee    http://www.springframework.org/schema/aop/spring-jee.xsd
    http://www.springframework.org/schema/beans    http://www.springframework.org/schema/aop/spring-beans.xsd http://www.springframework.org/schema/cache    http://www.springframework.org/schema/aop/spring-cache.xsd">
    <!-- 启用缓存 -->
    <cache:annotation-driven/>  
    <!-- 声明缓存管理器 -->
    <bean id="cacheManager" class="org.springframework.cache.concurrent.ConcurrentMapCacheManager"/> 
</beans>
```



```java
package com.ycf.maven.spring.config;

import org.springframework.cache.CacheManager;
import org.springframework.cache.annotation.EnableCaching;
import org.springframework.cache.concurrent.ConcurrentMapCacheManager;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

/**
 * CachingConfig
 */
@Configuration
@EnableCaching	//启用缓存
public class CachingConfig {

    @Bean
    public CacheManager cacheManager() {
        return new ConcurrentMapCacheManager();
    }
}
```



```java
package com.ycf.maven.spring.config;

import org.springframework.cache.CacheManager;
import org.springframework.cache.annotation.EnableCaching;
import org.springframework.cache.concurrent.ConcurrentMapCacheManager;
import org.springframework.cache.ehcache.EhCacheManagerFactoryBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.ClassPathResource;

/**
 * CachingConfig
 */
@Configuration
@EnableCaching
public class CachingConfig {

    @Bean
    public CacheManager cacheManager() {
        return new ConcurrentMapCacheManager();
    }

    @Bean
    public EhCacheManagerFactoryBean ehcache() {
        EhCacheManagerFactoryBean ehCacheManagerFactoryBean = new EhCacheManagerFactoryBean();
        ehCacheManagerFactoryBean.setConfigLocation(new ClassPathResource("cache/ehcache.xml"));
        return ehCacheManagerFactoryBean;
    }
}
```



## 使用Redis缓存



## 为方法添加注解以支持缓存

| 注 解       | 注 解 描 述                                                  |
| ----------- | ------------------------------------------------------------ |
| @Cacheable  | 表明Spring在调用方法之前，首先应该在缓存中查找方法的返回值。如果这个值能够找到，就会返回缓存的值。否则的话，这个方法就会被调用，返回值会放到缓存之中 |
| @CachePut   | 表明Spring应该将方法的返回值放到缓存中。在方法的调用前并不会检查缓存，方法始终都会被调用 |
| @CacheEvict | 表明Spring应该在缓存中清除一个或多个条目                     |
| @Caching    | 这是一个分组的注解，能够同时应用多个其他的缓存               |



## 使用XML声明缓存