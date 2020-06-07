# bean的作用域

在默认情况下，Spring应用 上下文中所有bean都是作为以单例\(singleton\) 的形式创建的。

也就是说，不管给定的一个bean被注入到其他bean多少次，每次所注入的都是同一个实例。

* 单例\(Singleton\) :在整个应用中，只创建bean的一个实例。

* 原型\(Prototype\) :每次注入或者通过Spring应用上下文获取的时候，都会创建一个新

  的bean实例。

* 会话\(Session\):在Web应用中，为每个会话创建一个bean实例。

* 请求\(Rquest\) :在Web应用中，为每个请求创建一个bean实例。

## 面向切面编程 _AOP（Aspect Oriented Programming）

面向切面的编程（AOP）通过提供另一种思考程序结构的方式来补充面向对象的编程（OOP）。 OOP中模块化的关键单元是类，而在AOP中模块化是切面。切面使关注点（例如事务管理）的模块化可以跨越多种类型和对象。 （这种关注在AOP文献中通常被称为“跨领域”关注。）

Spring的关键组件之一是AOP框架。尽管Spring IoC容器不依赖于AOP（这意味着您不需要的话就不需要使用AOP），但AOP是对Spring IoC的补充，以提供功能非常强大的中间件解决方案。

通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。

Spring AOP和AspectJ切入点

Spring提供了简单而强大的方法，使用基于模式的方法或@AspectJ注解样式来编写自定义切面的。这两种样式都提供了全类型的通知，并且使用了AspectJ切入点语言同时仍使用Spring AOP进行织入。

AOP在Spring框架中用于：

- 提供声明式企业服务。最重要的服务是声明式事务管理。
- 让用户实现自定义方面，并用AOP补充其对OOP的使用。



切面：涉及多个类的关注点的模块化。事务管理是企业Java应用程序中横切关注点的一个很好的例子。在Spring AOP中，切面是通过使用普通类（基于xml的方式）或使用`@Aspect`（@AspectJ风格）注解的普通类来实现的。

连接点：在程序执行过程中的一点，例如方法的执行或异常的处理。在Spring AOP中，连接点始终代表方法的执行。

通知：切面在特定的连接点处采取的操作。不同类型的通知包括“around”, “before” 和 “after” 通知。 包括Spring在内的许多AOP框架都将通知建模为拦截器，并在连接点周围维护一系列拦截器。

通知定义了切面是什么以及何时使用。

切入点：与连接点匹配的谓词。通知与切入点表达式关联，并在与该切入点匹配的任何连接点处运行（例如，执行具有特定名称的方法）。切入点表达式匹配的连接点的概念是AOP的核心，默认情况下，Spring使用AspectJ切入点表达语言。

引入：为现有的类声明其他方法或属性。 Spring AOP允许您向任何通知对象引入新的接口（和相应的实现）。例如，您可以使用引入使Bean实现IsModified接口，以简化缓存。 （在AspectJ社区中，引入被称为类型间声明。）

目标对象：一个或多个切面通知的对象。也称为“通知对象”。由于Spring AOP是使用运行时代理实现的，因此该对象始终是代理对象。

AOP代理：由AOP框架创建的一个对象，用于实现切面合同（通知方法执行等）。在Spring 框架中，AOP代理是JDK动态代理或CGLIB代理。

织入：将切面与其他应用程序类型或对象链接以创建通知的对象。这可以在编译时（例如，使用AspectJ编译器），加载时或在运行时完成。像其他纯Java AOP框架一样，Spring AOP在运行时执行织入。

Spring切面有五种类型的通知：

* 前置通知\(Before\) :在目标方法被调用之前调用通知功能;
* 后置通知\(After\) :在目标方法完成之后调用通知，此时不会关心方法的输出是什么;
* 返回通知\( After-returning\) :在目标方法成功执行之后调用通知;
* 异常通知\(After-throwing\) :在目标方法抛出异常后调用通知;
* 环绕通知\(Around\):通知包裹了被通知的方法，在被通知的方法调用之前和调用之后执行自定义的行为。
* 环绕连接点的通知，例如方法调用。这是最有力的通知。环绕通知可以在方法调用之前和之后执行自定义行为。它还负责选择是返回连接点还是通过返回其自身的返回值或引发异常来捷径通知的方法执行。

环绕通知是最综合的通知。由于Spring AOP与AspectJ一样，提供了各种通知类型，因此我们建议您使用功能最弱的通知类型，以实现所需的行为。例如，如果您只需要使用方法的返回值更新缓存，则最好使用返回通知而不是环绕通知，尽管环绕通知可以完成相同的事情。使用最具体的通知类型可提供更简单的编程模型，并减少出错的可能性。例如，您不需要在用于环绕通知的`JoinPoint`上调用`proceed（）`方法，因此，您不会失败。

