数组边界检查和空指针检查的注释选项

本文如何使用Soot注释选项将数组边界检查和空指针检查属性添加到类文件中，以及如何在JIT或ahead-of-time编译器中使用这些属性。

Java需要在访问数组时检查数组边界，以及在访问对象时检查null指针。
数组边界检查是在虚拟机级别通过在访问数组元素之前插入比较指令(comparison instructions)来实现的。
当字节码访问空指针时，大多数操作系统都会引发硬件异常，因此，在大多数情况下，对对象引用的无效检查是自选(free)的。
但是，某些字节码，例如```invokespecial```和```athrow```指令，确实需要显式比较指令才能检测空指针。这两种安全检查机制会导致大量的运行时开销。

Soot提供了用于检测安全数组和对象访问的静态分析方法。这些分析将数组和对象引用字节码标记为安全或不安全。
这些分析的结果作为属性编码到类文件中，然后可以由解释器或JIT编译器理解。
如果字节码在其属性中被标记为安全，则可以消除相关的比较指令。
这样可以加快Java应用程序的执行速度。我们使用属性对类文件进行编码的过程称为```annotation```。

Soot可用作编译器框架，以支持您要定义的任何属性；然后可以将它们编码为类文件。[通过Soot将属性添加到类文件](https://github.com/Sable/soot/wiki/Adding-attributes-to-class-files-%28Basic%29)中记录了添加新的分析和属性的过程。

## Soot中的注释选项
### 选项的描述
## 命令行例子
## 使用虚拟机中的属性
