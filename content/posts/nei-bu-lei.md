---
title: '内部类'
date: 2020-01-06 20:13:41
tags: ["Java"]
categories: ["Java"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
如果一个事物包含另一个事物，那么这就是一个类内部包含另一个类

例如：人体和心脏，汽车和发动机

<!-- more -->

## 分类

1. 成员内部类
2. 局部内部类（包含匿名内部类）

### 成员内部类

格式：

```java
修饰符 class 外部类名称{
	修饰符 class 内部类名称{
    //...
  }
  //...
}
```

注意；内用外，随意访问。外用内，需要内部类对象

```java
public class Body{//外部类
  public class Heart{//内部类
    
    public void beat(){//内部类的方法
      System.out.println("bibibi");
      System.out.println("my name is"+name);
    }
  }
  
  private String name;
}
```

如何使用成员内部类？

方法：

1. 间接方式：在外部类的方法当中，使用内部类；然后main只是调用内部类的方法
2. 直接方式：外部类名称 .内部类名称 对象名 = new 外部类名称().new 内部类名称



```java
public class Body{//外部类
  public class Heart{//内部类
    
    public void beat(){//内部类的方法
      System.out.println("bibibi");
      System.out.println("my name is"+name);
    }
  }
  
  public void methodBody(){
    Heart heart = new Heart();
    heart.beat();
    
    //或者 
    new Heart.beat();
  }
  private String name;
}
```



```java
public class Demo{
  Body bo = new Body();
  //通过外部类对象调用外部类方法，里面间接使用内部类Heart 
  bo.methodBody();
  //直接访问
  Body.Heart heart = new Body().new Heart();
}
```

### 内部类的同名变量访问

外部类名称.this.外部类成员变量名

```java
public class Outer{
  int num = 10;
  public class Inner{
    int num = 20;
    
    public void method(){
      int num = 30;
      System.out.println(num);//30
      System.out.println(this.num);//20
      System.out.println(Outer.this.num);//
    }
  }
}
```

### 局部内部类

如果一个类定义在方法内部，那么这就是一个局部内部类

“局部”：只有当前所属的方法才能使用它，出了方法外就不能用了



格式：

```java
修饰符 class 外部类名称{
	修饰符 返回值类型 外部类方法名称(参数列表){
    class 局部类名称{
      //...
    }
  }

}
```

````java
public class Outer{
	public void methodOuter(){
    class Inner{//局部内部类
      int num = 10;
      public void methodInner(){
        System.out.println(num);
      }
    }
  
    Inner inner = new Inner();
  	inner.methodInner;
  }
}


public class Demo{
  
  public static void main(String[] args){
    Outer obj = new Outer();
    obj.methodOuter();//10
  }
}
````

权限修饰符的小结：

public > protected > (default) > private

1. 外部类：public，default
2. 成员内部类：都行
3. 局部内部类：都不行



### 匿名内部类

如果接口的实现了类（或父类的子类），只需要使用唯一一次

那么该情况下可省略该类的定义，称为匿名内部类

格式：

```java
接口名称 对象名 = new 接口名称(){
  //覆盖重写抽象方法
};
```



实例

```java
public interface MyInterface{
  
  public void method(){
    System.out.println("这是接口");
  }
}


public class Demo{
  
  public static void main(String[] args){
    
    MyInterface obj = new MyInterface(){
      @override
      public void method(){
        
        System.out.println("这是匿名内部类");
      }
      
    };
    obj.method();//这是匿名内部类
  }
}
```

对格式"new 接口名称(){...}"解析

1. new 代表创建对象动作
2. 接口名称就是匿名内部类需要实现哪个接口
3. {///...}是匿名内部类内容

另外几点

1. 匿名内部类在【创建对象】时，只能使用唯一一次

如果希望多次创建对象。而且类内容一样，需要单独定义实现类

2. 匿名对象在调用方法时，只能调用唯一一次

如果希望同一对象，调用多个方法，必须给对象起名字

3. 匿名内部类省略了实现类，匿名对象省略了【对象名称】。两个不是一回事

```java
public interface MyInterface{
  
  public void method(){
    System.out.println("这是接口");
  }
}


public class Demo{
  
  public static void main(String[] args){
    
    MyInterface obj = new MyInterface(){
      @override
      public void method(){
        
        System.out.println("这是匿名内部类");
      }
      
    };
    obj.method();//这是匿名内部类
    
    new MyInterface(){//匿名对象
      @override
      public void method(){
        
        System.out.println("这是匿名内部类");
      }
      
    }.method();
  }
} 
```

