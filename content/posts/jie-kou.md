---
title: '接口'
date: 2020-01-05 12:37:38
tags: ["Java"]
categories: ["Java"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
接口是多个类的公共规范。

接口是一种引用类型，最重要的内容就是其中的抽象方法。

<!-- more -->

## 接口定义

接口是多个类的公共规范。

接口是一种引用类型，最重要的内容就是其中的抽象方法。

## 接口格式

```java
public interface 接口名称{
  	//接口内容
}
```

如果是Java7，接口内容应该有，

1. 常量

2. 抽象方法

如果是Java8，接口可以有，

3.  默认方法
4.  静态方法      

如果是Java9，接口可以有

5. 私有方法

### 抽象方法定义

在任何版本的Java中，都能定义接口方法，

格式：

```java
public abstract 返回值类型 方法名称(参数列表);
```

注意事项：

1. 接口中抽象方法，修饰符必须为两个固定关键字，public，abstract
2. 两个修饰符可以选择性省略

```java
public abstract void methodsAbs();
abstract void methodsAbs1();
public void methodsAbs2();
void methodsAbs3();
都是对的
```

### 接口使用步骤

1. 接口不能直接使用，必须有一个实现类来实现该接口

格式：

```java
public class 实现类名称 implements 接口名称{
  ...
}
```

2. 接口的实现必须覆盖重写（实现）接口中所有抽象方法

  实现：去掉abstract关键字，加上方法体大括号。

3. 创建实现类的对象，进行使用

```java
public interface MyInterfaceAbstract{
  
  public abstract void methodAbs();//抽象方法
}

public class MyInterfaceimpl implements MyInterfaceAbstract{
  
  @override
  public void methodAbs(){
    System.out.println("吃饭");
  }
}
```

```java
public class Demo{
  public class void main(String[] args){
  	MyInterfaceimpl impl = new MyInterfaceimpl();
    impl.methodAbs();
  }
}

//results: 吃饭
```



## 默认方法

问题描述：所有实现类都以使用，但接口想添加新方法，所有实现类必须覆盖重写又一次

从java8开始接口允许定义默认方法

格式：

```java
public default 返回值类型 方法名称（参数列表）{
  方法体
}
```



```java
public interface MyInterface{
  public abstract void methodAbs();
  
  public default void methodDefult(){
    System.out.println("Let's dance");
  }
}

public class MyInterfaceimpl implements MyInterface{
  @override 
  public void methodAbs(){
    System.out.println("111");
  }
  
}
```



```java
public class Demo{
  public static void main(String[] args){
    
    MyInterfaceimpl impl = new MyInterfaceimpl();
    impl.methodAbs();
    impl.methodDefault();
  }
}
//results: 111
// Let's dance
```



##  静态方法

Java8开始使用静态方法

格式：

```java
public static 返回值类型 方法名称(参数列表){
  //方法体
}
```





```java
public interface MyInterfaceStatic{
  
  public static void methodStatic(){
    System.out.println("static successed");
  }
}

public class MyInterfaceimpl implements MyInterfaceStatic{
  @override 
  public void methodAbs(){
    System.out.println("111");
  }
  
}
```



```java
public class Demo{
  public static void main(String[] args){
    
    MyInterfaceimpl impl = new MyInterfaceimpl();
    impl.methodStatic();// wrong
		MyInterfaceStatic.methodStatic;//right
  }
}
//results: 111
// Let's dance
```

## 私有方法

问题描述：我们需要抽取一个公用方法来解决两个默认方法直接重复代码问题，但这个共有方法不应该让实现类使用，应该是私有化的

解决方案

从Java 9 开始，接口允许定义私有方法

1. 普通私有方法，解决多个默认方法之间重复代码问题

```java
private 返回值类型 方法名称(参数列表){
  //...
}
```

2. 静态私有方法，解决多个静态方法之间重复代码问题

```java
private static 返回值类型 方法名称(参数列表){
  //...
}
```

普通私有方法

```java
public interface MyInterface{  
  public default void methodDefult1(){
    System.out.println("Let's dance1");
    methodCommon();
  }
  
  public default void methodDefult2(){
    System.out.println("Let's dance2");
    methodCommon();
  }
  
  private void method(){
    System.out.println("Let's have sex");
    System.out.println("Let's have sex");
    System.out.println("Let's have sex");
  }
}
```



静态私有方法



```java
public interface MyInterface{  
  public static void methodStatic1(){
    System.out.println("Let's dance1");
    methodCommon();
  }
  
  public static void methodStatic2(){
    System.out.println("Let's dance2");
    methodCommon();
  }
  
  private static void method(){
    System.out.println("Let's have sex");
    System.out.println("Let's have sex");
    System.out.println("Let's have sex");
  }
}
```





```java
public class Demo{
  public static void main(String[] args){
    impl.methodStatic1();// wrong
		MyInterfaceStatic.methodStatic1;//right
  }
}
//results: 111
// Let's dance
```



## 接口的常量

接口中也可以定义“成员变量”，但是必须使用 private, static, final 三个关键字进行修饰

从效果上看，这就是接口的常量

格式：

public static final 数据类型 常量名称 = 值；

一旦使用final，说明数据不可变

注意事项：

1. 接口当中的常量，可以省略三个关键字
2. 必须赋值
3. 常量名称使用大写，下划线

```java
public interface MyInterfaceConst{
  public static final int NUM = 2;//必须赋值
}
```



```java
public class Demo{
  public static void main(String[] args){
    impl.methodStatic1();// wrong
		System.out.println(MyInterfaceConst.NUM);//right
  }
}
//result is 2
```



## 继承父类并实现多个接口

1. 接口没有静态代码块或构造方法的
2. 一个类的直接父类是唯一的，但是一个类可以实现多个接口

格式：

```java
public class MyInterfaceImpl implements MyInterfaceA, MyInterfaceB{
  //覆盖重写所有抽象方法
}
```

3. 如果实现类所实现的多个接口中有重复抽象方法，只需覆盖重写一次
4. 如果实现类没有覆盖重写所有抽象方法，那么该类为抽象类
5. 如果实现类所实现的多个接口中，存在重复的默认方法，那么实现类必须对默认方法进行覆盖重写
6. 一个类如果他的直接父类中的方法和接口中的方法产生冲突，父类方法优先

## 接口之间可以多继承

```java
public interface MyInterface extends MyInterfaceA, MyInterfaceB{
  //...
}
```

