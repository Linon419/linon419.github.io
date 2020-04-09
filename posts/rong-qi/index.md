# 容器

容器，也叫集合(Collection)。


![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391121859.png)
<!-- more -->

# 泛型

泛型是JDK1.5以后增加的，它可以帮助我们建立类型安全的集合。在使用了泛型的集合中，遍历时不必进行强制类型转换。JDK提供了支持泛型的编译器，将运行时的类型检查提前到了编译时执行，提高了代码可读性和安全性。

   泛型的本质就是“数据类型的参数化”。 我们可以把“泛型”理解为数据类型的一个占位符(形式参数)，即告诉编译器，在调用泛型时必须传入实际类型。

## 自定义泛型

我们可以在类的声明处增加泛型列表，如：<T,E,V>。

   此处，字符可以是任何标识符，一般采用这3个字母。

-- 泛型类声明

```java
//  泛型E像一个占位符一样表示“未知的某个数据类型”，我们在真正调用的时候传入这个“数据类型”。
class MyCollection<E> { //E表示泛型
	Object[] obj = new Object[5];
  
  public E get(int index){
  	return E obj[index]; 
  }
  
  public void set(E e, int index){
    
  }
}
```

-- 应用

```java
public class Demo{
  public static void main(String[] args){
    MyCollection<String> mc = new MyCollection<String>();
    mc.set("Hello",0);
    mc.set(" World",1);
    String str = mc(1);
    System.out.println(str);
  }
}
```

## 容器中使用泛型-List

```java
public class Demo{
  public static void main(String[] args){
    List<String> ls = new ArrayList<String>();
    Set<Man> mans = new HashSet<Man>();
    
  }
}
```

通过阅读源码，我们发现Collection、List、Set、Map、Iterator接口都定义了泛型，如下图所示：
![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391228648.png)
# Collection

Collection 表示一组对象，它是集中、收集的意思。Collection接口的两个子接口是List、Set接口。

![表9-1 Collection接口中定义的方法.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495614959696503.png)

由于List、Set是Collection的子接口，意味着所有List、Set的实现类都有上面的方法。我们下一节中，通过ArrayList实现类来测试上面的方法。

## List常用方法

List是有序、可重复的容器。

   **有序：**List中每个元素都有索引标记。可以根据元素的索引标记(在List中的位置)访问元素，从而精确控制这些元素。

   **可重复：**List允许加入重复的元素。更确切地讲，List通常允许满足 e1.equals(e2) 的元素重复加入容器。

   除了Collection接口中的方法，List多了一些跟顺序(索引)有关的方法，参见下表：

![表9-2 List接口中定义的方法.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495616109914665.png)

List接口常用的实现类有3个：ArrayList、LinkedList和Vector

```java
//list 常用方法
public class TestList {
    public static void main(String[] args) {
        List<String> ls = new ArrayList<String>();
        ls.add("Yang");
        System.out.println(ls.isEmpty());
        ls.add("Love");
        ls.add("Yi jie");
        System.out.println(ls);
        System.out.println("-----------------------");
        System.out.println("list 的大小"+ls.size());
        System.out.println("是否包含某元素"+ls.contains("Yang"));


    }
}

```

```java
//两个List之间的元素处理
import java.util.ArrayList;
import java.util.List;

public class TestList02 {
    public static void main(String[] args) {
        List<String> ls = new ArrayList<>();
        ls.add("Yang");
        ls.add("Li");
        ls.add("China");

        List<String> ls2 = new ArrayList<>();
        ls2.add("Jenny");
        ls2.add("Pey");
        ls2.add("China");

        System.out.println(ls.containsAll(ls2));//list是否包含list2中所有元素
        ls.addAll(ls2); //将list2中所有元素都添加到list中
        System.out.println(ls);
        ls.removeAll(ls2);//从list中删除同时在list和list2中存在的元素
        System.out.println(ls);
        ls.retainAll(ls2);//取list和list2的交集
        System.out.println(ls);


    }
}
```

