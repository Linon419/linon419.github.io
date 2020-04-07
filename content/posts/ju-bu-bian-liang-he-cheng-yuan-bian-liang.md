---
title: '局部变量和成员变量'
date: 2020-01-03 19:32:19
tags: ["Java"]
categories: ["Java"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
局部变量和成员变量的区别

<!-- more -->

## 局部变量和成员变量

1. 定义的位置不一样

局部变量：在方法内部

成员变量：在方法外部，类内部

2. 作用范围不一样

局部变量：只能在方法内使用

成员变量：整个类都可以使用

3. 默认值不一样

局部变量：没有默认值，如果想使用，收到赋值

成员变量：会有默认值，规则和数组一样



```java
public class VirableDifferences(){
  String name;//成员变量
  
  public void methodA(){
    int num = 20;//局部变量
    int age;
    System.out.println(age);//局部变量必须赋值
  }
  
  public void methodB(int parma){//方法的参数就是局部变量
    System.out.println(parma);//方法调用必须给参数赋值
  }
}
```

