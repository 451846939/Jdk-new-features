# JVM

## 一. java体系

这里使用了java8文档中的一副图，也是最能表示java技术体系的一张图

> https://docs.oracle.com/javase/8/docs/

![1569144144865](E:\codes\ideaworkspace\Jdk-new-features\Jdk-new-features\imges\1569144144865.png)

## 二.JVM（13）

![1569151104302](E:\codes\ideaworkspace\Jdk-new-features\Jdk-new-features\imges\1569151104302.png)

> https://docs.oracle.com/javase/specs/jvms/se13/html/index.html
>
> https://docs.oracle.com/en/java/javase/13/vm/java-virtual-machine-technology-overview.html

### 1.Java虚拟机技术概述

> https://docs.oracle.com/en/java/javase/13/vm/java-virtual-machine-technology-overview.html#GUID-982B244A-9B01-479A-8651-CB6475019281

- **自适应编译器**：标准解释器用于启动应用程序。当应用程序运行时，将对代码进行分析以检测性能瓶颈或*热点*。Java HotSpot VM编译代码的性能关键部分以提高性能，但不编译很少使用的代码（大多数应用程序）。Java HotSpot VM使用自适应编译器来决定如何使用内联之类的技术来优化已编译的代码。
- **快速的内存分配和垃圾回收**：Java HotSpot技术为对象和快速，高效，最新的垃圾回收器提供了快速的内存分配。
- **线程同步**：Java HotSpot技术提供了一种线程处理功能，该功能旨在扩展用于大型共享内存多处理器服务器。

在Oracle Java Runtime Environment（JRE）8和更早版本中，对于通常用作客户端，服务器和嵌入式系统的配置，支持JVM的不同实现（客户端VM，服务器VM和最小VM）。由于现在大多数系统都可以利用服务器VM，因此在更高版本中仅提供该VM实现。

### 2.编译器控制

> https://docs.oracle.com/en/java/javase/13/vm/compiler-control1.html#GUID-94AD8194-786A-4F19-BFFF-278F8E237F3A

编译器控件提供了一种通过编译器指令选项控制Java虚拟机（JVM）编译的方法。控制级别是运行时可管理的，并且特定于方法。

编译器指令是告诉JVM如何进行编译的指令。指令可在控制编译过程中提供方法上下文的精度。您可以使用指令编写小型的，包含的JVM编译器测试，这些测试可以在不重新启动整个JVM的情况下运行。您还可以使用指令在JVM编译器中为错误创建解决方法。

通过命令行启动程序时，可以指定一个包含编译器指令的文件。您还可以使用诊断命令从已运行的程序中添加或删除指令。

编译器控件将取代并且向后兼容CompileCommand。

