# 抽象方法，抽象类

如果父类当中不确定如何进行{}方法体实现，那么这应该是一个抽象方法
<!-- more -->


## 概述

![](https://linon419.github.io/post-images/1578122009912.png)

## 格式

抽象方法就是加上abstract 关键字，然后去掉大括号，直接；结束

抽象类：抽象方法所在的类，必须是抽象类才行，在class之前加上abstract



```java
public abstract class Animal{
  public abstract void eat();
  
  public void method(){};//正确
}
```

## 使用

1. 不能直接创建new抽象类对象
2. 必须用一个子类来继承抽象父类
3. 子类必须覆盖重写所有抽象父类的抽象方法

覆盖重写：去掉abstract加上{}

4. 创建子类对象使用





```java
public abstract class Animal{
  public abstract void eat();
  
  public void method(){};//正确
}

public class Cat extends Animal(){
  public void eat(){
    System.out.println("eat fish");
  }
}
```



```java
public class DemoAbs{
  public static void main(String[] args){
    Cat cat = new Cat();
    cat.eat();
  }
}
//results: eat fish
```


