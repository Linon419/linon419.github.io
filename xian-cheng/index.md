# 线程

# 基本概念

多线程是Java语言的重要特性，大量应用于网络编程、服务器端程序的开发，最常见的UI界面底层原理、操作系统底层原理都大量使用了多线程。

   我们可以流畅的点击软件或者游戏中的各种按钮，其实，底层就是多线程的应用。UI界面的主线程绘制界面，如果有一个耗时的操作发生则启动新的线程，完全不影响主线程的工作。当这个线程工作完毕后，再更新到主界面上。

   我们可以上百人、上千人、上万人同时访问某个网站，其实，也是基于网站服务器的多线程原理。如果没有多线程，服务器处理速度会极大降低。

   多线程应用于计算机的各个方面，但是对于初学者，我们只需掌握基本的概念即可。在入门阶段，暂时没有必要钻研过深。

<!-- more -->

## 程序

 “程序(Program)”是一个静态的概念，一般对应于操作系统中的一个可执行文件，比如：我们要启动酷狗听音乐，则对应酷狗的可执行程序。当我们双击酷狗，则加载程序到内存中，开始执行该程序，于是产生了“进程”。

## 进程

执行中的程序叫做进程(Process)，是一个动态的概念。现代的操作系统都可以同时启动多个进程。比如：我们在用酷狗听音乐，也可以使用eclipse写代码，也可以同时用浏览器查看网页。进程具有如下特点：

   \1. 进程是程序的一次动态执行过程， 占用特定的地址空间。

   \2. 每个进程由3部分组成：cpu、data、code。每个进程都是独立的，保有自己的cpu时间，代码和数据，即便用同一份程序产生好几个进程，它们之间还是拥有自己的这3样东西，这样的缺点是：浪费内存，cpu的负担较重。

   \3. 多任务(Multitasking)操作系统将CPU时间动态地划分给每个进程，操作系统同时执行多个进程，每个进程独立运行。以进程的观点来看，它会以为自己独占CPU的使用权。

   \4. 进程的查看

​     Windows系统: Ctrl+Alt+Del，启动任务管理器即可查看所有进程。

​     Unix系统: ps or top。

## 线程

一个进程可以产生多个线程。同多个进程可以共享操作系统的某些资源一样，同一进程的多个线程也可以共享此进程的某些资源(比如：代码、数据)，所以线程又被称为轻量级进程(lightweight process)。

   \1. 一个进程内部的一个执行单元，它是程序中的一个单一的顺序控制流程。

   \2. 一个进程可拥有多个并行的(concurrent)线程。

   \3. 一个进程中的多个线程共享相同的内存单元/内存地址空间，可以访问相同的变量和对象，而且它们从同一堆中分配对象并进行通信、数据交换和同步操作。

   \4. 由于线程间的通信是在同一地址空间上进行的，所以不需要额外的通信机制，这就使得通信更简便而且信息传递的速度也更快。

   \5. 线程的启动、中断、消亡，消耗的资源非常少。

## **线程和进程的区别**

 \1. 每个进程都有独立的代码和数据空间(进程上下文)，进程间的切换会有较大的开销。

   \2. 线程可以看成是轻量级的进程，属于同一进程的线程共享代码和数据空间，每个线程有独立的运行栈和程序计数器(PC)，线程切换的开销小。

   \3. 线程和进程最根本的区别在于：进程是资源分配的单位，线程是调度和执行的单位。

   \4. 多进程: 在操作系统中能同时运行多个任务(程序)。

   \5. 多线程: 在同一应用程序中有多个顺序流同时执行。

   \6. 线程是进程的一部分，所以线程有的时候被称为轻量级进程。

   \7. 一个没有线程的进程是可以被看作单线程的，如果一个进程内拥有多个线程，进程的执行过程不是一条线(线程)的，而是多条线(线程)共同完成的。

   \8.  系统在运行的时候会为每个进程分配不同的内存区域，但是不会为线程分配内存(线程所使用的资源是它所属的进程的资源)，线程组只能共享资源。那就是说，除了CPU之外(线程在运行的时候要占用CPU资源)，计算机内部的软硬件资源的分配与线程无关，线程只能共享它所属进程的资源。