```java
public class TestList {
    public static void main(String[] args) {
        test03();
    }
    /**
     * 测试List中关于索引操作的方法
     */
    public static void test03() {
        List<String> list = new ArrayList<String>();
        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
        System.out.println(list); // [A, B, C, D]
        list.add(2, "高");
        System.out.println(list); // [A, B, 高, C, D]
        list.remove(2);
        System.out.println(list); // [A, B, C, D]
        list.set(2, "c");
        System.out.println(list); // [A, B, c, D]
        System.out.println(list.get(1)); // 返回：B
        list.add("B");
        System.out.println(list); // [A, B, c, D, B]
        System.out.println(list.indexOf("B")); // 1 从头到尾找到第一个"B"
        System.out.println(list.lastIndexOf("B")); // 4 从尾到头找到第一个"B"
    }
}
```

## ArrayList特点及底层实现

ArrayList底层是用数组实现的存储。 特点：查询效率高，增删效率低，线程不安全。我们一般使用它。查看源码：

![图9-6 ArrayList底层源码(/Volumes/Untitled 1/笔记/Java/img/arraylist底层源码.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495616601500147.png)

我们可以看出ArrayList底层使用Object数组来存储元素数据。所有的方法，都围绕这个核心的Object数组来开展。

   我们知道，数组长度是有限的，而ArrayList是可以存放任意数量的对象，长度不受限制，那么它是怎么实现的呢?本质上就是通过定义新的更大的数组，将旧数组中的内容拷贝到新数组，来实现扩容。 ArrayList的Object数组初始化长度为10，如果我们存储满了这个数组，需要存储第11个对象，就会定义新的长度更大的数组，并将原数组内容和新的元素一起加入到新数组中，源码如下：

![图9-7 ArrayList底层源码(/Volumes/Untitled 1/笔记/Java/img/arraylist底层源码2.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495616624527034.png)

## **LinkedList特点和底层实现**

LinkedList底层用双向链表实现的存储。特点：查询效率低，增删效率高，线程不安全。

   双向链表也叫双链表，是链表的一种，它的每个数据节点中都有两个指针，分别指向前一个节点和后一个节点。 所以，从双向链表中的任意一个节点开始，都可以很方便地找到所有节点。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391270038.png)![图9-8 LinkedList的存储结构图.png](/Volumes/Untitled 1/笔记/Java/img/LinkedList存储结构图.png)

 每个节点都应该有3部分内容：

```java
class Node {
  Node  previous;     //前一个节点
  Object  element;    //本节点保存的数据
  Node  next;         //后一个节点
}
```

我们查看LinkedList的源码，可以看到里面包含了双向链表的相关代码：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391282165.png)![图9-9 LinkedList的底层源码.png](/Volumes/Untitled 1/笔记/Java/img/LinkedList的底层源码.png)

**注意事项**

   entry在英文中表示“进入、词条、条目”的意思。在计算机英语中一般表示“项、条目”的含义。

## **Vector向量**

Vector底层是用数组实现的List，相关的方法都加了同步检查，因此“线程安全,效率低”。 比如，indexOf方法就增加了synchronized同步标记。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391294925.png)
 ## 如何选用ArrayList、LinkedList、Vector?



1. 需要线程安全时，用Vector。

2. 不存在线程安全问题时，并且查找较多用ArrayList(一般使用它)。

   1. 不存在线程安全问题时，增加或删除元素较多用LinkedList。

# Map接口

Map就是用来存储“键(key)-值(value) 对”的。 Map类中存储的“键值对”通过键来标识，所以“键对象”不能重复。

   Map 接口的实现类有HashMap、TreeMap、HashTable、Properties等。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391308034.png)
## **HashMap和HashTable**

