

## DispatcherServlet

`WebApplicationContext`（纯`ApplicationContext`的扩展）为其自身的配置。 `WebApplicationContext`具有指向`ServletContext`和与其关联的Servlet的链接。它还绑定到ServletContext，以便应用程序可以在`RequestContextUtils`上使用静态方法来查找`WebApplicationContext`（如果需要访问它们）。

对于许多应用程序而言，拥有一个`WebApplicationContext`很简单并且足够。也可能具有上下文层次结构，其中一个根`WebApplicationContext`在多个`DispatcherServlet`（或其他Servlet）实例之间共享，每个实例都有其自己的子`WebApplicationContext`配置。

根`WebApplicationContext`通常包含需要在多个Servlet实例之间共享的基础结构Bean，例如数据存储库和业务服务。这些Bean是有效继承的，并且可以在Servlet特定的子`WebApplicationContext`中重写（即重新声明），该子`WebApplicationContext`通常包含给定Servlet本地的Bean。下图显示了这种关系：

![mvc context hierarchy](https://raw.githubusercontent.com/mycf/it/master/assets/mvc-context-hierarchy.png)

如果不需要应用程序上下文层次结构，则应用程序可以通过getRootConfigClasses（）返回所有配置，并从getServletConfigClasses（）返回null。



### 特殊bean类型

DispatcherServlet委托给特殊的Bean处理请求并呈现适当的响应。所谓“特殊bean”，是指实现框架协定的Spring管理对象实例。这些通常带有内置协定，但是您可以自定义它们的属性并扩展或替换它们。

| HandlerMapping                        | 将请求与拦截器列表一起映射到处理程序，以进行预处理和后置处理。映射基于某些条件，其细节因HandlerMapping实现而异。<br />HandlerMapping的两个主要实现是RequestMappingHandlerMapping（支持@RequestMapping带注释的方法）和SimpleUrlHandlerMapping（维护对处理程序的URI路径模式的显式注册）。 |
| ------------------------------------- | ------------------------------------------------------------ |
| HandlerAdapter                        | 帮助DispatcherServlet调用映射到请求的处理程序，而不管实际如何调用该处理程序。例如，调用带注解的控制器需要解析注解。 HandlerAdapter的主要目的是使DispatcherServlet免受此类细节的影响。 |
| HandlerExceptionResolver              | 解决异常的策略，可能将它们映射到处理程序，HTML错误视图或其他目标。 |
| ViewResolver                          | 解析从处理程序返回的实际基于字符串的基于逻辑的视图名称，以实际的视图呈现给响应。 |
| LocaleResolver, LocaleContextResolver | 解析客户正在使用的语言环境以及可能的时区，以便能够提供国际化的视图。 |
| ThemeResolver                         | 解决Web应用程序可以使用的主题，例如，以提供个性化的布局。    |
| MultipartResolver                     | 借助一些multipart解析库来解析multipart请求的抽象化（例如，浏览器表单文件上传）。 |
| FlashMapManager                       | 存储和检索“输入”和“输出” FlashMap，可用于将属性从一个请求传递到另一个请求，通常跨重定向。 |

### Web MVC 配置

应用程序可以声明处理请求所需的[特殊Bean类型](#特殊bean类型)中列出的基础结构Bean。 `DispatcherServlet`检查每个特殊bean的`WebApplicationContext`。如果没有匹配的bean类型，它将使用`DispatcherServlet.properties`中列出的默认类型。

在大多数情况下，MVC Config是最佳起点。它使用Java或XML声明所需的bean，并提供了更高级别的配置回调API来对其进行自定义。

####  Servlet 配置

在Servlet 3.0+环境中，您可以选择以编程方式配置Servlet容器

`WebApplicationInitializer`是Spring MVC提供的接口，可确保检测到您的实现并将其自动用于初始化任何Servlet 3容器。 `WebApplicationInitializer`的抽象基类实现名为`AbstractDispatcherServletInitializer`，它通过覆盖指定Servlet映射和`DispatcherServlet`配置位置的方法，使注册`DispatcherServlet`更容易。

`AbstractDispatcherServletInitializer`提供了xml的配置（**createRootApplicationContext**和**createServletApplicationContext**方法），还可以添加`Filter`实例（getServletFilters）

每个过滤器都会根据其具体类型添加一个默认名称，并自动映射到`DispatcherServlet`。

`AbstractDispatcherServletInitializer`的`isAsyncSupported` protected方法提供了一个位置，以在`DispatcherServlet`及其映射的所有过滤器上启用异步支持。默认情况下，此标志设置为true。

最后，如果您需要进一步自定义`DispatcherServlet`本身，则可以覆盖`createDispatcherServlet`方法。

### 流程

### 面向切面

通知（**Advice**） 

切面的工作被称为通知。通知定义了切面是什么以及何时使用。除了描述切面要完成的工作，通知还解决了何时执行这个工作的问题。

Spring切面可以应用5种类型的通知： 

前置通知（Before）：在目标方法被调用之前调用通知功能； 

后置通知（After）：在目标方法完成之后调用通知，此时不会关心方法的输出是什么； 

返回通知（After-returning）：在目标方法成功执行之后调用通知； 

异常通知（After-throwing）：在目标方法抛出异常后调用通知； 

环绕通知（Around）：通知包裹了被通知的方法，在被通知的方法调用之前和调用之后执行自定义的行为。

连接点（**Join point**） 

连接点是在应用执行过程中能够插入切面的一个点。这个点可以是调用方法时、抛出异常时、甚至修改一个字段时。切面代码可以利用这些点插入到应用的正常流程之中，并添加新的行为。

切点（**Poincut**） 

切点的定义会匹配通知所要织入的一个或多个连接点。我们通常使用明确的类和方法名称，或是利用正则表达式定义所匹配的类和方法名称来指定这些切点。

### 事务

#### 事务参数

声明式事务通过传播行为、隔离级别、只读提示、超时间隔和回滚规则来定义

##### 传播行为

传播行为定义关于客户端和被调用方法的事务边界。

![image-20200518191709160](../../../../../Library/Application Support/typora-user-images/image-20200518191709160.png)

###### @Transactional失效场景

- @Transactional 应用在非 public 修饰的方法上
- @Transactional 注解属性 propagation 设置错误
- @Transactional 注解属性 rollbackFor 设置错误
- 同一个类中方法调用，导致@Transactional失效
- try/catch导致@Transactional失效

##### 隔离级别

- 脏读（Dirty read）——脏读发生在一个事务读取了被另一个事务改写但尚未提交的数据时。如果这些改变在稍后被回滚了，那么第一个事务读取的数据就会是无效的。
- 不可重复读（Nonrepeatable read）——不可重复读发生在一个事务执行相同的查询两次或两次以上，但每一次查询结果都不同时。这通常是由于另一个并发事务在两次查询之间更新了数据。
- 幻读（Phantom reads）——幻读和不可重复读相似。当一个事务（T1）读取几行记录后，另一个并发事务（T2）插入了一些记录时，幻读就发生了。在后来的查询中，第一个事务（T1）就会发现有一些原来没有的额外记录。

###### 只读

如果一个事务只对后端数据库执行读操作，那么该数据库就可能可以利用那个事务的只读特性，采取某些优化措施。

###### 事务超时

假设你的事务的运行时间变得格外的长。因为事务可能涉及对后端数据库的锁定，所以长时间运行的事务会不必要地占用数据库资源。你可以声明一个事务，在特定秒数之后自动回滚，而不必等它自己结束。

###### 回滚规则

在默认设置下，事务只在出现运行异常（runtime exception）时回滚，而在出现受阻异常（checked exception）时不回滚（这一行为和EJB中的回滚行为是一致的）。

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