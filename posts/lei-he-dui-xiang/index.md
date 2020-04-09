# 类和对象

类：是一种相关行为和属性的集合，可以看成一类事物的模版，使用事物属性和行为描述该类

<!-- more -->

## 类和对象对比

### 类

类：是一种相关行为和属性的集合，可以看成一类事物的模版，使用事物属性和行为描述该类

属性：该事物状态信息

行为：该事物能干什么

例如：猫

属性名字，体重，颜色

行为：走，跑，叫

### 对象

对象是类的一个实例，必然必备该事物的属性和行为

## 类和对象在Java实例

类为学生

成员变量：

1. 姓名
2. 年龄

成员方法：

1. 吃饭
2. 睡觉
3. 做爱

成员变量在类内，方法外

```java
public class Student{
  String name;
  int age;
  
  public void eat(){
    System.out.println("吃饭饭");
  }
  
  public void sleep(){
    System.out.println("睡觉觉");
  }
  
  public void sex(){
    System.out.println("做爱爱");
  }
}
```

## 类的使用

1. 导包

import 包名称.类名称；

2. 创建

类名称 对象名 = new 类名称();

Student stu = new Student();

3. 使用

使用成员变量：对象名.成员变量名

使用成员方法：对象名.成员方法名();

```java
public class DemoStudent{
  public static void main(String[] args){
    Student stu = new Student();
    
    stu.age = 18;
    stu.sex();
  }
}
```


