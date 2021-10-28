---
title: NullPointerException（空指针异常）
date: 2021-10-13 14:23:59
tags:
 - exception
 - java
categories: java
---

```java
public class ExceptionTest {
    public static void main(String[] args) {
        String s = null;
        s.indexOf("a"); //查找a在字符串s中首次出现的位置
        System.out.println("end");
    }
}
```

运行上面的代码，屏幕输出结果为：

```java
Exception in thread "main" java.lang.NullPointerException
	at com.example.restservice.ExceptionTest.main(ExceptionTest.java:4)
```

当运行s.indexOf("a")时，java系统发现s的值为null，没有办法继续执行，这时就启用异常处理机制：

首先 ，创建一个异常对象——类NullPointerException的对象，然后查找看谁能处理这个异常。在上面的代码中，没有代码能处理这个异常，java就启用默认处理机制，打印异常栈信息到屏幕，并退出程序。

​    

**java的默认异常处理机制是退出程序，异常发生点后的代码都不会执行。**

