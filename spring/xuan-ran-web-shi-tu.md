| 视图解析器 | 描 述 |
| :---: | :---: |
| BeanNameViewResolver | 将视图解析为Spring应用上下文中的bean，其中bean的ID与视图的名字相同 |
| ContentNegotiatingViewResolver |  |

通过考虑客户端需要的内容类型来解析视图，委托给另外一个能够产生对应内容类型的视图解析器

