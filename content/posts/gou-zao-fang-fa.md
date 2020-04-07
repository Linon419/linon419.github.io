---
title: '构造方法'
date: 2020-01-04 13:30:06
tags: ["Java"]
categories: ["Java"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
构造方法是专门用来创造对象的方法当通过new来创造对象时，就是在调用构造方法。

<!-- more -->

## 格式

```java
public 类名称（参数类型 参数名称）{
  方法体
}
```

## 注意事项

1. 构造方法的名称必须和类名称完全一样，大小写也一样
2. 构造方法不写返回值类型，void也不写
3. 不能return一个具体的返回值
4. 如果没有写任何构造方法，编译器会赠送默认构造方法，无参数，无方法体
5. 一旦自己编写，编译器不再赠送
6. 构造方法也可以重载

重载：方法名称相同，参数列表不同

```java
public class Student{
  private String name;
  private int age;
  public Student(){
    System.out.println("无参构造方法执行啦");
  }
  
  public Student(String name, int age){
    System.out.println("全参构造方法执行啦");
    this.name = name;
    this.age = age;
  }
}
```



```java
public class DemoStudent{
	Student stu1 = new Student();//new出来的为构造方法  
  Student stu2 = new Student("Yang","19")
}
//结果：无参构造方法执行啦
//     全参构造方法执行啦
```