所有通知参数都是静态类型，以便使用适当类型的通知参数（例如方法执行中返回值的类型），而不是 Object 数组。

切入点匹配连接点的概念是AOP的关键，它与仅提供拦截功能的旧技术有所不同。切入点使通知的目标独立于面向对象的层次结构。例如，您可以将提供声明式事务管理的环绕通知应用于跨越多个对象（例如服务层中的所有业务操作）的一组方法。

### Spring AOP的能力和目标

Spring AOP是用纯Java实现的。不需要特殊的编译过程。Spring AOP不需要控制类加载器的层次结构，因此适合在Servlet容器或应用程序服务器中使用。

Spring AOP当前仅支持方法执行连接点（建议在Spring Bean上执行方法）。尽管可以在不破坏核心Spring AOP API的情况下添加对字段拦截的支持，但并未实现字段拦截。如果需要通知字段访问和更新连接点，请考虑使用诸如AspectJ之类的语言。

Spring AOP的AOP方法不同于大多数其他AOP框架。目的不是提供最完整的AOP实现（尽管Spring AOP相当强大）。相反，其目的是在AOP实现和Spring IoC之间提供紧密的集成，以帮助解决企业应用程序中的常见问题。

因此，例如，通常将Spring Framework的AOP功能与Spring IoC容器结合使用。通过使用常规bean定义语法来配置方面（尽管这允许强大的“自动代理”功能）。这是与其他AOP实现的关键区别。使用Spring AOP不能轻松或高效地完成某些事情，例如建议非常细粒度的对象（通常是域对象）。在这种情况下，AspectJ是最佳选择。但是，我们的经验是，Spring AOP为AOP可以解决的企业Java应用程序中的大多数问题提供了出色的解决方案。

Spring AOP从未努力与AspectJ竞争以提供全面的AOP解决方案。我们认为，基于代理的框架（如Spring AOP）和成熟的框架（如AspectJ）都是有价值的，它们是互补的，而不是竞争。Spring无缝地将Spring AOP和IoC与AspectJ集成在一起，以在基于Spring的一致应用程序架构中支持AOP的所有使用。这种集成不会影响Spring AOP API或AOP Alliance API。Spring AOP仍然向后兼容。

### AOP代理

Spring AOP默认将标准JDK动态代理用于AOP代理。这使得可以代理任何接口（或一组接口）。

Spring AOP也可以使用CGLIB代理。这对于代理类而不是接口是必需的。默认情况下，如果业务对象未实现接口，则使用CGLIB。因为对接口而不是对类进行编程是一种好习惯，业务类通常实现一个或多个业务接口。在那些需要通知在接口上未声明的方法或需要将代理对象作为具体类型传递给方法的情况下（在极少数情况下），可以强制使用CGLIB。

### @AspectJ支持

@AspectJ是一种将切面声明为带有注解的常规Java类的样式。作为 AspectJ 5 版本的一部分，AspectJ 项目引入了@AspectJ样式。Spring 使用 AspectJ 提供的库进行切点切解析和匹配，解析与 AspectJ 5 相同的注解。但是，AOP 运行时仍然是纯 Spring AOP，并且没有依赖 AspectJ 编译器或编织器。

#### 启用@AspectJ支持

要在Spring配置中使用@AspectJ切面，您需要启用Spring支持，基于@AspectJ切面配置Spring AOP，并基于这些切面是否通知自动代理Bean。通过自动代理，我们的意思是，如果Spring确定一个或多个切面通知一个bean，它会自动为该bean生成一个代理来拦截方法调用并确保按需执行通知。

启用@AspectJ支持，需要`aspectjweaver.jar`在应用程序的类路径下面（版本1.8或者更高版本）

Spring使用了AspectJ语法



#### 声明一个切面

