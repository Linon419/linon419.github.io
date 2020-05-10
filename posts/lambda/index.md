# Lambda



# Hello Lambda

<!-- more -->

## 普通方法

使用一个普通方法，在for循环遍历中进行条件判断筛选出满足条件的数据

hp>100 && damage<50

```java
// hero
public class Hero implements Comparable<Hero> {
    public String name;
    public float hp;
    public int damage;
    public Hero(){}

    public Hero(String name){
        this.name = name;
    }

    public Hero(String name, float hp, int damage){
        this.name = name;
        this.hp = hp;
        this.damage = damage;
    }
    @Override
    public int compareTo(Hero anotherHero) {

         if (damage<anotherHero.damage){
             return 1;
         } else {
             return -1;
         }
    }

    public String toString(){
        return "Hero [name="+name+", hp "+hp+", damage"+damage+"]\r\n";
    }

}

```

```java
// testlambda
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

public class Normal {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heroes = new ArrayList<Hero>();
        for (int i = 0; i < 10; i++) {
            heroes.add(new Hero("Yang"+i, r.nextInt(1000),r.nextInt(1000)));
        }
        System.out.println("初始化的集合");
        System.out.println(heroes);
        System.out.println("finally");
        find(heroes);

    }

    private static void find(List<Hero> heroes){
        for (Hero hero: heroes){
            if (hero.hp>100&&hero.damage<50){
                System.out.println(hero);
            }
        }

    }
}

```

## 匿名方法

首先准备一个接口HeroChecker，提供一个test(Hero)方法
然后通过匿名类的方式，实现这个接口

 

HeroChecker checker = new HeroChecker() {

​	public boolean test(Hero h) {

​		return (h.hp>100 && h.damage<50);

​	}

};

 


接着调用filter，传递这个checker进去进行判断，这种方式就很像通过Collections.sort在对一个Hero集合排序，需要传一个[Comparator](https://how2j.cn/k/collection/collection-comparator-comparable/693.html#step828)的匿名类对象进去一样。`

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
   
import charactor.Hero;
   
public class TestLambda {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
        System.out.println("使用匿名类的方式，筛选出 hp>100 && damange<50的英雄");
        HeroChecker checker = new HeroChecker() {
            @Override
            public boolean test(Hero h) {
                return (h.hp>100 && h.damage<50);
            }
        };
           
        filter(heros,checker);
    }
   
    private static void filter(List<Hero> heros,HeroChecker checker) {
        for (Hero hero : heros) {
            if(checker.test(hero))
                System.out.print(hero);
        }
    }
   
}
```

## Lambda 方式

使用lambda筛选出

filter(heros,(h)->h.hp>100 && h.damage<50);

 同样是调用filter方法，从上一步的传递匿名类对象，变成了传递一个Lambda表达式进去

 h->h.hp>100 && h.damage<50

```java
import charactor.Hero;
 
public class TestLamdba {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
        System.out.println("使用Lamdba的方式，筛选出 hp>100 && damange<50的英雄");
        filter(heros,h->h.hp>100 && h.damage<50);
    }
 
    private static void filter(List<Hero> heros,HeroChecker checker) {
        for (Hero hero : heros) {
            if(checker.test(hero))
                System.out.print(hero);
        }
    }
 
}
```



## 从匿名类演变成Lambda表达式

1. 匿名类正常写法

```java
HeroChecker c1 = new HeroChecker() {
    public boolean test(Hero h) {
        return (h.hp>100 && h.damage<50);
    }
};
```

2. 把外面的壳子去掉
   只保留**方法参数**和**方法体**
   参数和方法体之间加上符号 **->**

```java
 
HeroChecker c2 = (Hero h) ->{
	return h.hp>100 && h.damage<50;
};
```

3. 把return和{}去掉

```java
HeroChecker c3 = (Hero h) ->h.hp>100 && h.damage<50;
```

4. 把 参数类型和圆括号去掉(只有一个参数的时候，才可以去掉圆括号)

```java
HeroChecker c4 = h ->h.hp>100 && h.damage<50;
```

5. 把c4作为参数传递进去

```java
 filter(heros,c4);
