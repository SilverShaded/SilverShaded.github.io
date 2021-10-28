---
title: RuntimeException的常见子类
date: 2021-10-19 19:10:34
tags:
 - exception
 - java
categories: java
---

|              异常               |       说明       |
| :-----------------------------: | :--------------: |
|      NullPointerException       |    空指针异常    |
|      IllegalStateException      |     非法状态     |
|       ClassCastException        | 非法强制类型转换 |
|    IllegalArgumentException     |     参数错误     |
|      NumberFormatException      |   数字格式错误   |
| ArrayIndexOutOfBoundsException  |   数组索引越界   |
| StringIndexOutOfBoundsException |  字符串索引越界  |

这些异常类其实并没有比Throwable这个基类多多少属性和方法，大部分类在继承父类后只是定义了几个构造方法，这些构造方法也只是强调了父类的构造方法。

定义那么多类，主要是为了名字不同。异常类的名字本身就代表了异常的关键信息。

