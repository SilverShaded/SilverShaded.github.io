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

try/catch/finall语法中，catch不是必须的，可以只有try/finally。这表示不捕获异常，异常自动向上传递。



