# 动态内存管理

## 动态内存分配
```c
// 分配内存
type * p = (type*) malloc(sizeof(type));

// 使用内存
...

// 释放内存
free(p);
```
内存被释放之后，就不应该再访问它了。
# 常见问题
## 内存泄漏
对象被使用完之后，没有被释放。

导致内存泄漏的原因：
* 丢失内存地址
* 应该调用free函数但是没有被调用

如果从堆管理器中申请的内存，但是没有及时的释放。
这会导致程序可以使用的内存变少，最终需要内存的时候，调用malloc会出错，
导致程序终止。

1.丢失地址
```c
int * pi = (int*)malloc(sizeof(int));
*pi = 5;
pi = (int*)malloc(sizeof(int));
```

第一次被分配的内存空间，在第二次分配内存之后就没有办法找到了。
这时，第一次被分配的内存空间就没有办法正常的释放给堆管理器。

2.隐式内存泄漏