HashMap采用哈希算法实现，是Map接口最常用的实现类。 由于底层采用了哈希表存储数据，我们要求键不能重复，如果发生重复，新的键值对会替换旧的键值对。 HashMap在查找、删除、修改方面都有非常高的效率。

## Map接口中常用方法

```java
public class TestMap {
    public static void main(String[] args) {
        Map<Integer, String> m1 = new HashMap<Integer, String>();
        Map<Integer, String> m2 = new HashMap<Integer, String>();
        m1.put(1, "one");
        m1.put(2, "two");
        m1.put(3, "three");
        m2.put(1, "一");
        m2.put(2, "二");
        System.out.println(m1.size());
        System.out.println(m1.containsKey(1));
        System.out.println(m2.containsValue("two"));
        m1.put(3, "third"); //键重复了，则会替换旧的键值对
        Map<Integer, String> m3 = new HashMap<Integer, String>();
        m3.putAll(m1);
        m3.putAll(m2);
        System.out.println("m1:" + m1);
        System.out.println("m2:" + m2);
        System.out.println("m3:" + m3);
    }
}
```

  HashTable类和HashMap用法几乎一样，底层实现几乎一样，只不过HashTable的方法添加了synchronized关键字确保线程同步检查，效率较低。

**HashMap与HashTable的区别**

   \1. HashMap: 线程不安全，效率高。允许key或value为null。

   \2. HashTable: 线程安全，效率低。不允许key或value为null。

## HashMap底层实现

 HashMap底层实现采用了哈希表，这是一种非常重要的数据结构。对于我们以后理解很多技术都非常有帮助(比如：redis数据库的核心技术和HashMap一样)，因此，非常有必要让大家理解。

   数据结构中由数组和链表来实现对数据的存储，他们各有特点。

   (1) 数组：占用空间连续。 寻址容易，查询速度快。但是，增加和删除效率非常低。

   (2) 链表：占用空间不连续。 寻址困难，查询速度慢。但是，增加和删除效率非常高。

   那么，我们能不能结合数组和链表的优点(即查询快，增删效率也高)呢? 答案就是“哈希表”。 哈希表的本质就是“数组+链表”。

 **Hashmap基本结构讲解**

   哈希表的基本结构就是“数组+链表”。我们打开HashMap源码，发现有如下两个核心内容：

![图9-12 HashMap底层源码(/Volumes/Untitled 1/笔记/Java/img/HashMap底层源码1.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495618960152437.png)

其中的Entry[] table 就是HashMap的核心数组结构，我们也称之为“位桶数组”。我们再继续看Entry是什么，源码如下

：![图9-13 HashMap底层源码(/Volumes/Untitled 1/笔记/Java/img/HashMap底层源码2.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170524/1495619012687826.png)

 一个Entry对象存储了：

   \1. key：键对象 value：值对象

   \2. next:下一个节点

   \3. hash: 键对象的hash值

   显然每一个Entry对象就是一个单向链表结构，我们使用图形表示一个Entry对象的典型示意：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391497238.png)
然后，我们画出Entry[]数组的结构(这也是HashMap的结构)：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391477859.png)

**▪ 存储数据过程put(key,value)**

   明白了HashMap的基本结构后，我们继续深入学习HashMap如何存储数据。此处的核心是如何产生hash值，该值用来对应数组的存储位置。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391513823.png)![图9-16 HashMap存储数据过程示意图.png](/Volumes/Untitled 1/笔记/Java/img/HashMap存储数据结构图.png)

我们的目的是将”key-value两个对象”成对存放到HashMap的Entry[]数组中。参见以下步骤：

   (1) 获得key对象的hashcode

​      首先调用key对象的hashcode()方法，获得hashcode。

   (2) 根据hashcode计算出hash值(要求在[0, 数组长度-1]区间)

​      hashcode是一个整数，我们需要将它转化成[0, 数组长度-1]的范围。我们要求转化后的hash值尽量均匀地分布在[0,数组长度-1]这个区间，减少“hash冲突”

