---
title: '封装性'
date: 2020-01-03 19:27:36
tags: ["Java"]
categories: ["Java"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
## 封装性在Java中的体现

1. 方法就是一种封装
2. private关键字也是一种封装


<!-- more -->


### 方法封装

```java
//封装就是将一些细节隐藏起来，对外界不可见
public class DemoMethod(){
  public static void main(String[] args){
    int[] array = {0,30,9,40,100};
    int max = getMax(array);
    System.out.println("The max number is"+max);
  }
  
  public static int getMax(int[] array){
    int max = array[0];
    for(int i = 0; i<array.length;i++){
      max = array[i];
    }
    return max;
  }
}
```



### private用法

问题描述：定义Peason年龄时，无法阻止不可理数值设置进来

解决方法：用private关键字将需要保护的成员修饰

使用private后本类可访问，但是！超出本类之后不可直接访问

必须要getXXX，setXXX

对于getter,无参数，返回值和成员变量对应

对于setter，无返回值参数类型和成员变量对应

```java
public class Peason{
  String name;
  int age;
  public void show(){
    System.out.println("My name is"+name="and my age is"+age);
  }
}
```

```java
public class DemoPeason{
	Peason one = new Peason();
  one.name = "🦙"；
  one.age = "-90";//不合常理
  one.show();
}
```

解决方法

```java
public class Peason{
  String name;
  private int age;
  public void show(){
    System.out.println("My name is"+name="and my age is"+age);
  }
  
  public void setAge(int num){
    if(num>0&&num<300)
      age = num;
    else
      System.out.println("参数不正确");
  }
  
  public int getAge(){
    return age;
  }
}
```



```java
public class DemoPeason{
	Peason one = new Peason();
  one.name = "🦙"；
  //one.age = "-90";//不可访问
  one.setAge(20);
  one.show();
}
```



### boolean特例

```java
public class Peason{
  private boolean male;
  
  public setMale(boolean b){
    male = b;
  }
  
  public isMale(){
    return male;
  }
  
}
```

