---
title: 异常中的finally
date: 2021-10-22 20:10:51
tags:
 - exception
 - java
categories: java

---

catch后面可以跟**finally**语句，语法如下：

```java
try {
    //可能抛出异常
} catch (Exception e) {
    //捕获异常
} finally {
    //不管有无异常都执行
}
```

**finally内的代码不管有无异常发生**，都会执行：

- 如果没有异常发生，在try内的代码执行结束后执行。

- 如果有异常发生且被catch捕获，在catch内的代码执行结束后执行。

- 如果有异常发生但没被捕获，则在异常被抛给上层之前执行。

由于finally的这个特点，它一般用于释放资源，如数据库连接、文件流等。

​    

try/catch/finall语法中，catch不是必须的，可以只有try/finally。这表示不捕获异常，异常自动向上传递，但finally中的代码在异常发生后也执行。

​    

**如果在try或者catch语句内有return语句，则return语句在finally语句执行结束后才执行，但finally并不能改变返回值**，我们来看下代码：

```java
public static int test() {
    int ret = 0;
    try {
        return ret;
    }finally {
        ret = 2;
    }
}
```

函数的返回值是0，不是2。在执行到return ret;语句之前，会先将返回值ret保存在一个临时变量中，然后才执行finally语句，最后try再返回那个临时变量，finally中对ret的修改不会被返回。

如果在finally中也有return语句

