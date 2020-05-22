### @EnableAutoConfiguration Annotation

告诉Spring Boot根据添加的`dependencies`配置Spring

我们应用程序的最后一部分是主要方法。这只是遵循Java约定的应用程序入口点的标准方法。我们的主要方法通过调用run委托给Spring Boot的SpringApplication类。 SpringApplication会引导我们的应用程序，并启动Spring，后者反过来又会启动自动配置的Tomcat Web服务器。我们需要将Example.class作为参数传递给run方法，以告诉SpringApplication哪个是主要的Spring组件。 args数组也通过传递以公开任何命令行参数。

### 创建可执行jar

需要添加`spring-boot-maven-plugin`到`pom.xml`（在`dependencies`下面）

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

spring-boot-starter-parent的POM包含配置以绑定重新打包目标。如果不使用父POM，则需要自己声明此配置。

打包`mvn package`

查看jar包文件

```bash
➞  jar tvf target/myproject-0.0.1-SNAPSHOT.jar
```

使用`java -jar`启动应用

```bash
➞  java -jar target/myproject-0.0.1-SNAPSHOT.jar

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v2.2.7.RELEASE)
....... . . .
....... . . . (log output here)
....... . . .
........ Started Example in 2.536 seconds (JVM running for 2.864)
```

如果没添加`spring-boot-maven-plugin`

```bash
➞  java -jar target/myproject-0.0.1-SNAPSHOT.jar                                                                                                                                                           
target/myproject-0.0.1-SNAPSHOT.jar中没有主清单属性
```

### FailureAnalyzer

FailureAnalyzer是一种很好的方式，可以在启动时拦截异常并将其转换为易于阅读的消息，并包装在FailureAnalysis中。 Spring Boot为与应用程序上下文相关的异常，JSR-303验证等提供了此类分析器。您也可以创建自己的。

AbstractFailureAnalyzer是FailureAnalyzer的便捷扩展，它检查要处理的异常中是否存在指定的异常类型。您可以对此进行扩展，以便您的实现只有在异常出现时才有机会处理该异常。如果由于某种原因无法处理该异常，请返回null，以使另一个实现有机会处理该异常。

`FailureAnalyzer`实现必须注册到`META-INF/spring.factories`

在任何Spring Boot ApplicationContext中都有一个非常有用的ConditionEvaluationReport。如果启用DEBUG日志记录输出，则可以看到它。如果您使用spring-boot-actuator（请参阅“执行器”一章），则还有一个`conditions`终结点以JSON形式呈现报告。使用该端点来调试应用程序，并在运行时查看Spring Boot添加了哪些功能（哪些尚未添加）。

### 自动配置故障

### 在启动前自定义环境和ApplicationContext

`SpringApplication`具有`ApplicationListeners`和`ApplicationContextInitializers`,用来将自定义项应用于上下文和环境

- 在运行前，每个应用

### @SpringBootApplication

### @EnableAutoConfiguration

### @ComponentScan

建议使用java配置的方式，把定义main方法的类作为主要的`@Configuration`

### @ImportResource

建议使用`@ImportResource`加载xml配置文件

Spring Boot自动配置尝试根据jar依赖自动配置Spring应用

可以`@Configuration`文件中使用`@EnableAutoConfiguration`和`@SpringBootApplication`之一加载自动配置

使用`@SpringBootApplication`的exclude属性禁用不用的配置类

应用程序类在根包下，`@ComponentScan`可以不设置任何参数，（`@Component`, `@Service`, `@Repository`, `@Controller`）所有的组件将被注册到Spring beans中

使用构造器注入时，可以省略`@Autowired`



