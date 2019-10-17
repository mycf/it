| 视图解析器 | 描 述 |
| :--- | :--- |
| BeanNameViewResolver | 将视图解析为Spring应用上下文中的bean，其中bean的ID与视图的名字相同 |
| ContentNegotiatingViewResolver | 通过考虑客户端需要的内容类型来解析视图，委托给另外一个能够产生对应内容类型的视图解析器 |
| FreeMarkerViewResolver | 将视图解析为FreeMarker |
| InternalResourceViewResolver | 将视图解析为Web应用的内部资源（一般为JSP） |
| JasperReportsViewResolver | 将视图解析为JasperReports定义 |
| ResourceBundleViewResolver | 将视图解析为资源bundle（一般为属性文件） |
| TilesViewResolver | 将视图解析为Apache Tile定义，其中tile ID与视图名称相同。注意有两个不同的TilesViewResolver实现，分别对应于Tiles 2.0和Tiles 3.0 |
| UrlBasedViewResolver  |  |



