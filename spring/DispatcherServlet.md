

### 处理请求的过程：

1. 搜索`WebApplicationContext`并绑定到request上，这样，控制器和request流程中的其他元素都能使用（默认`XmlWebApplicationContext`）
2. 绑定语言环境解析器，以使request流程中的元素知道语言环境去解析（渲染视图，准备数据等等）
3. 绑定主题解析器以使视图决定主题使用
4. 如果指定了多文件解析器，检查request是否是多文本。如果是多文本，request被包装成`MultipartHttpServletRequest`为流程中的其他元素进一步处理
5. 查找合适的处理器handler，如果找到，将执行和处理器（预处理器、后置处理器，控制器controllers）有关联的执行链。你也可以选择带注解的控制器controllers，渲染响应（在`HandlerAdapter`中）代替返回一个视图
6. 如果返回模型model，渲染视图。如果没有返回（可能因为request被预处理器或者后置处理程序器，也可能出于安全因素），不会有视图渲染，因为request已经完成

`HandlerExceptionResolver`异常解析器被声明在`WebApplicationContext`中，用于解析请求过程中的异常。允许自定义的异常处理器

你可以通过添加Servlet初始化参数`init-param`在`web.xml`中声明Servlet来自定义`DispatcherServlet`实例

### 拦截器

所有的`HandlerMapping`实现支持处理拦截器，需要实现`HandlerInterceptor`

- `preHandle(..)`: 在真正的处理器前执行
- `postHandle(..)`:在处理器后执行
- `afterCompletion(..)`: 完整的请求完成后

`preHandle(..)`方法返回boolean值，可以用来中断request过程中的执行链。当返回`true`,处理器执行链继续。当返回`false`的时候，`DispatcherServlet`假定拦截器已经处理好request（例如，渲染了合适的视图）和不在继续执行执行链中的其他拦截器和真正的处理器

注意⚠️：`@ResponseBody` and `ResponseEntity`方法的响应提交在`HandlerAdapter` 之前and  `postHandle`之后，`postHandle`用处不大。这意味着改变response已晚。对这种情况，我们可以实现`ResponseBodyAdvice`也可以声明`@ControllerAdvice` controllers bean，或者直接配置`RequestMappingHandlerAdapter`

### 异常

如果异常发生在请求映射或者请求处理（例如`@Controller`）期间.`DispatcherServlet`委托`HandlerExceptionResolver`beans链解决异常并且提供可选择的处理。通常一个错误的响应



