## 声明Hibernate的Session工厂

###### 使用Hibernate 3.2或更高版本（直到Hibernate 4.0，但不包含这个版本）并且使用XML定义映射

```Java
@Bean
public LocalSessionFactoryBean sessionFactory(DataSource dataSource) {
    LocalSessionFactoryBean sFactoryBean = new LocalSessionFactoryBean();
    sFactoryBean.setDataSource(dataSource);
    sFactoryBean.setMappingResources(new String[] {
        "spittle.hbm.xml"
    });
    Properties properties = new Properties();
    properties.setProperty("dialect", "org.hibernate.dialect.H2Dialect")
    sFactoryBean.setHibernateProperties(properites);
    return sFactoryBean;
}
```

###### 注解的方式