## 进程与程序的区别

程序是一组指令的集合，它是静态的实体，没有执行的含义。而进程是一个动态的实体，有自己的生命周期。一般说来，一个进程肯定与一个程序相对应，并且只有一个，但是一个程序可以有多个进程，或者一个进程都没有。除此之外，进程还有并发性和交往性。简单地说，进程是程序的一部分，程序运行的时候会产生进程。

# **Java中如何实现多线程**

 在Java中使用多线程非常简单，我们先学习如何创建和使用线程，然后再结合案例深入剖析线程的特性。

## **通过继承Thread类实现多线程**

 继承Thread类实现多线程的步骤：

   \1. 在Java中负责实现线程功能的类是java.lang.Thread 类。

   \2. 可以通过创建 Thread的实例来创建新的线程。

   \3. 每个线程都是通过某个特定的Thread对象所对应的方法run( )来完成其操作的，方法run( )称为线程体。

   \4. 通过调用Thread类的start()方法来启动一个线程。

 **此种方式的缺点：**如果我们的类已经继承了一个类(如小程序必须继承自 Applet 类)，则无法再继承 Thread 类。

```java
public class TestThread extends Thread {//自定义类继承Thread类
    //run()方法里是线程体
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(this.getName() + ":" + i);//getName()方法是返回线程名称
        }
    }
 
    public static void main(String[] args) {
        TestThread thread1 = new TestThread();//创建线程对象
        thread1.start();//启动线程
        TestThread thread2 = new TestThread();
        thread2.start();
    }
}
```



## **通过Runnable接口实现多线程**

在开发中，我们应用更多的是通过Runnable接口实现多线程。这种方式克服了11.2.1节中实现线程类的缺点，即在实现Runnable接口的同时还可以继承某个类。所以实现Runnable接口的方式要通用一些。

```java
public class Demo02 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName()+":"+i);
        }
    }

    public static void main(String[] args) {
        Thread th1 = new Thread(new Demo02());
        th1.start();
        Thread th2 = new Thread(new Demo02());
        
    }
}

```

# 线程状态


