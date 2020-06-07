lambda表达式就是一个代码块，以及必须传入代码的变量规范。

如果代码要完成的计算无法放在一个表达式中，就可以像写方法一样，把这些代码放在{}中，并包含显式的return语句。

```java
Arrays.sort(a, (String first, String second) -> {
    return first.length() - second.length();
});
```

即使lambda表达式没有参数，仍然要提供空括号，就像无参数方法一样：

```
Arrays.sort(a, (first, second) -> first.length() - second.length());
```

如果可以推导出一个lambda表达式的参数类型，则可以忽略其类型。

#### 自定义注解

```java
package com.yu.annotation;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE, ElementType.FIELD})
public @interface Auth {
    String value() default "";
}

```

`value`属性添加了默认值，使用注解的时候可以不用`value`指明例如：

```java
@Auth("yu")
```

- `RetentionPolicy`注解保留策略和元注解`Retention`一起使用
- `ElementType`和元注解`Target`一起使用，以指定在什么情况下使用注释类型是合法的。

#### 获取注解对象

```java
public static void getDeclaredAnnotation(IndexDao dao) {
    Class clazz = dao.getClass();
		// 判断是否包含注解Auth
    if (clazz.isAnnotationPresent(Auth.class)) {
      	// 获取注解对象
        Auth a = (Auth) clazz.getDeclaredAnnotation(Auth.class);
    }
}
```