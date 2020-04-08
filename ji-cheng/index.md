# 继承

继承是多态的前提，没有继承就没有多态


<!-- more -->


## 概述

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1578116972540.png)

## 格式

在继承关系中，子类就是一个父类，关系：is-a

父类格式（普通类）

```java
public class 父类名称{
  //...
}

```

子类格式

```java
public class zilei extends fulei{
  //...
}
```

## 继承中成员变量访问特点

在父子继承关系中，如果有重名变量，则创建子类对象时，有两种方法

1. 直接通过子类访问成员变量

等号左边是谁，就优先用谁，没有则向上找。

2. 间接通过成员方法

该方法属于谁就优先用谁

### 直接访问



```java
public class Empolyee{
  int age = 20;
}

----------------------
  
public class Teacher extends Employee{
  int age  = 39;
}
```



```java
public class Demo{
  public class void main(String[] args){
    Thacher te = new Teacher();//等号左边是谁用谁
    te.age;//39
  }
  
}
```

### 间接访问



```java
public class Empolyee{
  int age = 20;
  public void methodFu(){
    System.out.println(age);
  }
}

----------------------
  
public class Teacher extends Employee{
  int age  = 39;
  public void methodZi(){
    System.out.println(age);
  }
}
```



```java
public class Demo{
  public class void main(String[] args){
    Thacher te = new Teacher();//等号左边是谁用谁
    te.age;//39
    
    te.methodZi();//39
    te.methodFu();//20
  }
  
}
```



## super， this 关键字



```java
public class Empolyee{
  int age = 20;
}

----------------------
  
public class Teacher extends Employee{
  int age  = 39;
  public void methodZi(){
    int age  = 10
    System.out.println(age);//10
    System.out.println(this.age);//39
    System.out.println(super.age);//20
  }
}
```



### super 的3种用法

1. 在子类成员方法中，访问父类成员变量
2. 在子类成员方法中，访问父类成员方法
3. 在子类构造方法中，访问父类构造方法



```java
public class Empolyee{
  int age = 20;
  public void method(){
    System.out.println("Fu");
  }
}

----------------------
  
public class Teacher extends Employee{
  int age  = 39;
  public Teacher(){
    super();
  }
  public void method(){
		super.age;
    super.method;
    
  }
}
```

## This 3种用法

1. 在本类成员方法中，访问本类成员变量
2. 在本类成员方法中，访问本类另一个成员变量
3. 在本类的构造方法中，访问本类的另一个构造方法

A. 第三种this(...)必须写在方法的第一行，唯一一个语句 

B. super() this()两种构造调用不能同时使用



```java
public class Empolyee{
  int age = 20;
}

----------------------
  
public class Teacher extends Employee{
  int age  = 39;
  
  public Zi(){
    this(123)//本类无参数构造调用有参 
  }
  
  public Zi(int a){
    
  }
  public void methodZi(){
    int age  = 10
    System.out.println(age);//10
    System.out.println(this.age);//39
    System.out.println(super.age);//20
  }
  public void methodA(){
    this.methodZi();
  }
}
```

## 继承的三个特点

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1578116853041.png)
