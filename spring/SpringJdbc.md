# 配置数据源

###### Spring上下文中配置数据源bean的方式：

* 通过JDBC驱动程序定义的数据源；
* 通过JNDI查找的数据源；
* 连接池的数据源

## 使用JNDI数据源

resource-ref属性设置为true，这样给定的jndi-name将会自动添加“java:comp/env/”前缀

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns:jee="http://www.springframework.org/schema/jee" xsi:schemaLocation="http://www.springframework.org/schema/jee
    http://www.springframework.org/schema/aop/spring-jee.xsd">
    <jee:jndi-lookup id="dataSource" jndi-name="/jdbc/SpitterDS" resource-ref="true"/>
</beans>
```

java配置

```java
@Bean
public JndiObjectFactoryBean dataSource() {
    JndiObjectFactoryBean jBean = new JndiObjectFactoryBean();
    jBean.setJndiName("jdbc/SpittrDs");
    jBean.setResourceRef(true);
    jBean.setProxyInterface(DataSource.class);
    return jBean;
}
```

## 使用数据源连接池

```xml
    <bean id="dataSource" class="org.apache.commons.dbcp.basicDataSource" p:driverClassName="org.h2Driver" p:url="jdbc:h2:tcp://localhost/~/spitter" p:username="sa" p:password="" p:initialSize="5" p:maxActive="10"/>
```

java配置

```Java
@Bean
public BasicDataSource dataSource() {
    BasicDataSource ds = new BasicDataSource();
    ds.setDriverClassName("org.h2.Driver");
    ds.setUrl("jdbc:h2:tcp://localhost/~/spitter");
    ds.setUsername("sa");
    ds.setPassword("password");
    ds.setInitialSize(5);
    return ds;
}
```

## 基于JDBC驱动的数据源



* DriverManagerDataSource：在每个连接请求时都会返回一个新建的连接。与DBCP的BasicDataSource不同，由DriverManagerDataSource提供的连接并没有进行池化管理；
* SimpleDriverDataSource：与DriverManagerDataSource的工作方式类似，但是它直接使用JDBC驱动，来解决在特定环境下的类加载问题，这样的环境包括OSGi容器；
* SingleConnectionDataSource：在每个连接请求时都会返回同一个的连接。尽管SingleConnectionDataSource不是严格意义上的连接池数据源，但是你可以将其视为只有一个连接的池。

```
@Bean
public DataSource dataSource() {
    DriverManagerDataSource ds = new DriverManagerDataSource();
    ds.setDriverClassName("org.h2.Driver");
    ds.setUrl("jdbc:h2:tcp://localhost/~/spitter");
    ds.setUsername("sa");
    ds.setPassword("password");
    return ds;
}
```

## 使用JDBC模板

Spring将数据访问的样板代码抽象到模板类之中。Spring为JDBC提供了三个模板类供选择：

* JdbcTemplate：最基本的Spring JDBC模板，这个模板支持简单的JDBC数据库访问功能以及基于索引参数的查询；
* NamedParameterJdbcTemplate：使用该模板类执行查询时可以将值以命名参数的形式绑定到SQL中，而不是使用简单的索引参数；
* SimpleJdbcTemplate：该模板类利用Java 5的一些特性如自动装箱、泛型以及可变参数列表来简化JDBC模板的使用。