​      i. 一种极端简单和低下的算法是：

​      hash值 = hashcode/hashcode;

​      也就是说，hash值总是1。意味着，键值对对象都会存储到数组索引1位置，这样就形成一个非常长的链表。相当于每存储一个对象都会发生“hash冲突”，HashMap也退化成了一个“链表”。

​      ii. 一种简单和常用的算法是(相除取余算法)：

​      hash值 = hashcode%数组长度

​      这种算法可以让hash值均匀的分布在[0,数组长度-1]的区间。 早期的HashTable就是采用这种算法。但是，这种算法由于使用了“除法”，效率低下。JDK后来改进了算法。首先约定数组长度必须为2的整数幂，这样采用位运算即可实现取余的效果：hash值 = hashcode&(数组长度-1)。

当添加一个元素(key-value)时，首先计算key的hash值，以此确定插入数组中的位置，但是可能存在同一hash值的元素已经被放在数组同一位置了，这时就添加到同一hash值的元素的后面，他们在数组的同一位置，就形成了链表，同一个链表上的Hash值是相同的，所以说数组存放的是链表。 JDK8中，当链表长度大于8时，链表就转换为红黑树，这样又大大提高了查找的效率。

**▪ 取数据过程get(key)**

   我们需要通过key对象获得“键值对”对象，进而返回value对象。明白了存储数据过程，取数据就比较简单了，参见以下步骤：

   (1) 获得key的hashcode，通过hash()散列算法得到hash值，进而定位到数组的位置。

   (2) 在链表上挨个比较key对象。 调用equals()方法，将key对象和链表上所有节点的key对象进行比较，直到碰到返回true的节点对象为止。

   (3) 返回equals()为true的节点对象的value对象。

   明白了存取数据的过程，我们再来看一下hashcode()和equals方法的关系：

   Java中规定，两个内容相同(equals()为true)的对象必须具有相等的hashCode。因为如果equals()为true而两个对象的hashcode不同;那在整个存储过程中就发生了悖论。

**▪ 扩容问题**

   HashMap的位桶数组，初始大小为16。实际使用时，显然大小是可变的。如果位桶数组中的元素达到(0.75*数组 length)， 就重新调整数组大小变为原来2倍大小。

   扩容很耗时。扩容的本质是定义新的更大的数组，并将旧数组内容挨个拷贝到新数组中。

**▪ JDK8将链表在大于8情况下变为红黑二叉树**

   JDK8中，HashMap在存储一个元素时，当对应链表长度大于8时，链表就转换为红黑树，这样又大大提高了查找的效率。

## 二叉树和红黑树

**二叉树的定义**

   二叉树是树形结构的一个重要类型。 许多实际问题抽象出来的数据结构往往是二叉树的形式，即使是一般的树也能简单地转换为二叉树，而且二叉树的存储结构及其算法都较为简单，因此二叉树显得特别重要。

   二叉树(BinaryTree)由一个节点及两棵互不相交的、分别称作这个根的左子树和右子树的二叉树组成。下图中展现了五种不同基本形态的二叉树。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391532411.png)
   (a) 为空树。

   (b) 为仅有一个结点的二叉树。

   (c) 是仅有左子树而右子树为空的二叉树。

   (d) 是仅有右子树而左子树为空的二叉树。

   (e) 是左、右子树均非空的二叉树。

**注意事项**

   二叉树的左子树和右子树是严格区分并且不能随意颠倒的，图 (c) 与图 (d) 就是两棵不同的二叉树。

**排序二叉树特性如下：**

   (1) 左子树上所有节点的值均小于它的根节点的值。

   (2) 右子树上所有节点的值均大于它的根节点的值。

   比如：我们要将数据【14,12,23,4,16,13, 8,,3】存储到排序二叉树中，如下图所示：