```

6. 直接把表达式传递进去

```java
filter(heros, h -> h.hp > 100 && h.damage < 50);
```

## 匿名方法

与[匿名类](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#step687) 概念相比较，
Lambda 其实就是**匿名方法**，这是一种**把方法作为参数**进行传递的编程思想。

虽然代码是这么写

```java
filter(heros, h -> h.hp > 100 && h.damage < 50);
```

但是，Java会在背后，悄悄的，把这些都还原成[匿名类方式](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#step2552)。
引入Lambda表达式，会使得代码更加紧凑，而不是各种接口和匿名类到处飞。

## 弊端

Lambda表达式虽然带来了代码的简洁，但是也有其局限性。
\1. 可读性差，与**啰嗦的**但是**清晰的**匿名类代码结构比较起来，Lambda表达式一旦变得比较长，就难以理解
\2. 不便于调试，很难在Lambda表达式中增加调试信息，比如日志
\3. 版本支持，Lambda表达式在JDK8版本中才开始支持，如果系统使用的是以前的版本，考虑系统的稳定性等原因，而不愿意升级，那么就无法使用。

Lambda比较适合用在简短的业务代码中，并不适合用在复杂的系统中，会加大维护成本。

# 方法引用

## 引用静态方法

首先为TestLambda添加一个静态方法：

```java
public static boolean testHero(Hero h) {
   return h.hp>100 && h.damage<50;
}
```

lambda

```java
filter(heros, h->h.hp>100 && h.damage<50);
```

在Lambda表达式中调用这个静态方法：

```java
filter(heros, h -> TestLambda.testHero(h) );
```

还可以写成

```java
filter(heros, TestLambda::testHero);
```

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
   
import charactor.Hero;
   
public class TestLambda {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
           
        HeroChecker c = new HeroChecker() {
            public boolean test(Hero h) {
                return h.hp>100 && h.damage<50;
            }
        };
          
        System.out.println("使用匿名类过滤");
        filter(heros, c);
        System.out.println("使用Lambda表达式");
        filter(heros, h->h.hp>100 && h.damage<50);
        System.out.println("在Lambda表达式中使用静态方法");
        filter(heros, h -> TestLambda.testHero(h) );
        System.out.println("直接引用静态方法");
        filter(heros, TestLambda::testHero);
    }
       
    public static boolean testHero(Hero h) {
        return h.hp>100 && h.damage<50;
    }
       
    private static void filter(List<Hero> heros, HeroChecker checker) {
        for (Hero hero : heros) {
            if (checker.test(hero))
                System.out.print(hero);
        }
    }
   
}
```

## 引用对象方法

与引用静态方法很类似，只是传递方法的时候，需要一个对象的存在

 ```java
TestLambda testLambda = new TestLambda();
filter(heros, testLambda::testHero);
 ```

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
 
public class TestLambda {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
     
        System.out.println("使用引用对象方法  的过滤结果：");
        //使用类的对象方法
        TestLambda testLambda = new TestLambda();
        filter(heros, testLambda::testHero);
    }
     
    public boolean testHero(Hero h) {
        return h.hp>100 && h.damage<50;
    }
     
    private static void filter(List<Hero> heros, HeroChecker checker) {
        for (Hero hero : heros) {
            if (checker.test(hero))
                System.out.print(hero);
        }
    }
 
}
```

## 引用构造器

有的接口中的方法会返回一个对象，比如**java.util.function.Supplier**提供
了一个get方法，返回一个对象。

```java
 public interface Supplier<T> {
    T get();
}
```

设计一个方法，参数是这个接口

```java
public static List getList(Supplier<List> s){
  return s.get();
}
```

为了调用这个方法，有3种方式
第一种匿名类：

```java
Supplier<List> s = new Supplier<List>() {
	public List get() {
		return new ArrayList();
	}
};
List list1 = getList(s);
```

第二种：Lambda表达式

```
List list2 = getList(()->new ArrayList());
```

第三种：引用构造器

```
List list3 = getList(ArrayList::new);
```



```java
import java.util.ArrayList;
import java.util.List;
import java.util.function.Supplier;
 
