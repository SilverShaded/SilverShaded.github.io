---
title: 继承的细节--protected
date: 2021-09-03 19:08:43
tags:
 - java
 - class
 - extends
categories: java
---

继承和多态概念还有一些相关的细节，具体包括：

- 构造方法  
- 重名与静态绑定 
- 重载和重写
- 父子类型转换 
- 继承访问权限（protected） <font color=blue>now!</font>
- 可见性重写
- 防止继承（final）

​    

除了public/private之外，还有一种可见性介于中间的修饰符**protected**。

protected表示虽然不能被外部操作访问，但可被子类访问，还可被同一个包中的其他类访问（不管其他类是否是该类的子类）。

​    

举个栗子，基类Base代码如下：

```java
public class Base {
    protected int currentStep;

    protected void step1() {
    }

    protected void step2() {
    }

    public void action() {
        this.currentStep = 1;
        step1();
        this.currentStep = 2;
        step2();
    }
}
```

含有protected修饰符的是变量currentStep和方法step1、step2，还对外提供了方法action。

子类一般不重写action，只重写step1和step2。同时，子类可以直接访问currentStep查看进行到了哪一步。

子类Child的代码如下：

```java
public class Child extends Base{
   protected void step1 () {
       System.out.println("child step "+this.currentStep);
   }

   protected void step2 () {
       System.out.println("child step "+this.currentStep);
   }
}
```

使用子类的main方法代码如下：

```java
public static void main(String[] args) {
   Child child = new Child();
   child.action();
}
```

输出结果为：

```java
child step 1
child step 2
```

子类通过重写protected方法step1和step2，来修改对外的行为。

​    

这种思路和设计在设计模式中被称之为**模板方法**，action就是一个模板方法，它定义了实现的模板，而具体实现由子类提供。

模板方法在很多框架中由广泛的应用，这是使用protected的一个常用场景。



