在《Java虚拟机规范》的规定里，除了程序计数器外，虚拟机内存的其他几个运行时区域都有发生OutOfMemoryError（下文称OOM）异常的可能。

### Java堆溢出

Java堆用于储存对象实例，我们只要不断地创建对象，并且保证GC Roots到对象之间有可达路径来避免垃圾回收机制清除这些对象，那么随着对象数量的增加，总容量触及最大堆的容量限制后就会产生内存溢出异常。

```java
package com.ycf.jvm;

import java.util.ArrayList;
import java.util.List;

/**
 * VM args: -Xms1m -Xmx1m -XX:+HeapDumpOnOutOfMemoryError
 * HeadOOM
 */
public class HeadOOM {

    static class OOMObject {

    }
    
    public static void main(String[] args) {
        List<OOMObject> list = new ArrayList<OOMObject>();
        while (true) {
            
            list.add(new OOMObject());
        }
    }
}
```

处理方法：

1. 常规的处理方法是首先通过	（如Eclipse Memory Analyzer）对Dump出来的堆转储快照进行分析。第一步首先应确认内存中导致OOM的对象是否是必要的，也就是要先分清楚到底是出现了内存泄漏（Memory Leak）还是内存溢出（MemoryOverflow）。图2-5显示了使用Eclipse Memory Analyzer打开的堆转储快照文件。