![图9-19 排序二叉树示意图(/Volumes/Untitled 1/笔记/Java/img/排序二叉树示意图1.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170525/1495693833134742.png)

   排序二叉树本身实现了排序功能，可以快速检索。但如果插入的节点集本身就是有序的，要么是由小到大排列，要么是由大到小排列，那么最后得到的排序二叉树将变成普通的链表，其检索效率就会很差。 比如上面的数据【14,12,23,4,16,13, 8,,3】，我们先进行排序变成：【3,4,8,12,13,14,16,23】，然后存储到排序二叉树中，显然就变成了链表，如下图所示：

![图9-20 排序二叉树示意图(/Volumes/Untitled 1/笔记/Java/img/排序二叉树2.png).png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170525/1495693873605004.png)

**▪ 平衡二叉树(AVL)**

   为了避免出现上述一边倒的存储，科学家提出了“平衡二叉树”。

   在平衡二叉树中任何节点的两个子树的高度最大差别为1，所以它也被称为高度平衡树。 增加和删除节点可能需要通过一次或多次树旋转来重新平衡这个树。

   节点的平衡因子是它的左子树的高度减去它的右子树的高度(有时相反)。带有平衡因子1、0或 -1的节点被认为是平衡的。带有平衡因子 -2或2的节点被认为是不平衡的，并需要重新平衡这个树。

   比如，我们存储排好序的数据【3,4,8,12,13,14,16,23】，增加节点如果出现不平衡，则通过节点的左旋或右旋，重新平衡树结构，最终平衡二叉树如下图所示：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391558980.png)
平衡二叉树追求绝对平衡，实现起来比较麻烦，每次插入新节点需要做的旋转操作次数不能预知。

**▪ 红黑二叉树**

   红黑二叉树(简称：红黑树)，它首先是一棵二叉树，同时也是一棵自平衡的排序二叉树。

   红黑树在原有的排序二叉树增加了如下几个要求：

   \1. 每个节点要么是红色，要么是黑色。

   \2. 根节点永远是黑色的。

   \3. 所有的叶节点都是空节点(即 null)，并且是黑色的。

   \4. 每个红色节点的两个子节点都是黑色。(从每个叶子到根的路径上不会有两个连续的红色节点)

   \5. 从任一节点到其子树中每个叶子节点的路径都包含相同数量的黑色节点。

   这些约束强化了红黑树的关键性质：从根到叶子的最长的可能路径不多于最短的可能路径的两倍长。这样就让树大致上是平衡的。

   红黑树是一个更高效的检索二叉树，JDK 提供的集合类 TreeMap、TreeSet 本身就是一个红黑树的实现。

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391589220.png)

## **TreeMap的使用和底层实现**

 TreeMap是红黑二叉树的典型实现。我们打开TreeMap的源码，发现里面有一行核心代码：

```java
private transient Entry<K,V> root = null;
```

root用来存储整个树的根节点。我们继续跟踪Entry(是TreeMap的内部类)的代码：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391603878.png)

可以看到里面存储了本身数据、左节点、右节点、父节点、以及节点颜色。 TreeMap的put()/remove()方法大量使用了红黑树的理论。本书限于篇幅，不再展开。需要了解更深入的，可以参考专门的数据结构书籍。

   TreeMap和HashMap实现了同样的接口Map，因此，用法对于调用者来说没有区别。HashMap效率高于TreeMap;在需要排序的Map时才选用TreeMap。

# **Set接口**

Set接口继承自Collection，Set接口中没有新增方法，方法和Collection保持完全一致。我们在前面通过List学习的方法，在Set中仍然适用。因此，学习Set的使用将没有任何难度。

   Set容器特点：无序、不可重复。无序指Set中的元素没有索引，我们只能遍历查找;不可重复指不允许加入重复的元素。更确切地讲，新元素如果和Set中某个元素通过equals()方法对比为true，则不能加入;甚至，Set中也只能放入一个null元素，不能多个。

   Set常用的实现类有：HashSet、TreeSet等，我们一般使用HashSet。