public class TestLambda {
    public static void main(String[] args) {
    Supplier<List> s = new Supplier<List>() {
        public List get() {
            return new ArrayList();
        }
    };
 
    //匿名类
    List list1 = getList(s);
     
    //Lambda表达式
    List list2 = getList(()->new ArrayList());
     
    //引用构造器
    List list3 = getList(ArrayList::new);
 
    }
     
    public static List getList(Supplier<List> s){
        return s.get();
    }
      
}
```

# 聚合操作

## 传统方式与聚合操作方式遍历数据

遍历数据的传统方式就是使用for循环，然后条件判断，最后打印出满足条件的数据

```java
for (Hero h : heros) {
   if (h.hp > 100 && h.damage < 50)
      System.out.println(h.name);
}
```

使用聚合操作方式，**画风**就发生了变化：

```java
heros
	.stream()
	.filter(h -> h.hp > 100 && h.damage < 50)
	.forEach(h -> System.out.println(h.name));
```



```java
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
 
public class TestAggregate {
 
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
 
        System.out.println("初始化后的集合：");
        System.out.println(heros);
        System.out.println("查询条件：hp>100 && damage<50");
        System.out.println("通过传统操作方式找出满足条件的数据：");
 
        for (Hero h : heros) {
            if (h.hp > 100 && h.damage < 50)
                System.out.println(h.name);
        }
 
        System.out.println("通过聚合操作方式找出满足条件的数据：");
        heros
            .stream()
            .filter(h -> h.hp > 100 && h.damage < 50)
            .forEach(h -> System.out.println(h.name));
 
    }
}
```

## Stream和管道的概念

```java
heros
	.stream()
	.filter(h -> h.hp > 100 && h.damage < 50)
	.forEach(h -> System.out.println(h.name));
```

要了解聚合操作，首先要建立**Stream**和**管道**的概念
**Stream** 和Collection结构化的数据不一样，Stream是一系列的元素，就像是生产线上的罐头一样，一串串的出来。
**管道**指的是一系列的聚合操作。

管道又分3个部分
**管道源**：在这个例子里，源是一个List
**中间操作**： 每个中间操作，又会返回一个Stream，比如.filter()又返回一个Stream, 中间操作是“懒”操作，并不会真正进行遍历。
**结束操作**：当这个操作执行后，流就被使用“光”了，无法再被操作。所以这必定是流的最后一个操作。 结束操作不会返回Stream，但是会返回int、float、String、 Collection或者像forEach，什么都不返回, 结束操作才进行真正的遍历行为，在遍历的时候，才会去进行中间操作的相关判断

**注：** 这个Stream和I/O章节的InputStream,OutputStream是不一样的概念。

## 管道源

把Collection切换成管道源很简单，调用stream()就行了。

heros.stream()
但是数组却没有stream()方法，需要使用

Arrays.stream(hs)
或者

 Stream.of(hs)

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
 
public class TestAggregate {
 
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        //管道源是集合
        heros
        .stream()
        .forEach(h->System.out.println(h.name));
         
        //管道源是数组
        Hero hs[] = heros.toArray(new Hero[heros.size()]);
        Arrays.stream(hs)
        .forEach(h->System.out.println(h.name));
         
    }
}
```

## 中间操作

每个中间操作，又会返回一个Stream，比如.filter()又返回一个Stream, 中间操作是“懒”操作，并不会真正进行遍历。
中间操作比较多，主要分两类
对元素进行筛选 和 转换为其他形式的流
**对元素进行筛选：**
filter 匹配
distinct 去除重复(根据equals判断)
sorted 自然排序
sorted(Comparator<T>) 指定排序
limit 保留
skip 忽略
**转换为其他形式的流**
mapToDouble 转换为double的流
map 转换为任意类型的流

