---
layout:     post
title:      重新认识Java的Interface（接口）
date:       2017-02-17 21:24:11
summary:    重新认识Java的Interface（接口）
categories: jekyll
thumbnail: jekyll
tags:
 - 学习笔记
 - 基础
 - 接口
 - Java
---

最近觉得自己对接口的认识又有些生疏，前段时间为了笔试面试看的那些理论并不是很深刻，加上普通开发人员很少有定义接口的机会，难免会生疏。重新学习了一下。


Java的接口（Interface）是一系列的声明，其中不包括方法的实现。主要作用是精简程序结构，免除重复定义。其声明方式为：
```java
[访问控制符] interface <接口名>{
  类型 final 常量名
}
```
1. 接口中的变量默认自动隐含是```public static final```（都可以省略）；

接口是定义一个规范，public的实例变量不应该是好的接口定义的一部分，因此他们不能在java的接口中定义。

2.  interface的修饰符只能是缺省、public、abstract（“only public & abstract are permitted”）；

3. 一个类实现了某个接口时,必须实现接口中的所有抽象方法,否则该类必须声明为抽象类;

4. 接口不能实现(implements)另一个接口,但它可以继承多个其它的接口；

### Java 8新增的两个新特性：接口的默认方法和类方法

Java 8以前，接口里的方法要求全部是抽象方法，java8以后允许在接口里定义默认方法和类方法：

接口中默认方法和类方法的不同是：默认方法可以通过实现接口的类实例化的对象来调用,类方法只能在本接口中调用或在实现类中实现。

```java
//定义接口
public interface MyInter {
    default void df(){    //声明一个接口的默认方法
        
        System.out.println("i'am default f");
        sf();        //调用本接口的类方法
    }
    static void sf(){    //声明一个接口的类方法
        
        System.out.println("i'am static f");
    }
}

//接口的实现类，注意其中没有实现任何方法
public class Man implements MyInter{    //Man类实现MyInter接口
}

//继承接口的实现类
public class Test extends Man{
    public static void main(String[] args) {
        Man man=new Man();
        man.df();        //通过man对象调用MyInter接口的默认方法df()
    }
}

```
### 注意事项：接口中不要存在实现的方法（很明显接口中无法实现方法，这里说的是通过匿名内部类或者内部类实现的）

接口是一个契约，不仅仅约束着实现者，同事也是一个保证，保证提供的服务（常量、方法）是稳定、可靠的，如果把实现代码写到接口中，那接口就绑定了可能变化的因素，这就会导致实现不再稳定和可靠，是随时都能被抛弃、被更爱、被重构的。所以，接口中虽然可以有实现，单应该避免使用。

——注意事项出自《编写高质量代码：改善java程序的151个建议》
