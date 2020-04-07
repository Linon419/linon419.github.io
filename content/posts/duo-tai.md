---
title: '多态'
date: 2020-01-05 17:42:50
tags: ["Java"]
categories: ["Java"]
published: true
hideInList: false
feature: 
isTop: false
---

继承或接口是多态的前提

<!-- more -->


![](https://linon419.github.io/post-images/1578195792304.png)
## 格式

代码中体现多态性，其实就是一句话，父类引用指向子类对象

格式：

父类名称 对象名 = new 子类名称();

接口名称 对象名 = new 实现类名称();

```java
public class Fu{
  public void method(){
    System.out.println("fufufu");
  }
  
  public void methodFu(){
    Systm.out.println("only fu");
  }
}

public class Zi extends Fu{
  public void method(){
    System.out.println("zizizi");
  }
}
```



```java
public class Demo(){
  public static void main(String[] args){
    Fu obj = new Zi();//左父右子
    obj.method();//zizizi
    obj.methodFu();//only fu
  }
  
}
```

## 多态中成员变量访问特点

1. 直接通过对象名访问（等号左边是谁，优先用谁，没有向上找）
2. 间接通过方法访问（看方法属于谁，优先用谁）

```java
public class Fu{
  int num = 10;
  public void method(){
    System.out.println(num);
  }
}

public class Zi{
  int num = 20;
  @override
  public void method(){
    System.out.println(num);
  }
}
```



```java
public class Demo(){
  public static void main(String[] args){
    Fu obj = new Zi();//左父右子
    obj.num();//10
    obj.method();//20
  }
  
}
```



## 成员方法访问特点

看new的是谁，就优先用谁，没有则向上找

口诀：编译看左边，运行看右边



```java
public class Fu{
  int num = 10;
  public void method(){
    System.out.println("父类");
  }
  
  public void methodFu(){
    System.out.println("父类特有方法");
  }
}

public class Zi{
  int num = 20;
  @override
  public void method(){
    System.out.println("子类");
  }
  
  public void methodZi(){
    System.out.println("子类特有");
  }
}
```



```java
public class Demo(){
  public static void main(String[] args){
    Fu obj = new Zi();//左父右子
    obj.num();//10
    obj.method();//父子都有，优先用子，运行看右
    obj.mehtodFu();//子类无，父类有，向上找到父类
    //obj.methodZi();//编译看左，父类无此方法，错误写法
  }
  
}
```

## 多态的好处

![](https://linon419.github.io/post-images/1578195814404.png)



## 对象的向上转型

![](https://linon419.github.io/post-images/1578195825233.png)



## 对象的向下转型

![](https://linon419.github.io/post-images/1578195833728.png)

### Instanceof关键字使用

如何才能知道一个父类引用的对象本来是什么子类？

格式：

对象 Instanceof 类名称

将会得到一个布尔值

```java
public class Animal{
  public void eat(){
    System.out.println("eat food");
  }
}

public class Cat extends Animal{
  public void eat(){
    System.out.println("eat fish");
  }
  
  public void catchMouse(){
    System.out.println("catch");
  }
}

public class Dog extends Animal{
  public void eat(){
    System.out.println("eat shit");
  }
  
  public void watch(){
    System.out.println("watch");
  }
    
}
```



```java
public class Demo{
  public static void main(String[] args){
    Animal animal = new Cat();//is a cat
    aninal.eat();//eat fish
    giveMePet(new Dog())
  }
  
  public static void giveMePet(Animal animal){
    if(Animal instanceof Dog){// 各尽其职
      Dog dog = (Dog) animal;//向下转型
      dog.watch();
    } 
    if (Animal instanceof Cat){
      Cat cat = (Cat) animal;
      cat.catchMouse;
    }
  }
}
```

