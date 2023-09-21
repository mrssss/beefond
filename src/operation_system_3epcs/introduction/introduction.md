# 操作系统介绍

**操作系统做了什么？**

* 资源的虚拟化
  * CPU
  * 内存
  * 磁盘
  * 其他设备
* 处理并发问题
* 持久化存储文件

## 虚拟化CPU

在硬件的帮助下，操作系统负责提供系统拥有非常多虚拟CPU的假象。

```c
{{ #include ./cpu.c }}
```

```shell
./cpu A &; ./cpu B &; ./cpu C &; ./cpu D &;
```

## 虚拟化内存

操作系统为每个进程提供私有虚拟内存地址空间。
操作系统以某种方式映射到机器的物理内存。
一个进程不会影响到其他进程的地址空间。

```c
{{ #include ./mem.c }}
```

```shell
./mem &; ./mem &;
```

## 并发

进程看上去像是在同一时间内执行的。

```c
{{ #include ./threads.c }}
```

```shell
./threads 20000
```

## 持久性

持久存储数据

```c
{{ #include ./file_write.c }}
```

```shell
./file_write
```

# 操作系统设计目标

1. 建立**抽象**，让操作系统方便和易于使用
2. 最小化操作系统的开销，实现**高性能**
3. 在应用程序之间以及操作系统和应用程序之间的**提供保护**
4. 提供高度的**可靠性**