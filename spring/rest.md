

###### Spring提供了两种方法将资源的Java表述形式转换为发送给客户端的表述形式：

* 内容协商（Content negotiation）：选择一个视图，它能够将模型渲染为呈现给客户端的表述形式；
* 消息转换器（Message conversion）：通过一个消息转换器将控制器所返回的对象转换为呈现给客户端的表述形式。

###### ContentNegotiationManager

* 指定默认的内容类型，如果根据请求无法得到内容类型的话，将会使用默认值；
* 通过请求参数指定内容类型；
* 忽视请求的Accept头部信息；
* 将请求的扩展名映射为特定的媒体类型；

* 将JAF（Java Activation Framework）作为根据扩展名查找媒体类型的备用方案。



###### 三种配置ContentNegotiationManager的方法：

* 直接声明一个ContentNegotiationManager类型的bean；
* 通过ContentNegotiationManagerFactoryBean间接创建bean；
* 重载WebMvcConfigurerAdapter的configureContentNegotiation()方法。



###### Spring提供了多个HTTP信息转换器，用于实现资源表述与各种Java类型之间的互相转换

| 信息转换器                           | 描 述                                                        |
| ------------------------------------ | ------------------------------------------------------------ |
| AtomFeedHttpMessageConverter         | Rome Feed对象和Atom feed（媒体类型application/atom+xml）之间的互相转换。<br />如果 Rome 包在类路径下将会进行注册 |
| BufferedImageHttpMessageConverter    | BufferedImages与图片二进制数据之间互相转换                   |
| ByteArrayHttpMessageConverter        | 读取/写入字节数组。从所有媒体类型（*/*）中读取，并以application/octet-stream格式写入 |
| FormHttpMessageConverter             | 将application/x-www-form-urlencoded内容读入到MultiValueMap<String,String>中，也会将MultiValueMap<String,String>写入到application/x-www-form￾urlencoded中或将MultiValueMap<String, Object>写入到multipart/form-data中 |
| Jaxb2RootElementHttpMessageConverter | 在XML（text/xml或application/xml）和使用JAXB2注解的对象间互相读取和写入。<br/>如果 JAXB v2 库在类路径下，将进行注册 |
| MappingJacksonHttpMessageConverter   | 在JSON和类型化的对象或非类型化的HashMap间互相读取和写入。<br/>如果 Jackson JSON 库在类路径下，将进行注册 |
| MappingJackson2HttpMessageConverter  | 在JSON和类型化的对象或非类型化的HashMap间互相读取和写入。<br/>如果 Jackson 2 JSON 库在类路径下，将进行注册 |
| MarshallingHttpMessageConverter      | 使用注入的编排器和解排器（marshaller和unmarshaller）来读入和写入XML。支持的编排器和解排器包括Castor、JAXB2、JIBX、XMLBeans以及Xstream |
| ResourceHttpMessageConverter         | 读取或写入Resource                                           |
| RssChannelHttpMessageConverter       | 在RSS feed和Rome Channel对象间互相读取或写入。<br/>如果 Rome 库在类路径下，将进行注册 |
| SourceHttpMessageConverter           | 在XML和javax.xml.transform.Source对象间互相读取和写入。<br/>默认注册 |
| StringHttpMessageConverter           | 将所有媒体类型（*/*）读取为String。将String写入为text/plain  |
| XmlAwareFormHttpMessageConverter     | FormHttpMessageConverter的扩展，使用SourceHttp MessageConverter<br/>来支持基于XML的部分 |

 

