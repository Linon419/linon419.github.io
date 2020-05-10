# Java反射简单概念




反射，就是通过Class文件对象，获取该文件中的成员变量，构造方法，成员方法



要想这样使用，先要得到Class文件对象

Class类：

​	成员变量：Filed

​	构造方法：Constructor

​	成员方法： Method

## 获取对象三种方式

获取Class对象的方式：

1. Object类的getClass()方法
2. 数据类型的静态属性方法class
3. Class类中的静态方法

`public static Class forName(String ClassName)`

```java
public class Reflect {
    //the first way
    public static void main(String[] args) throws ClassNotFoundException {
        Person p1 = new Person();
        Class c1 = p1.getClass();

        Person p2 = new Person();
        Class c2 = p2.getClass();
        System.out.println(p1==p2);//false
        System.out.println(c1==c2);//true

        //the second way
        Class c3 = Person.class;
        System.out.println(c3==c1);//true

        //the third way
        Class c4 = Class.forName("com.demo01.Person");
        System.out.println(c4==c1);//true
    }
}
```

## 通过反射获取构造方法

获取构造方法

1. public Constructor[] getConstructors():所有公共构造方法
2. public Constructor[] getDeclaredConstructors()：所有构造方法

获取单个构造方法

`public Constructors<T> getCostructor(Class<?>... parameterTypes)`

获取全参构造

```java
        Class c = Class.forName("com.demo01.Person");
        Constructor con = c.getConstructor(int.class,String.class,String.class);
        Object obj = con.newInstance(23,"Hugo","Australia");
        System.out.println(obj);
```

获取私有方法

```java
        //暴力访问私有方法
        Constructor con2 = c.getDeclaredConstructor(String.class);
        con2.setAccessible(true);
        Object obj2 = con2.newInstance("Liyang");
        System.out.println(obj2);
```

## 获取成员变量

```java
//获得所有公共成员变量
Field[] fields = c.getFields();
//获得所有成员变量
Field[] fields2 = c.getDeclaredFields();

//获得单个成员变量  公共参数
//获取address并对其赋值
Field fields3 = c.getField("address");
Object obj = con.newInstance();
fields3.set(obj,"China");
System.out.println(obj);
//非公共参数 暴力访问
Field field4 = c.getDeclaredField("name");
field4.setAccessible(true);
field4.set(obj,"Yang");
System.out.println(obj);
```

## 获取成员方法

获取所有方法

getMethods

getDeclaredMethods

获取单个方法

getMethod

getDeclaredMethod

暴力访问

method.setAccessible(true);

```java
Class c = Class.forName("com.demo01.Person");
Constructor con = c.getConstructor();
Object obj = con.newInstance();

//public Method getMethod(String name, Class<?> param)
//第一个参数为方法名，第二个为方法参数的Class类型
Method m1 = c.getMethod("show");
//public Object invoke(Object obj, Object args)
//参数对象是谁，该方法的实际参数
m1.invoke(obj);
```