## **HashSet基本使用**

Set是无序、不可重复

```java
import java.util.HashSet;
import java.util.Set;

public class TestHashMap {
  public static void main(String[] args) {
    Set<String> s = new HashSet<String>();
    s.add("I");
    s.add("Love");
    s.add("Jenny");
    System.out.println(s);//[Love, I, Jenny]
		s.add("I");
    System.out.println(s);//[Love, I, Jenny]
    s.add(null);
		System.out.println(s);// [null, Love, I, Jenny]

  }
}

```

## **HashSet底层实现**

HashSet是采用哈希算法实现，底层实际是用HashMap实现的(HashSet本质就是一个简化版的HashMap)，因此，查询效率和增删效率都比较高。我们来看一下HashSet的源码：

![](https://raw.githubusercontent.com/Linon419/Img/master/post-images/1579391625044.png)

我们发现里面有个map属性，这就是HashSet的核心秘密。我们再看add()方法，发现增加一个元素说白了就是在map中增加一个键值对，键对象就是这个元素，值对象是名为PRESENT的Object对象。说白了，就是“往set中加入元素，本质就是把这个元素作为key加入到了内部的map中”。

   由于map中key都是不可重复的，因此，Set天然具有“不可重复”的特性。

## **TreeSet的使用和底层实现**

TreeSet底层实际是用TreeMap实现的，内部维持了一个简化版的TreeMap，通过key来存储Set的元素。 TreeSet内部需要对存储的元素进行排序，因此，我们对应的类需要实现Comparable接口。这样，才能根据compareTo()方法比较对象之间的大小，才能进行内部排序。

**TreeSet和Comparable接口的使用**

```java
public class Test {
    public static void main(String[] args) {
        User u1 = new User(1001, "高淇", 18);
        User u2 = new User(2001, "高希希", 5);
        Set<User> set = new TreeSet<User>();
        set.add(u1);
        set.add(u2);
    }
}
 
class User implements Comparable<User> {
    int id;
    String uname;
    int age;
 
    public User(int id, String uname, int age) {
        this.id = id;
        this.uname = uname;
        this.age = age;
    }
    /**
     * 返回0 表示 this == obj 返回正数表示 this > obj 返回负数表示 this < obj
     */
    @Override
    public int compareTo(User o) {
        if (this.id > o.id) {
            return 1;
        } else if (this.id < o.id) {
            return -1;
        } else {
            return 0;
        }
    }
}
```

**使用TreeSet要点：**

   (1) 由于是二叉树，需要对元素做内部排序。 如果要放入TreeSet中的类没有实现Comparable接口，则会抛出异常：java.lang.ClassCastException。

   (2) TreeSet中不能放入null元素。

# **使用Iterator迭代器遍历容器元素(List/Set/Map)**

**迭代器遍历List**

```java
public class Test {
    public static void main(String[] args) {
        List<String> aList = new ArrayList<String>();
        for (int i = 0; i < 5; i++) {
            aList.add("a" + i);
        }
        System.out.println(aList);
        for (Iterator<String> iter = aList.iterator(); iter.hasNext();) {
            String temp = iter.next();
            System.out.print(temp + "\t");
            if (temp.endsWith("3")) {// 删除3结尾的字符串
                iter.remove();
            }
        }
        System.out.println();
        System.out.println(aList);
    }
}
```

![图9-27示例9-11运行效果图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170525/1495698648334893.png)

**迭代器遍历Set**

```java
public class Test {
    public static void main(String[] args) {
        Set<String> set = new HashSet<String>();
        for (int i = 0; i < 5; i++) {
            set.add("a" + i);
        }
        System.out.println(set);
        for (Iterator<String> iter = set.iterator(); iter.hasNext();) {
            String temp = iter.next();
            System.out.print(temp + "\t");
        }
        System.out.println();
        System.out.println(set);
    }
}
```

![图9-28示例9-12运行效果图.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170525/1495698749486697.png)

**迭代器遍历Map一**

```java
public class Test {
    public static void main(String[] args) {
        Map<String, String> map = new HashMap<String, String>();
        map.put("A", "高淇");
        map.put("B", "高小七");
        Set<Entry<String, String>> ss = map.entrySet();
        for (Iterator<Entry<String, String>> iterator = ss.iterator(); iterator.hasNext();) {
            Entry<String, String> e = iterator.next();
            System.out.println(e.getKey() + "--" + e.getValue());
        }
    }
}
```

**迭代器遍历Map二**

```java
public class Test {
    public static void main(String[] args) {
        Map<String, String> map = new HashMap<String, String>();
        map.put("A", "高淇");
        map.put("B", "高小七");
        Set<String> ss = map.keySet();
        for (Iterator<String> iterator = ss.iterator(); iterator.hasNext();) {
            String key = iterator.next();
            System.out.println(key + "--" + map.get(key));
        }
    }
}
```

# **遍历集合的方法总结**

**遍历List方法一：普通for循环**

```java
for(int i=0;i<list.size();i++){//list为集合的对象名
    String temp = (String)list.get(i);
    System.out.println(temp);
}
```

**遍历List方法二：增强for循环(使用泛型!)**

```java
for (String temp : list) {
System.out.println(temp);
}
```

**遍历List方法三：使用Iterator迭代器(1)**

```java
for(Iterator iter= list.iterator();iter.hasNext();){
    String temp = (String)iter.next();
    System.out.println(temp);
}
```

**遍历List方法四：使用Iterator迭代器(2)**

```java
Iterator  iter =list.iterator();
while(iter.hasNext()){
    Object  obj =  iter.next();
    iter.remove();//如果要遍历时，删除集合中的元素，建议使用这种方式！
    System.out.println(obj);
}
```

**遍历Set方法一：增强for循环**

```java
for(String temp:set){
System.out.println(temp);
}
```

**遍历Set方法二：使用Iterator迭代器**

```java
for(Iterator iter = set.iterator();iter.hasNext();){
    String temp = (String)iter.next();
    System.out.println(temp);
}
```

**遍历Map方法一：根据key获取value**

```java
Map<Integer, Man> maps = new HashMap<Integer, Man>();
Set<Integer>  keySet =  maps.keySet();
for(Integer id : keySet){
System.out.println(maps.get(id).name);
}
```

**遍历Map方法二：使用entrySet**

```java
Set<Entry<Integer, Man>>  ss = maps.entrySet();
for (Iterator iterator = ss.iterator(); iterator.hasNext();) {
    Entry e = (Entry) iterator.next(); 
    System.out.println(e.getKey()+"--"+e.getValue());
```

# **Collections工具类**

 类 java.util.Collections 提供了对Set、List、Map进行排序、填充、查找元素的辅助方法。

   \1. void sort(List) //对List容器内的元素排序，排序的规则是按照升序进行排序。

   \2. void shuffle(List) //对List容器内的元素进行随机排列。

   \3. void reverse(List) //对List容器内的元素进行逆续排列 。

   \4. void fill(List, Object) //用一个特定的对象重写整个List容器。

   \5. int binarySearch(List, Object)//对于顺序的List容器，采用折半查找的方法查找特定对象。

```java
public class Test {
    public static void main(String[] args) {
        List<String> aList = new ArrayList<String>();
        for (int i = 0; i < 5; i++){
            aList.add("a" + i);
        }
        System.out.println(aList);
        Collections.shuffle(aList); // 随机排列
        System.out.println(aList);
        Collections.reverse(aList); // 逆续
        System.out.println(aList);
        Collections.sort(aList); // 排序
        System.out.println(aList);
        System.out.println(Collections.binarySearch(aList, "a2")); 
        Collections.fill(aList, "hello");
        System.out.println(aList);
    }
}
```


