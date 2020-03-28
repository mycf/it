

### 过滤Web请求

通过web.xml还是通过AbstractSecurityWebApplicationInitializer的子类来配置DelegatingFilterProxy，它都会拦截发往应用中的请求，并将请求委托给ID为springSecurityFilterChain bean。

借助WebApplicationInitializer以Java的方式来配置DelegatingFilterProxy

```java
/**
 * SecurityWebInitializer
 * AbstractSecurityWebApplicationInitializer实现了WebApplicationInitializer，因此Spring会发现它，并用它在Web容器中注册DelegatingFilterProxy。
 */
public class SecurityWebInitializer extends AbstractSecurityWebApplicationInitializer {

}
```