`@ Aspect`注解不足以在类路径中进行自动检测`。需要单独声明一个`@Component`注解。

在Spring AOP中，切面本身不能成为其他切面建议的目标。类上的@Aspect注解将其标记为一个方面，因此将其排除在自动代理之外。

#### 声明切入点

切入点确定了感兴趣的连接点，从而使我们能够控制何时执行通知。Spring AOP仅支持Spring Bean的方法执行连接点，因此您可以将切入点视为与Spring Bean上的方法执行匹配。切入点声明由两部分组成：一个包含名称和任何参数的签名，以及一个切入点表达式，该切入点表达式精确确定我们感兴趣的方法执行。在AOP的@AspectJ注解样式中，常规方法定义提供了切入点签名，并通过使用`@Pointcut`注解指出切入点表达式（用作切入点签名的方法必须具有`void`返回类型）。

```java
@Pointcut("execution(* transfer(..))") // 切入点表达式
private void anyOldTransfer() {} // 切入点签名
```

##### 支持的切入点指示符

- `execution`：用于匹配方法执行的连接点。这是使用Spring AOP时要使用的主要切入点指示符。

- `within`：将匹配限制为某些类型内的连接点（使用Spring AOP时，在匹配类型内声明的方法的执行）。

  within与execution相比，粒度更大，仅能实现到包和接口、类级别。而execution可以精确到方法的返回值，参数个数、修饰符、参数类型等

- `this`：限制匹配到连接点（使用Spring AOP时方法的执行）的匹配，其中bean引用（Spring AOP代理）是给定类型的实例。

- `target`：在目标对象（代理的应用程序对象）是给定类型的实例的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。

- `args`：在参数是给定类型的实例的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。

  匹配指定参数类型和指定参数数量的方法，与包名和类名无关

- `@target`：在执行对象的类具有给定类型的注解的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。

- `@args`：限制匹配的连接点（使用Spring AOP时方法的执行），其中传递的实际参数的运行时类型具有给定类型的注解。

- `@within`：将匹配限制为具有给定注释的类型内的连接点（使用Spring AOP时，使用给定注解的类型中声明的方法的执行）。

- `@annotation`：将匹配限制在连接点的主题（Spring AOP中正在执行的方法）具有给定注解的连接点上。



```java
AnnotationConfigApplicationContext configApplicationContext = new AnnotationConfigApplicationContext(AppConfig.class);