![](https://linon419.github.io/post-images/1579522358405.png)
一个线程对象在它的生命周期内，需要经历5个状态。

**▪ 新生状态(New)**

   用new关键字建立一个线程对象后，该线程对象就处于新生状态。处于新生状态的线程有自己的内存空间，通过调用start方法进入就绪状态。

**▪ 就绪状态(Runnable)**

   处于就绪状态的线程已经具备了运行条件，但是还没有被分配到CPU，处于“线程就绪队列”，等待系统为其分配CPU。就绪状态并不是执行状态，当系统选定一个等待执行的Thread对象后，它就会进入执行状态。一旦获得CPU，线程就进入运行状态并自动调用自己的run方法。有4中原因会导致线程进入就绪状态：

1. 新建线程：调用start()方法，进入就绪状态;

2. 阻塞线程：阻塞解除，进入就绪状态;

3. 运行线程：调用yield()方法，直接进入就绪状态;

4. 运行线程：JVM将CPU资源从本线程切换到其他线程。

**▪ 运行状态(Running)**

   在运行状态的线程执行自己run方法中的代码，直到调用其他方法而终止或等待某资源而阻塞或完成任务而死亡。如果在给定的时间片内没有执行结束，就会被系统给换下来回到就绪状态。也可能由于某些“导致阻塞的事件”而进入阻塞状态。

**▪ 阻塞状态(Blocked)**

   阻塞指的是暂停一个线程的执行以等待某个条件发生(如某资源就绪)。有4种原因会导致阻塞：

   \1. 执行sleep(int millsecond)方法，使当前线程休眠，进入阻塞状态。当指定的时间到了后，线程进入就绪状态。

   \2. 执行wait()方法，使当前线程进入阻塞状态。当使用nofity()方法唤醒这个线程后，它进入就绪状态。

   \3. 线程运行时，某个操作进入阻塞状态，比如执行IO流操作(read()/write()方法本身就是阻塞的方法)。只有当引起该操作阻塞的原因消失后，线程进入就绪状态。

   \4. join()线程联合: 当某个线程等待另一个线程执行结束后，才能继续执行时，使用join()方法。

**▪ 死亡状态(Terminated)**

   死亡状态是线程生命周期中的最后一个阶段。线程死亡的原因有两个。一个是正常运行的线程完成了它run()方法内的全部工作; 另一个是线程被强制终止，如通过执行stop()或destroy()方法来终止一个线程(注：stop()/destroy()方法已经被JDK废弃，不推荐使用)。

   当一个线程进入死亡状态以后，就不能再回到其它状态了。

## **终止线程的典型方式**

终止线程我们一般不使用JDK提供的stop()/destroy()方法(它们本身也被JDK废弃了)。通常的做法是提供一个boolean型的终止变量，当这个变量置为false，则终止线程的运行。

```java
public class TestThreadCiycle implements Runnable {
    String name;
    boolean live = true;// 标记变量，表示线程是否可中止；
    public TestThreadCiycle(String name) {
        super();
        this.name = name;
    }
    public void run() {
        int i = 0;
        //当live的值是true时，继续线程体；false则结束循环，继而终止线程体；
        while (live) {
            System.out.println(name + (i++));
        }
    }
    public void terminate() {
        live = false;
    }
 
    public static void main(String[] args) {
        TestThreadCiycle ttc = new TestThreadCiycle("线程A:");
        Thread t1 = new Thread(ttc);// 新生状态
        t1.start();// 就绪状态
        for (int i = 0; i < 100; i++) {
            System.out.println("主线程" + i);
        }
        ttc.terminate();
        System.out.println("ttc stop!");
    }
}

-----------------------
  no.10
主线程0
主线程1
no.11
no.12
no.13
主线程2
主线程3
主线程4
主线程5
主线程6
主线程7
主线程8
no.14
主线程9
主线程10
主线程11
no.15
主线程12
主线程13
主线程14
no.16
主线程15
no.17
主线程16
no.18
主线程17
no.19
主线程18
no.110
主线程19
no.111
主线程20
no.112
主线程21
no.113
主线程22
no.114
主线程23
no.115
主线程24
no.116
主线程25
no.117
主线程26
no.118
主线程27
no.119
主线程28
no.120
no.121
主线程29
no.122
no.123
no.124
no.125
no.126
no.127
主线程30
no.128
主线程31
主线程32
no.129
主线程33
no.130
no.131
no.132
no.133
no.134
no.135
no.136
no.137
no.138
no.139
no.140
no.141
no.142
no.143
no.144
no.145
主线程34
主线程35
主线程36
主线程37
主线程38
no.146
主线程39
no.147
主线程40
no.148
主线程41
no.149
主线程42
no.150
主线程43
主线程44
主线程45
主线程46
主线程47
主线程48
主线程49
主线程50
主线程51
主线程52
主线程53
主线程54
主线程55
主线程56
主线程57
no.151
主线程58
主线程59
主线程60
主线程61
主线程62
主线程63
主线程64
主线程65
主线程66
主线程67
no.152
主线程68
no.153
no.154
no.155
no.156
no.157
no.158
主线程69
主线程70
主线程71
no.159
主线程72
no.160
主线程73
主线程74
主线程75
no.161
主线程76
no.162
no.163
主线程77
no.164
no.165
no.166
主线程78
no.167
主线程79
no.168
主线程80
no.169
no.170
no.171
no.172
no.173
no.174
no.175
no.176
no.177
no.178
no.179
no.180
no.181
no.182
no.183
no.184
no.185
no.186
no.187
no.188
no.189
no.190
no.191
no.192
no.193
no.194
no.195
no.196
no.197
no.198
no.199
no.1100
主线程81
主线程82
no.1101
no.1102
no.1103
no.1104
no.1105
no.1106
no.1107
no.1108
no.1109
no.1110
no.1111
no.1112
no.1113
no.1114
主线程83
主线程84
主线程85
主线程86
主线程87
主线程88
主线程89
主线程90
主线程91
主线程92
主线程93
no.1115
主线程94
主线程95
主线程96
主线程97
主线程98
主线程99
tcc stop
no.1116

```

## **暂停线程执行sleep/yield**

暂停线程执行常用的方法有sleep()和yield()方法，这两个方法的区别是：

1. sleep()方法：可以让正在运行的线程进入阻塞状态，直到休眠时间满了，进入就绪状态。

2. yield()方法：可以让正在运行的线程直接进入就绪状态，让出CPU的使用权。

暂停（sleep）：

```java
public class TestThreadState {
    public static void main(String[] args) {
        StateThread thread1 = new StateThread();
        thread1.start();
        StateThread thread2 = new StateThread();
        thread2.start();
    }
}
//使用继承方式实现多线程
class StateThread extends Thread {
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(this.getName() + ":" + i);
            try {
                Thread.sleep(2000);//调用线程的sleep()方法；
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

暂停线程方法（yield）：

```java
public class TestThreadState {
    public static void main(String[] args) {
        StateThread thread1 = new StateThread();
        thread1.start();
        StateThread thread2 = new StateThread();
        thread2.start();
    }
}
//使用继承方式实现多线程
class StateThread extends Thread {
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(this.getName() + ":" + i);
            Thread.yield();//调用线程的yield()方法；
        }
    }
}
```

## 线程的联合

 线程A在运行期间，可以调用线程B的join()方法，让线程B和线程A联合。这样，线程A就必须等待线程B执行完毕后，才能继续执行。如下面示例中，“爸爸线程”要抽烟，于是联合了“儿子线程”去买烟，必须等待“儿子线程”买烟完毕，“爸爸线程”才能继续抽烟。

```java
public class Demo05 {
    public static void main(String[] args) {
        Thread fa = new Thread(new FatherThread());
        fa.start();
    }

