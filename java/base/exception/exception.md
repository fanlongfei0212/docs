# <img src="../../../images/icon/java.png" width="30" height="30" />异常

---

## 概述：

* **Java的所有的异常基类为Throwable，拥有两个子类，Error和Exception，Exception下分为
RuntimeException和非RuntimeException**

* **Error为程序无法处理的异常，无法进行捕获和人为处理，是JVM的异常**

* **RuntimeException为运行时异常，是程序设计过程中，在运行时可以进行处理的异常，非RuntimeException
为受检查异常，即在编译时需要进行处理的异常，比如：IOException，则需要进try捕获处理**

## 常见的Exception异常

**RuntimeException**

1. NullPointerException-空指针

2. ClassCastException-类型强制转换异常

3. IllegalArgumentException-传递非法参数异常

4. IndexOutOfBoundsException-下标越界异常

5. NumberFormatException-数字格式异常

**非RuntimeException**

1. NoClassNotFoundException-找不到指定Class的异常

2. IOException-IO操作异常

## 常见的Error异常

1. NoClassDefFoundError-找不到class定义的异常

2. StackOverflowError-深递归导致栈被耗尽而抛出的异常

3. OutOfMemoryError-内存溢出异常