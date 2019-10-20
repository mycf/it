

| 视图解析器                     | 描 述                                                        |
| :----------------------------- | :----------------------------------------------------------- |
| BeanNameViewResolver           | 将视图解析为Spring应用上下文中的bean，其中bean的ID与视图的名字相同 |
| ContentNegotiatingViewResolver | 通过考虑客户端需要的内容类型来解析视图，委托给另外一个能够产生对应内容类型的视图解析器 |
| FreeMarkerViewResolver         | 将视图解析为FreeMarker                                       |
| InternalResourceViewResolver   | 将视图解析为Web应用的内部资源（一般为JSP）                   |
| JasperReportsViewResolver      | 将视图解析为JasperReports定义                                |
| ResourceBundleViewResolver     | 将视图解析为资源bundle（一般为属性文件）                     |
| TilesViewResolver              | 将视图解析为Apache Tile定义，其中tile ID与视图名称相同。注意有两个不同的TilesViewResolver实现，分别对应于Tiles 2.0和Tiles 3.0 |
| UrlBasedViewResolver           | 直接根据视图的名称解析视图，视图的名称会匹配一个物理视图的定义 |
| VelocityLayoutViewResolver     | 将视图解析为Velocity布局，从不同的Velocity模板中组合页面     |
| VelocityViewResolver           | 将视图解析为Velocity模板                                     |
| XmlViewResolver                | 将视图解析为特定XML文件中的bean定义。类似于BeanNameViewResolver |
| XsltViewResolver               | 将视图解析为XSLT转换后的结果                                 |



#### 处理multipart形式的数据

##### 1.配置multipart解析器

委托给了MultipartResolver策略接口的实现，Spring3.1开始内置了两个MultipartResolver的实现

* CommonsMultipartResolver：使用Jakarta Commons FileUpload解析multipart请求：
* StandardServletMultipartResolver：依赖于Servlet 3.0对multipart请求的支持
  （始于Spring 3.1）。

配置multipart的具体参数（MultipartConfigElement）

* 临时目录

* 上传文件的最大容量（以字节为单位）。默认是没有限制的。
* 整个multipart请求的最大容量（以字节为单位），不会关心有多少个part以及每个part的大小。默认是没有限制的。
* 在上传的过程中，如果文件大小达到了一个指定最大容量（以字节为单位），将会写入到临时文件路径中。默认值为0，也就是所有上传的文件都会写入到磁盘。



```java
		/**
     * 配置DispatcherServlet的Servlet初始化类继承了AbstractAnnotationConfigDispatcherServletInitializer或AbstractDispatcherServletInitializer
     * 实现customizeRegistration方法
     */
    @Override
    protected void customizeRegistration(Dynamic registration) {
        registration.setMultipartConfig(new MultipartConfigElement("/tmp/spittr/uploads"));
    }
```



```java
		/**
     * 默认临时文件路径为Servlet容器的临时目录
     */
    @bean
    public MultipartResolver multipartResolver() {
        CommonsMultipartResolver multipartResolver = new CommonsMultipartResolver();
        multipartResolver.setUploadTempDir(new FileSystemResource("/tmp/spittr/uploads"));
        return multipartResolver;
    }
```

