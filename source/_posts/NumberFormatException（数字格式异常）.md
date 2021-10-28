---
title: NumberFormatException（数字格式异常）
date: 2021-10-13 14:48:35
tags:
 - exception
 - java
categories: java
---

```java
public class ExceptionTest {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入数字:");
        int num = Integer.parseInt(scanner.next()); //解析控制台输入的整数
        System.out.println(num);
    }
}
```

scanner要求输入数字，并通过Integer.parseInt将参数转换为一个整数，再输出这个整数。 

如果输入123，屏幕会输出123，但如果用户输入的不是数字，比如doge，屏幕会输出：

```java
Exception in thread "main" java.lang.NumberFormatException: For input string: "doge"
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
	at java.lang.Integer.parseInt(Integer.java:580)
	at java.lang.Integer.parseInt(Integer.java:615)
	at com.example.restservice.ExceptionTest.main(ExceptionTest.java:9)

```

出现异常NumberFormatException。

​     

对于屏幕输出中的异常栈信息，开发者是可以理解的，但普通用户无法理解。
我们需要给用户一个更为友好的信息，告诉用户，ta应该输入的是数字。要做到这一点，我们需要自己“捕获”异常。

“捕获”是指使用try/catch关键字，捕获异常后的示例代码如下：

```java
public class ExceptionTest {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入数字:");
        String input = scanner.next();
        try {
            int num = Integer.parseInt(input); //解析控制台输入的整数
            System.out.println(num);
        } catch (NumberFormatException e) {
            System.err.println("参数"+input+"不是有效的数字，请输入数字。");
        }
    }
}
```

使用**try/catch捕获并处理了异常**，try后面的大括号{}内包含可能抛出异常的代码，括号后的catch语句包含能捕获的异常和代理代码。

catch后面括号内是异常信息，包括异常类型和变量名，这里是NumberFormatException e。大括号{}内是处理代码，这里输出一个更为友好的提示信息。

**捕获异常后，程序就不会异常退出了，但try语句内异常点之后的其他代码就不会执行了，执行完catch内的语句后，程序会继续执行catch大括号外的代码。**

​    

异常是相对于return的一种退出机制，可以由系统触发，也可以由程序通过**throw语句**触发。异常可以通过try/catch语句进行捕获并处理，如果没有捕获，则会导致程序退出并输出异常栈信息。



