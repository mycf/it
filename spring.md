

### bean的作用域

在默认情况下，Spring应用 上下文中所有bean都是作为以单例\(singleton\) 的形式创建的。

也就是说，不管给定的一个bean被注入到其他bean多少次，每次所注入的都是同一个实例。



* 单例\(Singleton\) :在整个应用中，只创建bean的一个实例。

* 原型\(Prototype\) :每次注入或者通过Spring应用上下文获取的时候，都会创建一个新

  的bean实例。

* 会话\(Session\):在Web应用中，为每个会话创建一个bean实例。

* 请求\(Rquest\) :在Web应用中，为每个请求创建一个bean实例。