    static class FatherThread implements Runnable{

        @Override
        public void run() {
            System.out.println("Your father wants to smoke");
            System.out.println("Go out and buy it");
            Thread son = new Thread(new SonThread());
            son.start();
            System.out.println("Father is waiting");
            try{
                son.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
                System.out.println("Where is my son");
                System.exit(1);
            }
            System.out.println("Father is so happy");
        }
    }
}

    class SonThread implements Runnable{

        @Override
        public void run() {
            System.out.println("Go out and but it");
            System.out.println("It needs 10 mins");
            try{
                for (int i = 0; i < 10; i++) {
                    System.out.println("第"+i+"分钟");
                    Thread.sleep(1000);
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("I am back");
        }
    }
```

# **获取线程基本信息的方法**

![](https://linon419.github.io/post-images/1579522394614.png)
```java
public class TestThread {
    public static void main(String[] argc) throws Exception {
        Runnable r = new MyThread();
        Thread t = new Thread(r, "Name test");//定义线程对象，并传入参数；
        t.start();//启动线程；
        System.out.println("name is: " + t.getName());//输出线程名称；
        Thread.currentThread().sleep(5000);//线程暂停5分钟；
        System.out.println(t.isAlive());//判断线程还在运行吗？
        System.out.println("over!");
    }
}
class MyThread implements Runnable {
    //线程体；
    public void run() {
        for (int i = 0; i < 10; i++)
            System.out.println(i);
    }
}
```

## 线程的优先级

1. 处于就绪状态的线程，会进入“就绪队列”等待JVM来挑选。

2. 线程的优先级用数字表示，范围从1到10，一个线程的缺省优先级是5。

3. 使用下列方法获得或设置线程对象的优先级。

​     int getPriority();

​     void setPriority(int newPriority);

   注意：优先级低只是意味着获得调度的概率低。并不是绝对先调用优先级高的线程后调用优先级低的线程。

```java
public class TestThread {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyThread(), "t1");
        Thread t2 = new Thread(new MyThread(), "t2");
        t1.setPriority(1);
        t2.setPriority(10);
        t1.start();
        t2.start();
    }
}
class MyThread extends Thread {
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName() + ": " + i);
        }
    
