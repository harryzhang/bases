title: "Java研发复习笔记(五)--IO/NIO"
date: 2015-10-22 11:13:00
author: "郑江龙"
description: java IO/NIO知识总结
categories: interview
tags:
    - Java
    - interview
---

## IO/NIO
Java IO与NIO
在以前的Java IO中，都是阻塞式IO，NIO引入了非阻塞式IO。
第一种方式：我从硬盘读取数据，然后程序一直等，数据读完后，继续操作。这种方式是最简单的，叫阻塞IO。
第二种方式：我从硬盘读取数据，然后程序继续向下执行，等数据读取完后，通知当前程序（对硬件来说叫中断，对程序来说叫回调），然后此程序可以立即处理数据，也可以执行完当前操作在读取数据。

流与块的比较
原来的 I/O 库(在 java.io.*中) 与 NIO 最重要的区别是数据打包和传输的方式。正如前面提到的，原来的 I/O 以流的方式处理数据，而 NIO 以块的方式处理数据
面向流 的 I/O 系统一次一个字节地处理数据。一个输入流产生一个字节的数据，一个输出流消费一个字节的数据。为流式数据创建过滤器非常容易。链接几个过滤器，以便每个过滤器只负责单个复杂处理机制的一部分，这样也是相对简单的。不利的一面是，面向流的 I/O 通常相当慢。
一个 面向块 的 I/O 系统以块的形式处理数据。每一个操作都在一步中产生或者消费一个数据块。按块处理数据比按(流式的)字节处理数据要快得多。但是面向块的 I/O 缺少一些面向流的 I/O 所具有的优雅性和简单性。

通道与流	
Channel是一个对象，可以通过它读取和写入数据。拿 NIO 与原来的 I/O 做个比较，通道就像是流
通道与流的不同之处在于通道是双向的。而流只是在一个方向上移动(一个流必须是 InputStream 或者 OutputStream 的子类)， 而 通道 可以用于读、写或者同时用于读写。

缓冲区
在 NIO 库中，所有数据都是用缓冲区处理的。在 NIO 库中，所有数据都是用缓冲区处理的。

Position: 表示下一次访问的缓冲区位置
Limit: 表示当前缓冲区存放的数据容量。
Capacity:表示缓冲区最大容量
Flip():
它将 limit 设置为当前 position。
它将 position 设置为 0
Clear:
它将 limit 设置为与 capacity 相同。
它设置 position 为 0。

NIO详解 http://www.ibm.com/developerworks/cn/education/java/j-nio/#ibm-pcon