```java
//Hero
public class Hero implements Comparable<Hero>{
    public String name;
    public float hp;
         
    public int damage;
         
    public Hero(){
            
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public float getHp() {
        return hp;
    }
    public void setHp(float hp) {
        this.hp = hp;
    }
    public int getDamage() {
        return damage;
    }
    public void setDamage(int damage) {
        this.damage = damage;
    }
    public Hero(String name) {
        this.name =name;
    }
    //初始化name,hp,damage的构造方法
    public Hero(String name,float hp, int damage) {
        this.name =name;
        this.hp = hp;
        this.damage = damage;
    }
    
    @Override
    public int compareTo(Hero anotherHero) {
        if(damage<anotherHero.damage)
            return 1; 
        else
            return -1;
    }
    
    @Override
    public String toString() {
        return "Hero [name=" + name + ", hp=" + hp + ", damage=" + damage + "]\r\n";
    }
        
}
```

```java
//TestAggregate
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
  
public class TestAggregate {
  
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        //制造一个重复数据
        heros.add(heros.get(0));
        System.out.println("初始化集合后的数据 (最后一个数据重复)：");
        System.out.println(heros);
        System.out.println("满足条件hp>100&&damage<50的数据");
          
        heros
            .stream()
            .filter(h->h.hp>100&&h.damage<50)
            .forEach(h->System.out.print(h));
          
        System.out.println("去除重复的数据，去除标准是看equals");
        heros
            .stream()
            .distinct()
            .forEach(h->System.out.print(h));
        System.out.println("按照血量排序");
        heros
            .stream()
            .sorted((h1,h2)->h1.hp>=h2.hp?1:-1)
            .forEach(h->System.out.print(h));
          
        System.out.println("保留3个");
        heros
            .stream()
            .limit(3)
            .forEach(h->System.out.print(h));
          
        System.out.println("忽略前3个");
        heros
            .stream()
            .skip(3)
            .forEach(h->System.out.print(h));
          
        System.out.println("转换为double的Stream");
        heros
            .stream()
            .mapToDouble(Hero::getHp)
            .forEach(h->System.out.println(h));
          
        System.out.println("转换任意类型的Stream");
        heros
            .stream()
            .map((h)-> h.name + " - " + h.hp + " - " + h.damage)
            .forEach(h->System.out.println(h));
          
    }
}
```

## 结束操作

当进行结束操作后，流就被使用“光”了，无法再被操作。所以这必定是流的最后一个操作。 结束操作不会返回Stream，但是会返回int、float、String、 Collection或者像forEach，什么都不返回,。
结束操作才真正进行遍历行为，前面的中间操作也在这个时候，才真正的执行。
常见结束操作如下：
**forEach()** 遍历每个元素
**toArray()** 转换为数组
**min(Comparator)** 取最小的元素
**max(Comparator)** 取最大的元素
**count()** 总数
**findFirst()** 第一个元素



```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Random;
 
import org.omg.Messaging.SYNC_WITH_TRANSPORT;
 
import charactor.Hero;
  
public class TestAggregate {
  
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("遍历集合中的每个数据");
        heros
            .stream()
            .forEach(h->System.out.print(h));
        System.out.println("返回一个数组");
        Object[] hs= heros
            .stream()
            .toArray();
        System.out.println(Arrays.toString(hs));
        System.out.println("返回伤害最低的那个英雄");
        Hero minDamageHero =
        heros
            .stream()
            .min((h1,h2)->h1.damage-h2.damage)
            .get();
        System.out.print(minDamageHero);
        System.out.println("返回伤害最高的那个英雄");
 
        Hero mxnDamageHero =
                heros
                .stream()
                .max((h1,h2)->h1.damage-h2.damage)
                .get();
        System.out.print(mxnDamageHero);     
         
        System.out.println("流中数据的总数");
        long count = heros
                .stream()
                .count();
        System.out.println(count);
 
        System.out.println("第一个英雄");
        Hero firstHero =
                heros
                .stream()
                .findFirst()
                .get();
         
        System.out.println(firstHero);
         
    }
}
```