```

# **什么是线程同步**

**▪ 同步问题的提出**

   现实生活中，我们会遇到“同一个资源，多个人都想使用”的问题。 比如：教室里，只有一台电脑，多个人都想使用。天然的解决办法就是，在电脑旁边，大家排队。前一人使用完后，后一人再使用。

**▪ 线程同步的概念**

   处理多线程问题时，多个线程访问同一个对象，并且某些线程还想修改这个对象。 这时候，我们就需要用到“线程同步”。 线程同步其实就是一种等待机制，多个需要同时访问此对象的线程进入这个对象的等待池形成队列，等待前面的线程使用完毕后，下一个线程再使用。

**多线程操作同一个对象(未使用线程同步)**

```java
public class TestSync {
    public static void main(String[] args) {
        Account a1 = new Account(100, "高");
        Drawing draw1 = new Drawing(80, a1);// 定义取钱线程对象；
        Drawing draw2 = new Drawing(80, a1);// 定义取钱线程对象；
        draw1.start(); // 你取钱
        draw2.start(); // 你老婆取钱
    }
}
/*
 * 简单表示银行账户
 */
class Account {
    int money;
    String aname;
 
    public Account(int money, String aname) {
        super();
        this.money = money;
        this.aname = aname;
    }
}
/**
 * 模拟提款操作
 */
class Drawing extends Thread {
    int drawingNum; // 取多少钱
    Account account; // 要取钱的账户
    int expenseTotal; // 总共取的钱数
 
    public Drawing(int drawingNum, Account account) {
        super();
        this.drawingNum = drawingNum;
        this.account = account;
    }
 
    @Override
    public void run() {
        if (account.money - drawingNum < 0) {
            return;
        }
        try {
            Thread.sleep(1000); // 判断完后阻塞。其他线程开始运行。
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        account.money -= drawingNum;
        expenseTotal += drawingNum;
        System.out.println(this.getName() + "--账户余额：" + account.money);
        System.out.println(this.getName() + "--总共取了：" + expenseTotal);
    }
}
```

没有线程同步机制，两个线程同时操作同一个账户对象，竟然从只有100元的账户，轻松取出80*2=160元，账户余额竟然成为了-60。这么大的问题，显然银行不会答应的。

## 实现多线程同步

由于同一进程的多个线程共享同一块存储空间，在带来方便的同时，也带来了访问冲突的问题。Java语言提供了专门机制以解决这种冲突，有效避免了同一个数据对象被多个线程同时访问造成的这种问题。

   由于我们可以通过 private 关键字来保证数据对象只能被方法访问，所以我们只需针对方法提出一套机制，这套机制就是synchronized关键字，它包括两种用法：synchronized 方法和 synchronized 块。

**synchronized 方法**

```java
public  synchronized  void accessVal(int newVal);
```

synchronized 方法控制对“对象的类成员变量”的访问：每个对象对应一把锁，每个 synchronized 方法都必须获得调用该方法的对象的锁方能执行，否则所属线程阻塞，方法一旦执行，就独占该锁，直到从该方法返回时才将锁释放，此后被阻塞的线程方能获得该锁，重新进入可执行状态。

**synchronized块**

   synchronized 方法的缺陷：若将一个大的方法声明为synchronized 将会大大影响效率。

   Java 为我们提供了更好的解决办法，那就是 synchronized 块。 块可以让我们精确地控制到具体的“成员变量”，缩小同步的范围，提高效率。

   synchronized 块：通过 synchronized关键字来声明synchronized 块，语法如下：

```java
synchronized(syncObject)
　  { 
　　 //允许访问控制的代码 
　  }
```

多线程操作一个对象

```java
public class TestSync {
    public static void main(String[] args) {
        Account a1 = new Account(100, "高");
        Drawing draw1 = new Drawing(80, a1);
        Drawing draw2 = new Drawing(80, a1);
        draw1.start(); // 你取钱
        draw2.start(); // 你老婆取钱
    }
}
/*
 * 简单表示银行账户
 */
class Account {
    int money;
    String aname;
    public Account(int money, String aname) {
        super();
        this.money = money;
        this.aname = aname;
    }
}
/**
 * 模拟提款操作
 * 
 * @author Administrator
 *
 */
class Drawing extends Thread {
    int drawingNum; // 取多少钱
    Account account; // 要取钱的账户
    int expenseTotal; // 总共取的钱数
 
