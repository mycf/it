

### static(默认定位)

static 遵循默认的文档流布局，top、left、right、bottom属性都无效

### relative(相对定位)

> relative 先遵循默认的文档流布局也就是 static 布局，然后再在不改变页面布局的前提下根据 left、right、top、bottom 调整此元素的位置。
>
> 也就是 left、right、top、bottom 的调整都是 相对于当前元素 static 布局位置进行的调整。
>
> relative 也被称为 **相对定位**

### absolute(绝对定位)

> absolute（绝对定位） 和 relation（相对定位）的区别，relation 是相对自己进行 top、left、right、bottom 进行偏移，而 absolute 是寻找最近的 非 static 的祖先节点进行偏移。

### fixed(固定定位)

> fixed  为 **固定定位**
>
> 固定定位和绝对定位类似，但元素的包含块为屏幕视口（viewport）
>
> 固定定位不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。

> 1. 默认非 static 元素的 z-index 都为 0
> 2. z-index 越大，则越在最上面，离观察者越近
> 3. 同样的 z-index， 在 HTML 中的元素越靠后，则越在最上面，离观察者越近



### sticky