Dao dao = (Dao) configApplicationContext.getBean("DaoImpl");
System.out.println(dao instanceof DaoImpl);
System.out.println(dao instanceof Dao);
System.out.println(dao instanceof Proxy);
```

打印出

```java
false
true
true
```



```java
static void generatorClass(){
    Class[] classes = new Class[]{Dao.class};
    byte[] bytes = ProxyGenerator.generateProxyClass("Yu", classes);
    try {
        File file = new File("Yu.class");
        FileOutputStream fos = new FileOutputStream(file);
        fos.write(bytes);
        fos.flush();
        fos.close();
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```



#### 通知（Advice）

切面的工作被称为通知

* 

### 连接点（Join point）

这些时机被称为连接点连接点是在应用执行过程中能够插入切面的一个点。这个点可以是调用方法时、抛出异常时、甚至修改一个字段时。切面代码可以利用这些点插入到应用的正常流程之中，并添加新的行为。

### 切点（Poincut）

一个切面并不需要通知应用的所有连接点。切点有助于缩小切面所通知的连接点的范围。

如果说通知定义了切面的“什么”和“何时”的话，那么切点就定义了“何处”。切点的定义会匹配通知所要织入的一个或多个连接点。我们通常使用明确的类和方法名称，或是利用正则表达式定义所匹配的类和方法名称来指定这些切点。有些AOP框架允许我们创建动态的切点，可以根据运行时的决策（比如方法的参数值）来决定是否应用通知。

### 切面（Aspect）

切面是通知和切点的结合。通知和切点共同定义了切面的全部内容——它是什么，在何时和何处完成其功能。

### 引入（Introduction）

引入允许我们向现有的类添加新方法或属性。例如，我们可以创建一个Auditable通知类，该类记录了对象最后一次修改时的状态。这很简单，只需一个方法，setLastModified\(Date\)，和一个实例变量来保存这个状态。然后，这个新方法和实例变量就可以被引入到现有的类中，从而可以在无需修改这些现有的类的情况下，让它们具有新的行为和状态。

## 织入（Weaving）

织入是把切面应用到目标对象并创建新的代理对象的过程。切面在指定的连接点被织入到目标对象中。在目标对象的生命周期里有多个点可以进行织入：

编译期：切面在目标类编译时被织入。这种方式需要特殊的编译器。AspectJ的织入编译器就是以这种方式织入切面的。

类加载期：切面在目标类加载到JVM时被织入。这种方式需要特殊的类加载器（ClassLoader），它可以在目标类被引入应用之前增强该目标类的字节码。AspectJ5的加载时织入（load-time weaving，LTW）就支持以这种方式织入切面。

运行期：切面在应用运行的某个时刻被织入。一般情况下，在织入切面时，AOP容器会为目标对象动态地创建一个代理对象。Spring AOP就是以这种方式织入切面的。

### Spring提供了4种类型的AOP支持：

* 基于代理的经典Spring AOP；

* 纯POJO切面；

* @AspectJ注解驱动的切面；

* 注入式AspectJ切面（适用于Spring各版本）。

#### Spring在运行时通知对象

通过在代理类中包裏切面，Spring在运行期把切面织入到Spring管理的bean中。代理类封装了目标类，并拦截被通知方法的调用，再把调用转发给真正的目标bean。当代理拦截到方法调用时，在调用目标bean方法之前，会执行切面逻辑。

Spring的切面 由包裹了目标对象的代理类实现。

代理类处理方法的调用，执行额外的切面逻辑，并调用目标方法

直到应用需要被代理的bean时，Spring才 创建代理对象。如果使用的是ApplicationContext的话，在ApplicationContext从BeanFactory中加载所有bean的时候，Spring才会创建被代理的对象。因为Spring运行时才创建代理对象，所以我们不需要特殊的编译器来织入SpringAOP的切面。



@Autowired



@Qualifier



@Primary

### Spring事件

![image-20200601081111255](https://raw.githubusercontent.com/mycf/it/master/assets/image-20200601081111255.png)

### WebSocket

WebSocket消息包括原始WebSocket交互，通过SockJS进行WebSocket仿真以及通过STOMP作为WebSocket的子协议进行发布-订阅消息。

是一种协议 基于http协议 使用websokcet 集成spring和stomp技术 规范了socket传输的内容 让我们的webscoket实现了发布订阅的模式

html5的新特性 需要浏览器和服务端（web容器支持tomcat和jetty）

/topic 不通过应用程序 直接tomcat容器

WebSocket协议RFC 6455提供了一种标准化方法，可通过单个TCP连接在客户端和服务器之间建立全双工双向通信通道。它是与HTTP不同的TCP协议，但在HTTP上工作，使用端口80和443并允许重复使用现有的防火墙规则。

WebSocket交互始于一个HTTP请求，该请求使用HTTP `Upgrade`header进行升级`，在这种情况下切换到WebSocket协议。以下示例显示了这种交互：



对于内置的简单代理，`/topic`和`/queue`前缀没有任何特殊含义。它们仅是区分发布订阅消息传递和点对点消息传递的约定（即，许多订阅者与一个消费者）。使用外部代理时，请检查代理的STOMP页面以了解其支持哪种STOMP的目标和前缀。

### STOMP

WebSocket协议定义了两种消息类型（文本消息和二进制消息），但是其内容未定义。该协议定义了一种机制，供客户端和服务器协商用于在WebSocket上使用的子协议（即高级消息协议），用于定义每种协议可以发送的消息类型，每个消息的内容格式，等等。子协议的使用是可选的，但无论哪种方式，客户端和服务器都需要就定义消息内容的某种协议达成共识。

STOMP（面向简单文本的消息传递协议）最初是为脚本语言（例如Ruby，Python和Perl）创建的，以连接到企业消息代理。它旨在解决常用消息传递模式的最小子集。 STOMP可以在任何可靠的双向流网络协议上使用，例如TCP和WebSocket。尽管STOMP是面向文本的协议，但是消息有效负载可以是文本或二进制。

STOMP是基于帧的协议，其帧以HTTP为模型。

与使用原始WebSocket相比，使用STOMP作为子协议可以使Spring Framework和Spring Security提供更丰富的编程模型。

客户端可以使用`SEND`或`SUBSCRIBE`命令发送或订阅消息，以及描述消息的内容和接收者的`destination`头。这启用了一种简单的发布-订阅机制，您可以使用该机制通过代理将消息发送到其他连接的客户端，或者将消息发送到服务器以请求执行某些工作。



在STOMP规范中，目的地的含义是故意不透明的。它可以是任何字符串，并且完全由STOMP服务器定义它们所支持的目的地的语义和语法。但是，目的地通常是类似路径的字符串。

STOMP服务器可以使用MESSAGE命令向所有订阅者广播消息。

服务器无法发送未经请求的消息。来自服务器的所有消息都必须响应特定的客户端订阅，并且服务器消息的`subscription-id`header必须与客户端订阅的`id`header匹配。



使用Spring的STOMP支持时，Spring WebSocket应用程序将充当客户端的STOMP代理。消息被路由到`@Controller`消息处理方法或简单的内存代理，该代理跟踪订阅并向订阅的用户广播消息。您还可以配置Spring与专用的STOMP代理（例如RabbitMQ，ActiveMQ等）一起使用，以实际广播消息。在那种情况下，Spring维护与代理的TCP连接，将消息中继到该代理，并将消息从该代理向下传递到已连接的WebSocket客户端。因此，Spring Web应用程序可以依靠基于HTTP的统一安全性，通用验证以及用于消息处理的常用编程模型。

- 无需发明自定义消息协议和消息格式。


- 可以使用STOMP客户端，包括Spring框架中的Java客户端。


- 您可以（可选）使用消息代理（例如RabbitMQ，ActiveMQ和其他代理）来管理订阅和广播消息。


- 可以在任意数量的`@Controller`实例中组织应用程序逻辑，并且可以基于STOMP destinations header将消息路由到它们，而不是通过给定连接使用单个WebSocketHandler处理原始WebSocket消息。


- 您可以使用Spring Security基于STOMP destinations和消息类型来保护消息。