    public Drawing(int drawingNum, Account account) {
        super();
        this.drawingNum = drawingNum;
        this.account = account;
    }
 
    @Override
    public void run() {
        draw();
    }
 
    void draw() {
        synchronized (account) {
            if (account.money - drawingNum < 0) {
                System.out.println(this.getName() + "取款，余额不足！");
                return;
            }
            try {
                Thread.sleep(1000); // 判断完后阻塞。其他线程开始运行。
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            account.money -= drawingNum;
            expenseTotal += drawingNum;
        }
        System.out.println(this.getName() + "--账户余额：" + account.money);
        System.out.println(this.getName() + "--总共取了：" + expenseTotal);
    }
}
```

“synchronized (account)” 意味着线程需要获得account对象的“锁”才有资格运行同步块中的代码。 Account对象的“锁”也称为“互斥锁”，在同一时刻只能被一个线程使用。A线程拥有锁，则可以调用“同步块”中的代码;B线程没有锁，则进入account对象的“锁池队列”等待，直到A线程使用完毕释放了account对象的锁，B线程得到锁才可以开始调用“同步块”中的代码。

## 死锁

**死锁的概念**

   “死锁”指的是：

   多个线程各自占有一些共享资源，并且互相等待其他线程占有的资源才能进行，而导致两个或者多个线程都在等待对方释放资源，都停止执行的情形。

   因此， 某一个同步块需要同时拥有“两个以上对象的锁”时，就可能会发生“死锁”的问题。下面案例中，“化妆线程”需要同时拥有“镜子对象”、“口红对象”才能运行同步块。那么，实际运行时，“小丫的化妆线程”拥有了“镜子对象”，“大丫的化妆线程”拥有了“口红对象”，都在互相等待对方释放资源，才能化妆。这样，两个线程就形成了互相等待，无法继续运行的“死锁状态”。

**【示例11-11】死锁问题演示**

```java
class Lipstick {//口红类
 
}
class Mirror {//镜子类
 
}
class Makeup extends Thread {//化妆类继承了Thread类
    int flag;
    String girl;
    static Lipstick lipstick = new Lipstick();
    static Mirror mirror = new Mirror();
 
    @Override
    public void run() {
        // TODO Auto-generated method stub
        doMakeup();
    }
 