- 编写指令
  - [编写指令文件](https://docs.oracle.com/en/java/javase/13/vm/writing-directives.html#GUID-8D24F71C-00A0-4959-AF10-1E08201B0B69)
  - [编写编译器指令](https://docs.oracle.com/en/java/javase/13/vm/writing-directives.html#GUID-4191CF8A-8FBB-4DB1-9275-DE438B7EE69A)
  - [在编译器指令中编写方法模式](https://docs.oracle.com/en/java/javase/13/vm/writing-directives.html#GUID-EAAA6987-3F98-42FB-A877-C6169B4C71BE)
  - [编写内联指令选项](https://docs.oracle.com/en/java/javase/13/vm/writing-directives.html#GUID-F9B12DF3-50D7-432F-942C-BD554FF41865)
  - [使用“启用”选项防止重复](https://docs.oracle.com/en/java/javase/13/vm/writing-directives.html#GUID-D89AB9B7-B72B-4889-B3F3-4FEABEC783C1)

- 了解指令
  - [什么是默认指令？](https://docs.oracle.com/en/java/javase/13/vm/understanding-directives-better.html#GUID-1011AB83-1C0E-4C4B-B302-4CD487F25C61)
  - [指令如何应用于代码？](https://docs.oracle.com/en/java/javase/13/vm/understanding-directives-better.html#GUID-FB010DC3-9E3C-4D19-AEDE-9527DAA1AD7D)
  - [编译器控制和向后兼容性](https://docs.oracle.com/en/java/javase/13/vm/understanding-directives-better.html#GUID-AC93D367-C00F-4054-83A0-42C4BD5C4F87)

- 用于处理指令文件的命令
  - [编译器指令和命令行](https://docs.oracle.com/en/java/javase/13/vm/commands-work-directive-files.html#GUID-3517007F-824A-4079-B374-188C107D9AB2)
  - [编译器指令和诊断命令](https://docs.oracle.com/en/java/javase/13/vm/commands-work-directive-files.html#GUID-4B31D43A-EEBF-47E0-AAB5-9BEB23B7CFC2)
  - [指令堆栈中的指令顺序如何？](https://docs.oracle.com/en/java/javase/13/vm/commands-work-directive-files.html#GUID-0BE73FEB-C133-4907-869A-42F9E4646E9D)

### 3.垃圾收集

> https://docs.oracle.com/en/java/javase/13/vm/garbage-collection-enhancements.html

Oracle的HotSpot VM包含多个垃圾收集器，可用于帮助优化应用程序的性能。如果您的应用程序处理大量数据（数GB），具有多个线程并且具有高事务处理率，则垃圾收集器特别有用。

有关可用垃圾收集器的说明，请参见《Java平台标准版HotSpot虚拟机垃圾收集优化指南》中的[垃圾收集实现](https://www.oracle.com/pls/topic/lookup?ctx=en/java/javase/13/vm&id=JSGCT-GUID-23844E39-7499-400C-A579-032B68E53073)。

### 4.类数据共享

> https://docs.oracle.com/en/java/javase/13/vm/class-data-sharing.html#GUID-7EAA3411-8CF0-4D19-BD05-DF5E1780AA91

### 5.Java HotSpot虚拟机性能增强

> https://docs.oracle.com/en/java/javase/13/vm/java-hotspot-virtual-machine-performance-enhancements.html#GUID-3BB4C26F-6DE7-4299-9329-A3E02620D50A

### 6.JVM Constants API

https://docs.oracle.com/en/java/javase/13/vm/jvm-constants-api.html#GUID-3C060795-4516-4950-802F-B196F8E936E5

JVM Constants API在包中定义 `java.lang.constants`，其中包含各种类型的可加载常量的标称描述符。这些名义上的描述符对于处理类文件和编译时或链接时程序分析工具的应用程序很有用。

标称描述符不是可加载常量的值，而是对其值的描述，可以在给定类加载上下文的情况下对其进行重构。可加载常量是一个常量池条目，可以将其压入操作数堆栈，也可以出现在`invokedynamic` 指令的引导方法的静态参数列表中。操作数栈是JVM指令获取其输入并存储其输出的地方。每个Java类文件都有一个常量池，其中包含几种常量，从编译时已知的数字文字到必须在运行时解析的方法和字段引用。

使用非标称可加载常量（例如`Class`在运行时解析其引用的 对象）时存在的问题是，这些引用取决于类加载上下文的正确性和一致性。类加载可能会有副作用，例如，您不希望运行的代码运行，并引发与访问相关的异常和内存不足异常，您可以使用名义上的描述来避免这种情况。此外，可能根本无法加载类。

请参阅包装[`java.lang.constant`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/constant/package-summary.html)。

### 7.对非Java语言的支持

> https://docs.oracle.com/en/java/javase/13/vm/support-non-java-languages.html#GUID-CC00C59C-0426-487A-A836-A40E5E67A0CE

### 8.信号链

> https://docs.oracle.com/en/java/javase/13/vm/signal-chaining.html#GUID-CB49A2A7-2A9F-4C18-948F-6D4A96FF688D

### 9.内存跟踪

> https://docs.oracle.com/en/java/javase/13/vm/native-memory-tracking.html#GUID-710CAEA1-7C6D-4D80-AB0C-B0958E329407

### 10.DTrace Probes in HotSpot VM(探针)

> https://docs.oracle.com/en/java/javase/13/vm/dtrace-probes-hotspot-vm.html#GUID-78348097-CD1C-4D1D-BE34-CB24EEC982C4

## 三.GC

> https://docs.oracle.com/en/java/javase/13/gctuning/introduction-garbage-collection-tuning.html

### 1.垃圾收集器

从台式机上的小程序到大型服务器上的Web服务，各种各样的应用程序都使用Java平台标准版（Java SE）。为了支持这种多样化的部署范围，Java HotSpot VM提供了多个垃圾收集器，每个垃圾收集器旨在满足不同的需求。Java SE根据运行应用程序的计算机的类别选择最合适的垃圾收集器。但是，此选择可能并非对每个应用程序都是最佳的。具有严格性能目标或其他要求的用户，开发人员和管理员可能需要明确选择垃圾回收器并调整某些参数以实现所需的性能水平。本文档提供了有助于完成这些任务的信息。

首先，在串行世界级收集器的上下文中描述了垃圾收集器的一般功能和基本调整选项。然后介绍其他收集器的特定功能以及选择收集器时要考虑的因素。

