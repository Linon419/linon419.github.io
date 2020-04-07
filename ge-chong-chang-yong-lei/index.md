# 各种常用类



# 包装类

## 包装类的基本知识

  Java是面向对象的语言，但并不是“纯面向对象”的，因为我们经常用到的基本数据类型就不是对象。但是我们在实际应用中经常需要将基本数据转化成对象，以便于操作。比如：将基本数据类型存储到Object[]数组或集合中的操作等等。

<!-- more -->

   为了解决这个不足，Java在设计类时为每个基本数据类型设计了一个对应的类进行代表，这样八个和基本数据类型对应的类统称为包装类(Wrapper Class)。

![](https://linon419.github.io/post-images/1578551748273.png)

```java
public class WrapperClassTest {
    public static void main(String[] args) {
        Integer i = new Integer(10);
        Integer j = new Integer(50);
    }
}
```

![图8-3 示例8-1内存分析图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495593796672168.png)

## 包装类的用途

1. 作为和基本数据类型对应的类型存在，方便涉及到对象的操作，如Object[]、集合等的操作。

2. 包含每种基本数据类型的相关属性如最大值、最小值等，以及相关的操作方法(这些操作方法的作用是在基本数据类型、包装类对象、字符串之间提供相互之间的转化!)。

```java
public class Test {
    /** 测试Integer的用法，其他包装类与Integer类似 */
    void testInteger() {
        // 基本类型转化成Integer对象
        Integer int1 = new Integer(10);
        Integer int2 = Integer.valueOf(20); // 官方推荐这种写法
        // Integer对象转化成int
        int a = int1.intValue();
        // 字符串转化成Integer对象
        Integer int3 = Integer.parseInt("334");
        Integer int4 = new Integer("999");
        // Integer对象转化成字符串
        String str1 = int3.toString();
        // 一些常见int类型相关的常量
        System.out.println("int能表示的最大整数：" + Integer.MAX_VALUE); // 2147483674
    }
    public static void main(String[] args) {
        Test test  = new Test();
        test.testInteger();
    }
}
```

## 自动拆箱和自动装箱

   自动装箱和拆箱就是将基本数据类型和包装类之间进行自动的互相转换。JDK1.5后，Java引入了自动装箱(autoboxing)/拆箱(unboxing)。

### 自动装箱

基本类型的数据处于需要对象的环境中时，会自动转为“对象”。

   我们以Integer为例：在JDK1.5以前，这样的代码 Integer i = 5 是错误的，必须要通过Integer i = new Integer(5) 这样的语句来实现基本数据类型转换成包装类的过程;而在JDK1.5以后，Java提供了自动装箱的功能，因此只需Integer i = 5这样的语句就能实现基本数据类型转换成包装类，这是因为JVM为我们执行了Integer i = Integer.valueOf(5)这样的操作，这就是Java的自动装箱。

```java
Integer i = 100;//自动装箱
//相当于编译器自动为您作以下的语法编译：
Integer i = Integer.valueOf(100);//调用的是valueOf(100)，而不是new Integer(100)
```

### 自动拆箱

   每当需要一个值时，对象会自动转成基本数据类型，没必要再去显式调用intValue()、doubleValue()等转型方法。

   如 Integer i = 5;int j = i; 这样的过程就是自动拆箱。

   我们可以用一句话总结自动装箱/拆箱：

   自动装箱过程是通过调用包装类的valueOf()方法实现的，而自动拆箱过程是通过调用包装类的 xxxValue()方法实现的(xxx代表对应的基本数据类型，如intValue()、doubleValue()等)。

```java
Integer i = 100;
int j = i;//自动拆箱
//相当于编译器自动为您作以下的语法编译：
int j = i.intValue();
```

包装类空指针异常

```java
public class Test1 {
    public static void main(String[] args) {
        Integer i = null;
        int j = i;
    }
}//空指针异常
```

```java
public class Test1 {
    public static void main(String[] args) {
        //示例的代码在编译时期是合法的，但是在运行时期会有错误，因为其相当于：
        Integer i = null; 
        int j = i.intValue();         
    }
}
```

   null表示i没有指向任何对象的实体，但作为对象名称是合法的(不管这个对象名称存是否指向了某个对象的实体)。由于实际上i并没有指向任何对象的实体，所以也就不可能操作intValue()方法，这样上面的写法在运行时就会出现NullPointerException错误。

## 包装类的缓存处理

   整型、char类型所对应的包装类，在自动装箱时，对于-128~127之间的值会进行缓存处理，其目的是提高效率。

   缓存处理的原理为：如果数据在-128~127这个区间，那么在类加载时就已经为该区间的每个数值创建了对象，并将这256个对象存放到一个名为cache的数组中。每当自动装箱过程发生时(或者手动调用valueOf()时)，就会先判断数据是否在该区间，如果在则直接获取数组中对应的包装类对象的引用，如果不在该区间，则会通过new调用包装类的构造方法来创建对象。

   下面我们以Integer类为例

```java
public class Test3 {
    public static void main(String[] args) {
        Integer in1 = -128;
        Integer in2 = -128;
        System.out.println(in1 == in2);//true 因为123在缓存范围内
        System.out.println(in1.equals(in2));//true
        Integer in3 = 1234;
        Integer in4 = 1234;
        System.out.println(in3 == in4);//false 因为1234不在缓存范围内
        System.out.println(in3.equals(in4));//true
    }
}
```

# String类

   String类常用的方法有(可翻到第五章5.11.4查看，已讲过，此处不赘述)：

   \1. String类的下述方法能创建并返回一个新的String对象: concat()、 replace()、substring()、 toLowerCase()、 toUpperCase()、trim()。

   \2. 提供查找功能的有关方法: endsWith()、 startsWith()、 indexOf()、lastIndexOf()。

   \3. 提供比较功能的方法: equals()、equalsIgnoreCase()、compareTo()。

   \4. 其它方法: charAt() 、length()。

## StringBuffer, StringBuilder

StringBuffer和StringBuilder非常类似，均代表可变的字符序列。 这两个类都是抽象类AbstractStringBuilder的子类，方法几乎一模一样。

### 部分源码

```java
// AbstractStringBuilder
abstract class AbstractStringBuilder implements Appendable, CharSequence {
    /**
     * The value is used for character storage.
     */
    char value[];
//以下代码省略
}
```

   显然，内部也是一个字符数组，但这个字符数组没有用final修饰，随时可以修改。因此，StringBuilder和StringBuffer称之为“可变字符序列”。那两者有什么区别呢?

1. StringBuffer JDK1.0版本提供的类，线程安全，做线程同步检查， 效率较低。

2. StringBuilder JDK1.5版本提供的类，线程不安全，不做线程同步检查，因此效率较高。 建议采用该类。

## 常用方法列表

1. 重载的public StringBuilder append(…)方法

​    可以为该StringBuilder 对象添加字符序列，仍然返回自身对象。

2. 方法 public StringBuilder delete(int start,int end)

​    可以删除从start开始到end-1为止的一段字符序列，仍然返回自身对象。

3. 方法 public StringBuilder deleteCharAt(int index)

​    移除此序列指定位置上的 char，仍然返回自身对象。

4. 重载的public StringBuilder insert(…)方法

​    可以为该StringBuilder 对象在指定位置插入字符序列，仍然返回自身对象。

5. 方法 public StringBuilder reverse()

​    用于将字符序列逆序，仍然返回自身对象。

6. 方法 public String toString() 返回此序列中数据的字符串表示形式。

7. 和 String 类含义类似的方法：

```java
public int indexOf(String str)
public int indexOf(String str,int fromIndex)
public String substring(int start)
public String substring(int start,int end)
public int length() 
char charAt(int index)
```

## 基本用法

```java
public class TestStringBufferAndBuilder 1{
    public static void main(String[] args) {
        /**StringBuilder*/
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 7; i++) {
            sb.append((char) ('a' + i));//追加单个字符
        }
        System.out.println(sb.toString());//转换成String输出
        sb.append(", I can sing my abc!");//追加字符串
        System.out.println(sb.toString());
        /**StringBuffer*/
        StringBuffer sb2 = new StringBuffer("中华人民共和国");
        sb2.insert(0, "爱").insert(0, "我");//插入字符串
        System.out.println(sb2);
        sb2.delete(0, 2);//删除子字符串
        System.out.println(sb2);
        sb2.deleteCharAt(0).deleteCharAt(0);//删除某个字符
        System.out.println(sb2.charAt(0));//获取某个字符
        System.out.println(sb2.reverse());//字符串逆序
    }
}
```

## 可变字符串和不可变字符串使用陷阱

String一经初始化后，就不会再改变其内容了。对String字符串的操作实际上是对其副本(原始拷贝)的操作，原来的字符串一点都没有改变。比如：

   String s ="a"; 创建了一个字符串

   s = s+"b"; 实际上原来的"a"字符串对象已经丢弃了，现在又产生了另一个字符串s+"b"(也就是"ab")。 如果多次执行这些改变串内容的操作，会导致大量副本字符串对象存留在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序的时间和空间性能，甚至会造成服务器的崩溃。

   相反，StringBuilder和StringBuffer类是对原字符串本身操作的，可以对字符串进行修改而不产生副本拷贝或者产生少量的副本。因此可以在循环中使用。

```java
//效率测试
public class Test {
    public static void main(String[] args) {
        /**使用String进行字符串的拼接*/
        String str8 = "";
        //本质上使用StringBuilder拼接, 但是每次循环都会生成一个StringBuilder对象
        long num1 = Runtime.getRuntime().freeMemory();//获取系统剩余内存空间
        long time1 = System.currentTimeMillis();//获取系统的当前时间
        for (int i = 0; i < 5000; i++) {
            str8 = str8 + i;//相当于产生了10000个对象
        }
        long num2 = Runtime.getRuntime().freeMemory();
        long time2 = System.currentTimeMillis();
        System.out.println("String占用内存 : " + (num1 - num2));
        System.out.println("String占用时间 : " + (time2 - time1));
        /**使用StringBuilder进行字符串的拼接*/
        StringBuilder sb1 = new StringBuilder("");
        long num3 = Runtime.getRuntime().freeMemory();
        long time3 = System.currentTimeMillis();
        for (int i = 0; i < 5000; i++) {
            sb1.append(i);
        }
        long num4 = Runtime.getRuntime().freeMemory();
        long time4 = System.currentTimeMillis();
        System.out.println("StringBuilder占用内存 : " + (num3 - num4));
        System.out.println("StringBuilder占用时间 : " + (time4 - time3));
    }
}
```

![图8-12 示例8-13运行效果图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495607616300229.png)

1. String：不可变字符序列。

2. StringBuffer：可变字符序列，并且线程安全，但是效率低。

3. StringBuilder：可变字符序列，线程不安全，但是效率高(一般用它)。

## 时间处理相关类

在计算机世界，我们把1970 年 1 月 1 日 00:00:00定为基准时间，每个度量单位是毫秒(1秒的千分之一)

 我们用long类型的变量来表示时间，从基准时间往前几亿年，往后几亿年都能表示。如果想获得现在时刻的“时刻数值”，可以使用：

```java
long now = System.currentTimeMillis();
```



这个“时刻数值”是所有时间类的核心值，年月日都是根据这个“数值”计算出来的。我们工作学习涉及的时间相关类有如下这些：
![](https://linon419.github.io/post-images/1578551813619.png)

### 时间类

   \1. Date() 分配一个Date对象，并初始化此对象为系统当前的日期和时间，可以精确到毫秒)。

   \2. Date(long date) 分配 Date 对象并初始化此对象，以表示自从标准基准时间(称为“历元(epoch)”，即 1970 年 1 月 1 日 00:00:00 GMT)以来的指定毫秒数。

   \3. boolean after(Date when) 测试此日期是否在指定日期之后。

   \4. booleanbefore(Date when) 测试此日期是否在指定日期之前。

   \5. boolean equals(Object obj) 比较两个日期的相等性。

   \6. long getTime() 返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数。

   \7. String toString() 把此 Date 对象转换为以下形式的 String：

​    dow mon dd hh:mm:ss zzz yyyy 其中： dow 是一周中的某一天 (Sun、 Mon、Tue、Wed、 Thu、 Fri、 Sat)。

```java
import java.util.Date;
public class TestDate {
    public static void main(String[] args) {
        Date date1 = new Date();
        System.out.println(date1.toString());
        long i = date1.getTime();
        Date date2 = new Date(i - 1000);
        Date date3 = new Date(i + 1000);
        System.out.println(date1.after(date2));
        System.out.println(date1.before(date2));
        System.out.println(date1.equals(date2));
        System.out.println(date1.after(date3));
        System.out.println(date1.before(date3));
        System.out.println(date1.equals(date3));
        System.out.println(new Date(1000L * 60 * 60 * 24 * 365 * 39L).toString());
    }
}
```



![图8-15 示例8-14运行效果图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495608258449100.png)

### Data format 类

**·DateFormat类的作用**

   把时间对象转化成指定格式的字符串。反之，把指定格式的字符串转化成时间对象。

   DateFormat是一个抽象类，一般使用它的的子类SimpleDateFormat类来实现。

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
public class TestDateFormat {
    public static void main(String[] args) throws ParseException {
        // new出SimpleDateFormat对象
        SimpleDateFormat s1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
        SimpleDateFormat s2 = new SimpleDateFormat("yyyy-MM-dd");
        // 将时间对象转换成字符串
        String daytime = s1.format(new Date());
        System.out.println(daytime);
        System.out.println(s2.format(new Date()));
        System.out.println(new SimpleDateFormat("hh:mm:ss").format(new Date()));
        // 将符合指定格式的字符串转成成时间对象.字符串格式需要和指定格式一致。
        String time = "2007-10-7";
        Date date = s2.parse(time);
        System.out.println("date1: " + date);
        time = "2007-10-7 20:15:30";
        date = s1.parse(time);
        System.out.println("date2: " + date);
    }
}
```

![图8-16 示例8-15运行效果图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495608746205492.png)

### Calendar类

  Calendar 类是一个抽象类，为我们提供了关于日期计算的相关功能，比如：年、月、日、时、分、秒的展示和计算。

   GregorianCalendar 是 Calendar 的一个具体子类，提供了世界上大多数国家/地区使用的标准日历系统。

 注意月份的表示，一月是0，二月是1，以此类推，12月是11。 因为大多数人习惯于使用单词而不是使用数字来表示月份，这样程序也许更易读，父类Calendar使用常量来表示月份：JANUARY、FEBRUARY等等。

```java
import java.util.*;
public class TestCalendar {
    public static void main(String[] args) {
        // 得到相关日期元素
        GregorianCalendar calendar = new GregorianCalendar(2999, 10, 9, 22, 10, 50);
        int year = calendar.get(Calendar.YEAR); // 打印：1999
        int month = calendar.get(Calendar.MONTH); // 打印：10
        int day = calendar.get(Calendar.DAY_OF_MONTH); // 打印：9
        int day2 = calendar.get(Calendar.DATE); // 打印：9
        // 日：Calendar.DATE和Calendar.DAY_OF_MONTH同义
        int date = calendar.get(Calendar.DAY_OF_WEEK); // 打印：3
        // 星期几 这里是：1-7.周日是1，周一是2，。。。周六是7
        System.out.println(year);
        System.out.println(month);
        System.out.println(day);
        System.out.println(day2);
        System.out.println(date);
        // 设置日期
        GregorianCalendar calendar2 = new GregorianCalendar();
        calendar2.set(Calendar.YEAR, 2999);
        calendar2.set(Calendar.MONTH, Calendar.FEBRUARY); // 月份数：0-11
        calendar2.set(Calendar.DATE, 3);
        calendar2.set(Calendar.HOUR_OF_DAY, 10);
        calendar2.set(Calendar.MINUTE, 20);
        calendar2.set(Calendar.SECOND, 23);
        printCalendar(calendar2);
        // 日期计算
        GregorianCalendar calendar3 = new GregorianCalendar(2999, 10, 9, 22, 10, 50);
        calendar3.add(Calendar.MONTH, -7); // 月份减7
        calendar3.add(Calendar.DATE, 7); // 增加7天
        printCalendar(calendar3);
        // 日历对象和时间对象转化
        Date d = calendar3.getTime();
        GregorianCalendar calendar4 = new GregorianCalendar();
        calendar4.setTime(new Date());
        long g = System.currentTimeMillis();
    }
    static void printCalendar(Calendar calendar) {
        int year = calendar.get(Calendar.YEAR);
        int month = calendar.get(Calendar.MONTH) + 1;
        int day = calendar.get(Calendar.DAY_OF_MONTH);
        int date = calendar.get(Calendar.DAY_OF_WEEK) - 1; // 星期几
        String week = "" + ((date == 0) ? "日" : date);
        int hour = calendar.get(Calendar.HOUR);
        int minute = calendar.get(Calendar.MINUTE);
        int second = calendar.get(Calendar.SECOND);
        System.out.printf("%d年%d月%d日,星期%s %d:%d:%d\n", year, month, day,  
                        week, hour, minute, second);
    }
}
```



```java
【示例8-18】可视化日历的编写

import java.text.ParseException;
import java.util.Calendar;
import java.util.GregorianCalendar;
import java.util.Scanner;
public class TestCalendar2 {
    public static void main(String[] args) throws ParseException {
        System.out.println("请输入日期（格式为：2010-3-3）：");
        Scanner scanner = new Scanner(System.in);
        String dateString = scanner.nextLine(); // 2010-3-1
        // 将输入的字符串转化成日期类
        System.out.println("您刚刚输入的日期是：" + dateString);
        String[] str = dateString.split("-");
        int year = Integer.parseInt(str[0]);
        int month = new Integer(str[1]);
        int day = new Integer(str[2]);
        Calendar c = new GregorianCalendar(year, month - 1, day); // Month:0-11
        // 大家自己补充另一种方式：将字符串通过SImpleDateFormat转化成Date对象，
        //再将Date对象转化成日期类
        // SimpleDateFormat sdfDateFormat = new SimpleDateFormat("yyyy-MM-dd");
        // Date date = sdfDateFormat.parse(dateString);
        // Calendar c = new GregorianCalendar();
        // c.setTime(date);
        // int day = c.get(Calendar.DATE);
        c.set(Calendar.DATE, 1);
        int dow = c.get(Calendar.DAY_OF_WEEK); // week:1-7 日一二三四五六
        System.out.println("日\t一\t二\t三\t四\t五\t六");
        for (int i = 0; i < dow - 1; i++) {
            System.out.print("\t");
        }
        int maxDate = c.getActualMaximum(Calendar.DATE);
        // System.out.println("maxDate:"+maxDate);
        for (int i = 1; i <= maxDate; i++) {
            StringBuilder sBuilder = new StringBuilder();
            if (c.get(Calendar.DATE) == day) {
                sBuilder.append(c.get(Calendar.DATE) + "*\t");
            } else {
                sBuilder.append(c.get(Calendar.DATE) + "\t");
            }
            System.out.print(sBuilder);
            // System.out.print(c.get(Calendar.DATE)+
            //                ((c.get(Calendar.DATE)==day)?"*":"")+"\t");
 
            if (c.get(Calendar.DAY_OF_WEEK) == Calendar.SATURDAY) {
                System.out.print("\n");
            }
            c.add(Calendar.DATE, 1);
        }
    }
}
```

## Math类

  java.lang.Math提供了一系列静态方法用于科学计算;其方法的参数和返回值类型一般为double型。如果需要更加强大的数学运算能力，计算高等数学中的相关内容，可以使用apache commons下面的Math类库。

**Math类的常用方法：**

   1. abs 绝对值

   2. acos,asin,atan,cos,sin,tan 三角函数

   3. sqrt 平方根

   4. pow(double a, double b) a的b次幂

   5. max(double a, double b) 取大值

   6. min(double a, double b) 取小值

   7. ceil(double a) 大于a的最小整数

   8. floor(double a) 小于a的最大整数

   9. random() 返回 0.0 到 1.0 的随机数

   10. long round(double a) double型的数据a转换为long型(四舍五入)

   11. toDegrees(double angrad) 弧度->角度

   12. toRadians(double angdeg) 角度->弧度



## 递归

本节结合前面给大家讲的递归算法，展示目录结构。大家可以先建立一个目录，下面增加几个子文件夹或者文件，用于测试。

**【示例8-26】使用递归算法，以树状结构展示目录树**

```java
import java.io.File;
public class TestFile6 {
    public static void main(String[] args) {
        File f = new File("d:/电影");
        printFile(f, 0);
    }
    /**
     * 打印文件信息
     * @param file 文件名称
     * @param level 层次数(实际就是：第几次递归调用)
     */
    static void printFile(File file, int level) {
        //输出层次数
        for (int i = 0; i < level; i++) {
            System.out.print("-");
        }
        //输出文件名
        System.out.println(file.getName());
        //如果file是目录，则获取子文件列表，并对每个子文件进行相同的操作
        if (file.isDirectory()) {
            File[] files = file.listFiles();
            for (File temp : files) {
                //递归调用该方法：注意等+1
                printFile(temp, level + 1);
            }
        }
    }
}

```