    void doMakeup() {
        if (flag == 0) {
            synchronized (lipstick) {//需要得到口红的“锁”；
                System.out.println(girl + "拿着口红！");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
 
                synchronized (mirror) {//需要得到镜子的“锁”；
                    System.out.println(girl + "拿着镜子！");
                }
 
            }
        } else {
            synchronized (mirror) {
                System.out.println(girl + "拿着镜子！");
                try {
                    Thread.sleep(2000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (lipstick) {
                    System.out.println(girl + "拿着口红！");
                }
            }
        }
    }
 
}
 
public class TestDeadLock {
    public static void main(String[] args) {
        Makeup m1 = new Makeup();//大丫的化妆线程；
        m1.girl = "大丫";
        m1.flag = 0;
        Makeup m2 = new Makeup();//小丫的化妆线程；
        m2.girl = "小丫";
        m2.flag = 1;
        m1.start();
        m2.start();
    }
}
```

两线程都在等对方的资源，都处于停滞状态)

**死锁的解决方法**

   死锁是由于“同步块需要同时持有多个对象锁造成”的，要解决这个问题，思路很简单，就是：同一个代码块，不要同时持有两个对象锁

# **线程并发协作(生产者/消费者模式)**

多线程环境下，我们经常需要多个线程的并发和协作。这个时候，就需要了解一个重要的多线程并发协作模型“生产者/消费者模式”。

**Ø 什么是生产者?**

   生产者指的是负责生产数据的模块(这里模块可能是：方法、对象、线程、进程)。

**Ø 什么是消费者?**

   消费者指的是负责处理数据的模块(这里模块可能是：方法、对象、线程、进程)。

**Ø 什么是缓冲区?**

   消费者不能直接使用生产者的数据，它们之间有个“缓冲区”。生产者将生产好的数据放入“缓冲区”，消费者从“缓冲区”拿要处理的数据



缓冲区是实现并发的核心，缓冲区的设置有3个好处：

**Ø 实现线程的并发协作**

   有了缓冲区以后，生产者线程只需要往缓冲区里面放置数据，而不需要管消费者消费的情况;同样，消费者只需要从缓冲区拿数据处理即可，也不需要管生产者生产的情况。 这样，就从逻辑上实现了“生产者线程”和“消费者线程”的分离。

**Ø 解耦了生产者和消费者**

   生产者不需要和消费者直接打交道。

**Ø 解决忙闲不均，提高效率**

   生产者生产数据慢时，缓冲区仍有数据，不影响消费者消费;消费者处理数据慢时，生产者仍然可以继续往缓冲区里面放置数据 。



**线程并发协作总结：**

   线程并发协作(也叫线程通信)，通常用于生产者/消费者模式，情景如下：

   \1. 生产者和消费者共享同一个资源，并且生产者和消费者之间相互依赖，互为条件。

   \2. 对于生产者，没有生产产品之前，消费者要进入等待状态。而生产了产品之后，又需要马上通知消费者消费。

   \3. 对于消费者，在消费之后，要通知生产者已经消费结束，需要继续生产新产品以供消费。

   \4. 在生产者消费者问题中，仅有synchronized是不够的。

​    · synchronized可阻止并发更新同一个共享资源，实现了同步;

​    · synchronized不能用来实现不同线程之间的消息传递(通信)。

   \5. 那线程是通过哪些方法来进行消息传递(通信)的呢?见如下总结：

 ![表11-2 线程通信常用方法.png](https://www.sxt.cn/360shop/Public/admin/UEditor/20170526/1495792837120930.png)

\6. 以上方法均是java.lang.Object类的方法;

   都只能在同步方法或者同步代码块中使用，否则会抛出异常。

# **任务定时调度**

通过Timer和Timetask，我们可以实现定时启动某个线程。

**java.util.Timer**

   在这种实现方式中，Timer类作用是类似闹钟的功能，也就是定时或者每隔一定时间触发一次线程。其实，Timer类本身实现的就是一个线程，只是这个线程是用来实现调用其它线程的。

**java.util.TimerTask**

   TimerTask类是一个抽象类，该类实现了Runnable接口，所以该类具备多线程的能力。

在这种实现方式中，通过继承TimerTask使该类获得多线程的能力，将需要多线程执行的代码书写在run方法内部，然后通过Timer类启动线程的执行。

```java
public class TestTimer {
    public static void main(String[] args) {
        Timer t1 = new Timer();//定义计时器；
        MyTask task1 = new MyTask();//定义任务；
        t1.schedule(task1,3000);  //3秒后执行；
        //t1.schedule(task1,5000,1000);//5秒以后每隔1秒执行一次！
        //GregorianCalendar calendar1 = new GregorianCalendar(2010,0,5,14,36,57); 
        //t1.schedule(task1,calendar1.getTime()); //指定时间定时执行； 
    }
}
 
class MyTask extends TimerTask {//自定义线程类继承TimerTask类；
    public void run() {
        for(int i=0;i<10;i++){
            System.out.println("任务1:"+i);
        }
    }
}
```

运行以上程序时，可以感觉到在输出之前有明显的延迟(大概就是3秒!)。还有几个方法，我注释掉了，大家自己试试吧!

   在实际使用时，一个Timer可以启动任意多个TimerTask实现的线程，但是多个线程之间会存在阻塞。所以如果多个线程之间需要完全独立的话，最好还是一个Timer启动一个TimerTask实现。

**老鸟建议**

   实际开发中，我们可以使用开源框架quanz，更加方便的实现任务定时调度。实际上，quanz底层原理就是我们这里介绍的内容。
