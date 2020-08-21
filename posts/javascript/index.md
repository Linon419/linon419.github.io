# 

# 语言基础

## Hello Javascript

### 通过javascript向文档中输出文本

**document**是javascript的内置对象，代表浏览器的文档部分
**document.write("Hello Javascript");** 向文档写入字符串

```javascript
<script>
  document.write("Hello Javascript");
</script>
```



### javascript和DOM结合的一个简单例子

这是一个javascript和DOM结合的一个简单例子

**onclick=**"..." 表示点击button之后做的事情
**document.getElementById** 根据id获取指定的元素
**.style.display='none'** 隐藏
**.style.display='block'** 显示(准确的讲，以block的形式显示)

onclick，getElementById，style.display 这些内容，是[HTML DOM](https://how2j.cn/k/dom/dom-node/457.html) 应该到才会用到的知识和概念

```javascript
<button onclick="document.getElementById('text').style.display='none'">隐藏文本</button>
 
<button onclick="document.getElementById('text').style.display='block'">显示文本</button>
 
<p id="text"> 这个是一段可以被javascript隐藏的文本</p>
```

### 语言基础，BOM和DOM

完整的javascript由[语言基础](https://how2j.cn/k/javascript/javascript-type/428.html)，[BOM](https://how2j.cn/k/javascript/javascript-bom-window/449.html)和[DOM](https://how2j.cn/k/dom/dom-node/457.html)组成。

只有通过javascript操作DOM对象的时候，才会带来很好的实用效果，而本章节只会涉及到语言基础 和 BOM部分，DOM部分在[下个章节](https://how2j.cn/k/dom/dom-node/457.html)展开

## script标签

javascript代码必须放在script标签中

script标签可以放在html的任何地方，一般建议放在head标签里

### script 标签

javascript都是放在script标签中的，一旦加载，就会执行

```html
<html>
  <head>
   <script>
      document.write("这是 javascript");
   </script>
  </head>
</html>
```

### javascript顺序执行

如果有多段script代码，会按照从上到下，顺序执行

```css
<script>
   document.write("第一段javascript");
</script>
 
<script>
   document.write("第二段javascript");
</script>
```

### 使用外部js文件

和css一样，当javascript代码特别多，并且都写在html里的时候，会显得比较繁杂，难以维护。
这个时候可以[采用和css一样的手段](https://how2j.cn/k/css2/css2-link/255.html#step496)，把javascript代码剥离出来，单独放在一个文件里，在html中引用该文件即可。
准备一个[hello.js](https://how2j.cn/study/hello.js)，里面的是内容是
document.write("hello javascript ");
**注意，不要写 script标签**

```css
<html>
  <script src="https://how2j.cn/study/hello.js"></script>
</html>
```

## 注释

在代码中提供有效的注释，可以让代码更加易读和便于维护。
javascript有两种注释方式

### 单行注释

<script type="text/javascript">
// 单行注释
document.write("hello java");
</script>

### 多行注释

<script type="text/javascript">
/*
进行
多行注释
*/
document.write("hello java");
</script>

## 变量

使用var声明一个变量

### 使用var声明一个变量

```javascript
<script>
  var x = 10;
  document.write("变量x的值:"+x);
</script>
```



### 不使用var

```javascript
<script>
  x = 10;
  document.write("没有用var声明的变量x的值:"+x);
</script>
```

### 变量命名

命名规则和[java差不多](https://how2j.cn/k/variable/variable-nameing/260.html#step520)
可以使用
**开头**可以用 _$和字母
**其他部分**可以用 $ _ 字母或者数字
这些是合法的：

```
var $a;
var _b;
var ab123;
```

这些是不合法的：

```
var 3$a;
var a%;
var b*;
var (6@
```

## 调试

Javascript的运行和Java不一样，没有一个像eclipse这样的集成开发环境(IDE)。

尤其在刚开始学习的时候，更加推荐直接使用记事本来编写，而不是依赖于其他的有提示功能的编辑器([Sublime](https://how2j.cn/k/18/18-536/536.html))，这样更加利于暴露自己编写的javascript代码的问题，并纠正和学习。

但是依然存在一个调试的问题，本知识点只是讲解各种调试的办法。

### alert进行调试

使用alert(1)进行调试，这是最开始的时候非常常用的一种手法来进行javascript代码调试，即使今天，也是比较有效的一种方式。
使用alert的思路

```
alert(1)
```

会弹出一个对话框，里面的内容是1。换句话说，如果弹出了1,这个位置以上的代码，都是可以运行的。
你不停的把alert(1)向下移动，当移动到某一行之后，就不再弹出，那么就证明那一行运行有问题。 这样就把问题的范围缩小了，就很容易通过**肉眼观察法**来定位真正问题所在。

### 浏览器调试

这里准备了一段故意写错的javascript代码。
点击快捷键F12，就会出现console页面。

console是控制台的意思，用于输出一些错误和调试信息。

**注意：** 虽然这段javascript代码有错误，但是**第一次F12**是看不到错误的，因为错误已经发生了，才打开了F12。 所以打开了F12之后，使用快捷键F5刷新一下当前页面，就可以看到控制台报出了错误的原因
**document.write1 is not a function**
这样定位问题就非常方便了。

## 基本数据类型

| 关键字    | 简介              | 示例代码                                                     |
| :-------- | :---------------- | :----------------------------------------------------------- |
| undefined | 声明了但未赋值    | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1075) |
| Boolean   | 布尔              | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1076) |
| Number    | 数字              | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1077) |
| String    | 字符串            | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1078) |
| var       | 动态类型          | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1079) |
| typeof    | 变量类型判断      | [示例代码](https://how2j.cn/k/javascript/javascript-type/428.html#step1080) |
| null      | 空对象/对象不存在 |                                                              |

### 声明了但是没有赋值

<script>
  var x; //声明了变量x,但是没有赋值
  document.write('声明了，但是没有赋值的变量 x: '+x);
</script>

结果：

声明了，但是没有赋值的变量 x: undefined

### 布尔值

```javascript
<script>
  var x=true;
  var y=false;
  document.write("布尔值:"+x);
  document.write("<br>");
  document.write("布尔值:"+y);
</script>
```

结果：

布尔值:true
布尔值:false

### 数字

javascript中的Number可以表示十进制，八进制，十六进制整数，浮点数，科学记数法

```javascript
<script>
  var a=10; //十进制
  var b=012;//第一位是0，表示八进制
  var c=0xA;//0x开头表示十六进制
  var d=3.14;//有小数点表示浮点数
  var e=3.14e2;//使用e的幂表示科学计数法
  document.write("十进制 10 的值: "+a);
  document.write("<br>");
  document.write("八进制 012 的值: "+b);
  document.write("<br>");
  document.write("十六进制 0xA 的值: "+c);
  document.write("<br>");
  document.write("浮点数 3.14 的值: "+d);
  document.write("<br>");
  document.write("科学记数法 3.14e2 的值: "+e);
  document.write("<br>");
</script>
```

结果：十进制 10 的值: 10
八进制 012 的值: 10
十六进制 0xA 的值: 10
浮点数 3.14 的值: 3.14
科学记数法 3.14e2 的值: 314

### 字符串

与java不同的是，javascript中没有字符的概念，只有字符串，所以单引号和双引号，都用来表示字符串。

```
<script>
  var x='hello '; //单引号
  var y="javascript"; //双引号
  document.write("单引号的字符串:"+x);
  document.write("<br>");
  document.write("双引号的字符串:"+y);
</script>
```

### 动态类型

变量的类型是动态的，当值是整数的时候，就是Number类型，当值是字符串的时候，就是String类型

```javascript
<script>
  var x=10; //Number类型
  document.write("此时 x的值是 "+x+" 类型是数字");
  document.write("<br>");
  x = "hello javascript"; //String类型
  document.write("此时 x的值是 "+x+" 类型是字符串");
</script>
```

### 变量类型判断

使用**typeof**来进行判断数据类型

正是因为变量是动态类型的，所以无法确定**当前到底是哪种类型**，这个时候，就可以使用typeof来进行判断

```javascript
<script>
  var x;
  document.write('声明了但是未赋值的时候，类型是： '+typeof x);
  document.write("<br>");
  x=5;
  document.write('赋值为5之后，类型是： '+typeof x);
  document.write("<br>");
  x=5.1;
  document.write('赋值为5.1之后，类型是： '+typeof x);
  document.write("<br>");
  x=true;
  document.write('赋值为true之后，类型是： '+typeof x);
  document.write("<br>");
  x="hello";
  document.write('赋值为hello之后，类型是： '+typeof x);
 
</script>
```

结果：

声明了但是未赋值的时候，类型是： undefined
赋值为5之后，类型是： number
赋值为5.1之后，类型是： number
赋值为true之后，类型是： boolean
赋值为hello之后，类型是： string

### 空对象/对象不存在

null表示一个对象不存在，因为本章节讲的都是基本类型，而null是和对象相关的，所以会放在[javascript中的对象](https://how2j.cn/k/javascript/javascript-number/438.html)中进行讲解

## 类型转换

### 伪对象

**伪对象概念：**javascript是一门很有意思的语言，即便是基本类型，也是伪对象，所以他们都有属性和方法。
变量a的类型是字符串，通过调用其为伪对象的属性length获取其长度

```javascript
<script>
  var a="hello javascript";
  document.write("变量a的类型是:"+(typeof a));
  document.write("<br>");
  document.write("变量a的长度是:"+a.length);
</script>
```

### 转换为字符串

无论是Number,Boolean还是String都有一个toString方法，用于转换为字符串

```javascript
<script>
  var a=10;
  document.write("数字 "+a+" 转换为字符串"+a.toString());
  document.write("<br>");
 
  var b=true;
  document.write("布尔 "+b+" 转换为字符串"+b.toString());
  document.write("<br>");
 
  var c="hello javascript";
  document.write("字符串 "+c+" 转换为字符串 "+c.toString());
  document.write("<br>");
 
</script>
```

结果：数字 10 转换为字符串10
布尔 true 转换为字符串true
字符串 hello javascript 转换为字符串 hello javascript

### 数字转字符串

```javascript
<script>
  var a=10;
  document.write('默认模式下，数字10转换为十进制的'+a.toString()); //默认模式，即十进制
  document.write("<br>");
 
  document.write('基模式下，数字10转换为二进制的'+a.toString(2)); //基模式，二进制
  document.write("<br>");
   
  document.write('基模式下，数字10转换为八进制的'+a.toString(8)); //基模式，八进制
  document.write("<br>");
 
  document.write('基模式下，数字10转换为十六进制的'+a.toString(16)); //基模式，十六进制
  document.write("<br>");
 
</script>
```

Number转换为字符串的时候有**默认模式**和**基模式**两种

默认模式下，数字10转换为十进制的10
基模式下，数字10转换为二进制的1010
基模式下，数字10转换为八进制的12
基模式下，数字10转换为十六进制的a

### 转换为数字

javascript分别提供内置函数 parseInt()和parseFloat()，转换为数字

**注：**如果被转换的字符串，同时由数字和字符构成，那么parseInt会一直定位数字，直到出现非字符。 所以"10abc" 会被转换为 10

**思考题:** 字符串"10abc8" 又会被转换为多少呢？



```javascript
<script>
  document.write("字符串的\"10\"转换为数字的:"+parseInt("10")); //转换整数
  document.write("<br>");
  document.write("字符串的\"3.14\"转换为数字的:"+parseFloat("3.14"));//转换浮点数
  document.write("<br>");
  document.write("字符串的\"10abc\"转换为数字的:"+parseInt("10abc")); //判断每一位，直到发现不是数字的那一位
  document.write("<br>");

  document.write("字符串的\"hello javascript\"转换为数字的:"+parseInt("hello javascript")); //如果完全不包含数字，则返回NaN - Not a Number
  document.write("<br>");
  document.write("字符串的\"3ah78\"转换为数字的"+parseInt("43ffj555"));
```

结果：

字符串的"10"转换为数字的:10
字符串的"3.14"转换为数字的:3.14
字符串的"10abc"转换为数字的:10
字符串的"hello javascript"转换为数字的:NaN
字符串的"3ah78"转换为数字的43

### 转换为Boolean

使用内置函数Boolean() 转换为Boolean值
当转换字符串时：
**非空即为true**
当转换数字时：
**非0即为true**
当转换对象时：
**非null即为true**

```javascript
<script>
  document.write("空字符串''转换为布尔后的值:"+Boolean(""));  //空字符串
  document.write("<br>");
  document.write("非空字符'hello javascript '串转换为布尔后的值:"+Boolean("hello javascript"));  //非空字符串
  document.write("<br>");
  document.write("数字 0 转换为布尔后的值:"+Boolean(0));  //0
  document.write("<br>");
  document.write("数字 3.14 转换为布尔后的值:"+Boolean(3.14)); //非0
  document.write("<br>");
  document.write("空对象 null 转换为布尔后的值:"+Boolean(null));  //null
  document.write("<br>");
  document.write("非空对象 new Object() 转换为布尔后的值:"+Boolean(new Object()));  //对象存在
  document.write("<br>");
 
</script>
```

### Number()和parseInt()的区别

Number()和parseInt()一样，都可以用来进行数字的转换
区别在于，当转换的**内容包含非数字**的时候，Number() 会返回NaN(Not a Number)
parseInt() 要看情况，如果以数字开头，就会返回开头的合法数字部分，如果以非数字开头，则返回NaN

```javascript
<script>
  document.write("通过Number() 函数转换字符串'123' 后得到的数字："+Number("123"));   //正常的
  document.write("<br>");
  document.write("通过Number() 函数转换字符串'123abc' 后得到的数字："+Number("123abc"));   //包含非数字
  document.write("<br>");
  document.write("通过Number() 函数转换字符串'abc123' 后得到的数字："+Number("abc123"));   //包含非数字
  document.write("<br>");
 
  document.write("通过parseInt() 函数转换字符串'123' 后得到的数字："+parseInt("123"));   //正常的
  document.write("<br>");
  document.write("通过parseInt() 函数转换字符串'123abc' 后得到的数字："+parseInt("123abc"));   //包含非数字,返回开头的合法数字部分
  document.write("<br>");
  document.write("通过parseInt() 函数转换字符串'abc123' 后得到的数字："+parseInt("abc123"));   //包含非数字,以非数字开头，返回NaN
  document.write("<br>");
 
</script>
```

结果：

通过Number() 函数转换字符串'123' 后得到的数字：123
通过Number() 函数转换字符串'123abc' 后得到的数字：NaN
通过Number() 函数转换字符串'abc123' 后得到的数字：NaN
通过parseInt() 函数转换字符串'123' 后得到的数字：123
通过parseInt() 函数转换字符串'123abc' 后得到的数字：123
通过parseInt() 函数转换字符串'abc123' 后得到的数字：NaN



### String()和toString()的区别

String()和toString()一样都会返回字符串，区别在于对null的处理
String()会返回字符串"null"
toString() 就会报错，无法执行

```javascript
String(null) 把空对象转换为字符串：null
null.toString() 就会报错，所以后面的代码不能执行


<script>
  var a = null;
  document.write('String(null) 把空对象转换为字符串：'+String(a)); 
  document.write("<br>"); 
  document.write('null.toString() 就会报错，所以后面的代码不能执行'); 
  document.write(a.toString()); 
  document.write("因为第5行报错，所以这一段文字不会显示"); 
</script>
```

## 函数

函数即一段可以重复使用的代码

### 函数

**function**关键字用于定义一个函数
**print**即函数的名称
**()**表示参数列表，像这样就指没有参数
**{** 表示函数开始
**}** 表示函数结束
光有函数的定义，还不够，它不会自动执行，还需要进行第5行的调用

```javascript
<script>
function print(){
  document.write("这一句话是由一个自定义函数打印");
}
print();//调用
</script>
```

### 带参数函数

<script>
function print(message){
  document.write(message);
}
print("第一句话");
print("<br>");
print("第二句话");
</script>

### 带返回值的函数

自定义一个calc函数，用于计算两个参数的和，并通过**return** 返回计算结果

```javascript
<script>
function print(message){
  document.write(message);
}
 
function calc(x,y){
  return x+y;
}
 
var sum = calc(500,20);
print(sum);
 
</script>
//结果520
```

## 作用域

### 参数的作用域

一个参数的作用域就在这个函数内部，超出函数就看不见该参数了

```javascript
<script>
 
function f1(a){
   document.write('参数的作用域在函数以内，其值是 '+a);//参数a的作用范围，所以打印出来是5；
}
 
function f2(){
   document.write('在函数里不能访问其他函数的参数'+a); //不在参数a的作用范围，是一个未声明的变量，无法打印
}
 
f1(5);
f2();
document.write('在函数外也不能访问'+a);//也不在参数a的作用范围，是一个未声明的变量，无法打印
 
</script>
```

参数的作用域在函数以内，其值是 5

### 全局变量的作用域

```javascript
<script>
var a = 0; //定义在函数前面，即全局变量，所有函数都可以访问
 
function f1(){
  document.write('通过函数f1 设置全局变量a的值 为 5');
  a = 5; //能够访问
}
 
function f2(){
  document.write('通过函数f2 访问并打印全局变量a的值 '+a); //能够访问
}
 
f1(); //通过f1，设置a的值
document.write('<br>');
f2(); //通过f2,  打印a的值
</script>
```

结果：

通过函数f1 设置全局变量a的值 为 5
通过函数f2 访问并打印全局变量a的值 5

## 事件

事件是javascript允许html与用户交互的行为。 用户任何对网页的操作，都会产生一个事件。

事件有很多种，比如鼠标移动，鼠标点击，键盘点击等等。

本例演示当一个按钮被点击的时候，弹出一个对话框

更多的事件，请参考[HTML DOM 的事件章节](https://how2j.cn/k/dom/dom-event/464.html)

### 鼠标点击事件

首先定义一个函数 showHello，被调用的时候，弹出一个对话框"Hello JavaScript";

接着准备一个button元素,在button元素上增加一个属性
property是**onclick**,表示点击的时候触发
value是**showHello()**，调用showHello()函数

## 算数运算符

| 关键字           | 简介             | 示例代码                                                     |
| :--------------- | :--------------- | :----------------------------------------------------------- |
| + - * / %        | 基本算数运算符   | [示例代码](https://how2j.cn/k/javascript/javascript-arithmetic/433.html#step1099) |
| ++ --            | 自增，自减运算符 | [示例代码](https://how2j.cn/k/javascript/javascript-arithmetic/433.html#step1101) |
| = += -= *= /= %= | 赋值运算符       | [示例代码](https://how2j.cn/k/javascript/javascript-arithmetic/433.html#step1100) |
| +                | +运算符的多态    |                                                              |

### 自增自减

```javascript
<script>
 
var a = 5;
document.write('a++ 是先取值，再运算，所以打印出来是：'+a++); //先取值 ，即5
 
document.write("<br>");
var b = 5;
document.write('++b 是先运算，再取值，所以打印出来是：'+ ++b); //先运算，再取值，即6
 
</script>
```

## 逻辑运算符

| 关键字          | 简介               | 示例代码                                                     |
| :-------------- | :----------------- | :----------------------------------------------------------- |
| == != > >= < <= | 基本逻辑运算符     | [示例代码](https://how2j.cn/k/javascript/javascript-logic/434.html#step1103) |
| === !==         | 绝对等，绝对不等于 | [示例代码](https://how2j.cn/k/javascript/javascript-logic/434.html#step1104) |
| ?:              | 三目运算符         |                                                              |

### 绝对等

与==进行值是否相等的判断不同 ，绝对等 ===还会进行 类型的判断
比如 数字1和 字符串'1'比较，值是相等的，但是类型不同
所以==会返回true,但是===会返回false
绝对不等于!== 与上是一个道理

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
p("1=='1': "+(1=='1'));
p("1==='1': "+(1==='1'));
 
</script>
```

1=='1': true
1==='1': false

### 三目运算符

三目运算符 ?: 有三个操作数
如果第一个返回true,就返回第二个操作符
否则就返回第三个操作符。

使用?: 三相运算法进行判断。
age<18?"卡通":"你懂的"
表示当年纪小于18的时候，就看卡通，否则就看 你懂得
而age变量的值是15，所以返回 卡通

## 条件语句

| 关键字  | 简介                 | 示例代码                                                     |
| :------ | :------------------- | :----------------------------------------------------------- |
| if      | 条件成立时执行       | [示例代码](https://how2j.cn/k/javascript/javascript-condition/435.html#step1106) |
| else    | 条件不成立时执行     | [示例代码](https://how2j.cn/k/javascript/javascript-condition/435.html#step1107) |
| else if | 多条件判断 - else if | [示例代码](https://how2j.cn/k/javascript/javascript-condition/435.html#step1108) |
| switch  | 多条件判断 - switch  |                                                              |

switch

**switch** 语句与else if一样，也是进行多条件判断的
需要注意的是，每个判断结束，都要加上**break;**
本例用到了Date对象，更多的用法，请参考 [javascript 日期对象](https://how2j.cn/k/javascript/javascript-date/440.html)

```javascript
<script>
var day=new Date().getDay(); //通过日期对象获取数字形式的星期几
var today;
switch (day)
{
case 0:
  today="星期天";
  break;
case 1:
  today="星期一";
  break;
case 2:
  today="星期二";
  break;
case 3:
  today="星期三";
  break;
case 4:
 today="星期四";
  break;
case 5:
  today="星期五";
  break;
case 6:
  today="星期六";
  break;
}
 
document.write("今天是 ： "+today);
 
</script>
```

## 循环语句

常用的循环语句有： for, while, do-while, for-each

都是用于在满足条件的前提下，重复执行代码用的

| 关键字   | 简介                   | 示例代码                                                     |
| :------- | :--------------------- | :----------------------------------------------------------- |
| for      | 循环语句               | [示例代码](https://how2j.cn/k/javascript/javascript-cycle/436.html#step1110) |
| while    | 循环语句               | [示例代码](https://how2j.cn/k/javascript/javascript-cycle/436.html#step1111) |
| do-while | 循环语句，至少执行一次 | [示例代码](https://how2j.cn/k/javascript/javascript-cycle/436.html#step1112) |
| forEach  | 增强型循环语句         | [示例代码](https://how2j.cn/k/javascript/javascript-cycle/436.html#step2107) |
| continue | 继续下一次循环         | [示例代码](https://how2j.cn/k/javascript/javascript-cycle/436.html#step2105) |
| break    | 终止循环               |                                                              |

**continue** 表示放弃本次循环，进行下一次循环

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
  
document.write("使用for循环打印 0 到 4<br>如果发现是3，就<span style='color:red'>放弃本次循环，并且进入下一次</span>循环<br>");
  
for(i=0;i<5;i++){
  if(i==3)
    continue;
  p(i);
}
  
</script>
```

使用for循环打印 0 到 4
如果发现是3，就放弃本次循环，并且进入下一次循环
0
1
2
4

## 错误处理

JavaScript提供了一种try catch的错误处理机制，当有错误抛出的时候，可以catch住

```javascript
<script>
 
function f1(){
  //函数f1是存在的
}
try{
   document.write("试图调用不存在的函数f2()<br>");
    f2();  //调用不存在的函数f2();
}
catch(err){
   document.write("捕捉到错误产生:");
    document.write(err.message);
}
 
document.write("<p>因为错误被捕捉了，所以后续的代码能够继续执行</p>");
 
</script>
```

试图调用不存在的函数f2()
捕捉到错误产生:f2 is not defined

因为错误被捕捉了，所以后续的代码能够继续执行

# 对象

## 数字

JavaScript中的对象是有着属性和方法的一种特殊数据类型。

常见的对象有数字Number，字符串String，日期Date，数组Array等。

本章节从数字对象开始讲起

**注:** 这里讲的Number是**对象Number,**和[基本数据类型](https://how2j.cn/k/javascript/javascript-type/428.html)中的**基本类型Number**是不一样的Number。

| 关键字                      | 简介                           | 示例代码                                                     |
| :-------------------------- | :----------------------------- | :----------------------------------------------------------- |
| new Number                  | 创建一个数字对象               | [示例代码](https://how2j.cn/k/javascript/javascript-number/438.html#step1116) |
| 属性MIN_VALUE 属性MAX_VALUE | 最小值 最大值                  | [示例代码](https://how2j.cn/k/javascript/javascript-number/438.html#step1118) |
| 属性NaN                     | 表示不是数字                   | [示例代码](https://how2j.cn/k/javascript/javascript-number/438.html#step1122) |
| 方法toFixed                 | 返回一个数字的小数表达         | [示例代码](https://how2j.cn/k/javascript/javascript-number/438.html#step1119) |
| 方法toExponential           | 返回一个数字的科学计数法表达   | [示例代码](https://how2j.cn/k/javascript/javascript-number/438.html#step1120) |
| 方法valueOf                 | 返回一个数字对象的基本数字类型 |                                                              |

### 创建一个数字对象

可以通过new Number()创建一个数字**对象**

与基本类型的数字不同，对象类型的数字，拥有更多的属性和方法
接下来就会讲解各种属性和方法

```javascript
<script>
 
var x = new Number(123);
 document.write('数字对象x的值:'+x);
 document.write("<br>");
 document.write('数字对象x的类型:'+typeof x); //通过typeof 获知这是一个object
 document.write("<br>");
var y = 123;
 document.write('基本类型y的值:'+y);
 document.write("<br>");
 document.write('基本类型y的类型:'+typeof y); //通过typeof 获知这是一个number
 
</script>
```

数字对象x的值:123
数字对象x的类型:object
基本类型y的值:123
基本类型y的类型:number

### 最小值 最大值

```javascript
<script>
 
 document.write('Number对象的最小值:'+Number.MIN_VALUE);
 
 document.write("<br>");
 
 document.write('Number对象的最大值:'+Number.MAX_VALUE);
 
</script>
```

Number对象的最小值:5e-324
Number对象的最大值:1.7976931348623157e+308

### 表示不是数字

**NaN**(Not a Number),表示不是一个数字
当通过非数字创建Number的时候，就会得到NaN.
注意： 不能通过 是否等于Number.NaN来判断 是否 “不是一个数字”，应该使用函数 isNaN()

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var a = new Number("123abc"); //通过非数字创建Number对象，得到的是一个NaN
p('通过非数字字符串"123abc"创建出来的Number对象 a的值是：'+a);
 
p('但是, a==Number.NaN会返回:'+(a==Number.NaN)); //即便是一个NaN 也"不等于" Number.NaN
 
p('正确判断是否是NaN的方式是调用isNaN函数:'+isNaN(a)); //正确的方式是通过isNaN() 函数进行判断
 
</script>
```

### 返回一个数字的小数表达

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var a = new Number("123");
 
p("数字对象123通过toFixed(2) 保留两位小数:"+a.toFixed(2)); //保留两位小数点
 
var b = new Number("3.1415926");
 
p("PI 通过toFixed(3) 保留三位小数:"+b.toFixed(3));//保留三位小数点
 
</script>
```

### 返回一个数字的科学计数法表达

数字对象123通过toExponential 返回计数法表达 1.23e+2
数字对象3.1415926通过toExponential 返回计数法表达 3.1415926e+0

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
  
var a = new Number("123");
  
p("数字对象123通过toExponential 返回计数法表达 "+a.toExponential ());
  
var b = new Number("3.1415926");
  
p("数字对象3.1415926通过toExponential 返回计数法表达 "+b.toExponential ());
  
</script>
```

### 返回一个数字对象的基本数字类型

方法 valueOf() 返回一个基本类型的数字
通过typeof 判断数据类型可以发现，一种是object,一种是number

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var a = new Number("123");
 
var b = a.valueOf();
 
p('数字对象a的类型是: '+typeof a); //返回object
p('通过valueOf()返回的值的类型是'+typeof b); //返回number
 
</script>
```

## 字符串

与数字类似，基本类型String也有一个对应的String 对象，并且提供了很多有用的方法。

| 关键字                                 | 简介                                                         | 示例代码                                                     |
| :------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| new String()                           | 创建字符串对象                                               | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1123) |
| 属性 length                            | 字符串长度                                                   | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1124) |
| 方法 charAt() charCodeAt               | 返回指定位置的字符                                           | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1125) |
| 方法 x.concat(y)                       | 字符串拼接                                                   | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1126) |
| 方法 indexOf("") lastIndexOf("")       | 子字符串出现的位置                                           | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1127) |
| 方法 x.localeCompare("y")              | 比较两段字符串是否相同                                       | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1128) |
| 方法 substring                         | 截取一段子字符串,字符串x的值: Hello JavaScript<br/>x.substring (0,3) 获取位0到3的字符串： Hel<br/>左闭右开，取得到0，取不到3 | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1129) |
| 方法 split                             | 根据分隔符，把字符串转换为数组                               | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1205) |
| 方法 replace                           | 替换子字符串                                                 | [示例代码](https://how2j.cn/k/javascript/javascript-string/439.html#step1814) |
| 方法 charAt 方法 concat 方法 substring | 返回基本类型                                                 | g                                                            |

### 根据分隔符，把字符串转换为数组

split 根据分隔符，把字符串转换为数组。
注： 第二个参数可选，表示返回数组的长度

```javascript
<script>
var x = new String("Hello This Is JavaScript");
document.write( '字符串x的值: '+x);
document.write('<br>');
 
var y =  x.split(" ");
document.write('通过空格分隔split(" "),得到数组'+y);
document.write("<br>");
 
var z =  x.split(" ",2);
document.write('通过空格分隔split(" ",2),得到数组，并且只保留前两个'+z);
  
</script>
```

字符串x的值: Hello This Is JavaScript
通过空格分隔split(" "),得到数组Hello,This,Is,JavaScript
通过空格分隔split(" ",2),得到数组，并且只保留前两个Hello,This

### 替换子字符串

replace(search,replacement)
找到满足条件的子字符串search，替换为replacement

注: 默认情况下只替换找到的第一个子字符串，如果要所有都替换，需要写成：

x.replace(/a/g, "o");

或者

var regS = new RegExp("a","g");

x.replace(regS, "o");

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
  
var x = new String("Hello JavaScript");
p('这个是原字符串: '+x);
var y = x.replace("a","o");
p('只替换第一个 a:  '+y);
var regS = new RegExp("a","g");
var z = x.replace(regS, "o");
p('替换掉所有的 a:  '+z);
 
</script>
```

这个是原字符串: Hello JavaScript
只替换第一个 a: Hello JovaScript
替换掉所有的 a: Hello JovoScript

## 数组

javascript中的数组是动态的，即长度是可以发生变化的。

| 关键字                                         | 简介                                             | 示例代码                                                     |
| :--------------------------------------------- | :----------------------------------------------- | :----------------------------------------------------------- |
| new Array                                      | 创建数组对象                                     | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1131) |
| 属性 length                                    | 数组长度                                         | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1132) |
| for for in                                     | 遍历一个数组                                     | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1140) |
| 方法 concat                                    | 连接数组                                         | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1133) |
| 方法 join                                      | 通过指定分隔符，返回一个数组的字符串表达         | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1134) |
| 方法 push pop                                  | 分别在最后的位置插入数据和获取数据(获取后删除)   | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1135) |
| 方法 unshift shift                             | 分别在最开始的位置插入数据和获取数据(获取后删除) | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1136) |
| 方法 sort                                      | 对数组的内容进行排序                             | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1137) |
| 方法 sort(comparator)                          | 自定义排序算法                                   | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step2962) |
| ![img](https://how2j.cn/img/site/practise.png) | 练习-排序                                        | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step2894) |
| ![img](https://how2j.cn/img/site/answer.png)   | 答案-排序                                        | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step2113) |
| 方法 reverse                                   | 对数组的内容进行反转                             | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1138) |
| 方法 slice                                     | 获取子数组                                       | [示例代码](https://how2j.cn/k/javascript/javascript-array/441.html#step1139) |
| 方法 splice                                    | 删除和插入元素                                   |                                                              |

### 创建数组对象

创建一个数组对象
创建数组对象的3种方式：

1. new Array() 创建长度是0的数组
2. new Array(5); 创建长度是5的数组,，但是其每一个元素都是undefine
3. new Array(3,1,4,1,5,9,2,6); 根据参数创建数组

```javascript
<script>
function p(s,v){
  document.write(s+' '+v);
  document.write("<br>");
}
 
var x = new Array(); //创建长度是0的数组
p('通过 new Array()创建一个空数组:',x);
x = new Array(5); //创建长度是5的数组,，但是其每一个元素都是undefine
p('通过 new Array(5)创建一个长度是5的数组:',x);
p('像new Array(5) 这样没有赋初值的方式创建的数组，每个元素的值都是:',x[0]);
x = new Array(3,1,4,1,5,9,2,6); //根据参数创建数组
p('创建有初值的数组new Array(3,1,4,1,5,9,2,6) :',x);
 
</script>
```

通过 new Array()创建一个空数组:
通过 new Array(5)创建一个长度是5的数组: ,,,,
像new Array(5) 这样没有赋初值的方式创建的数组，每个元素的值都是: undefined
创建有初值的数组new Array(3,1,4,1,5,9,2,6) : 3,1,4,1,5,9,2,6

### 遍历一个数组

遍历有两种方式
1.结合for循环，通过下标遍历
2.使用增强for in循环遍历
需要注意的是，在增强for in中，i是下标的意思。



```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var x = new Array(3,1,4);
p('当前数组是:'+x);
p("使用普通的for循环遍历数组");
for(i=0;i<x.length;i++){  //普通for循环
  p(x[i]);
}
p("使用增强for循环遍历数组");
for(i in x){  //for in 循环
  p(x[i]);
}
</script>
```

### 连接数组

方法 concat 连接两个数组

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
var x = new Array(3,1,4);
var y = new Array(1,5,9,2,6);
p('数组x是:'+x);
p('数组y是:'+y);
 
var z = x.concat(y);
p('使用concat连接数组x和y');
p('数组z是:'+z);
 
</script>
```

### 通过指定分隔符，返回一个数组的字符串表达

方法 join 通过指定分隔符，返回一个数组的字符串表达

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var x = new Array(3,1,4);
p('数组x是:'+x);
var y = x.join();
p('y = x.join() 得到的是数组x的字符串表达，其值是'+y+" 其类型是 :" +(typeof y));
var z = x.join("@");
p('z = x.join("@");是x的字符串表达，不过分隔符不是默认的"," 而是"@" : '+z);
 
</script>
```

数组x是:3,1,4
y = x.join() 得到的是数组x的字符串表达，其值是3,1,4 其类型是 :string
z = x.join("@");是x的字符串表达，不过分隔符不是默认的"," 而是"@" : 3@1@4

### 分别在最后的位置插入数据和获取数据(获取后删除)

方法 push pop,分别在**最后的位置**插入数据和获取数据(获取后删除)
就像**先入后出的栈**一样

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
var x = new Array(3,1,4);
p('数组x是:'+x);
 
x.push(5);
p('向x中push 5,得到 ' + x);
var e = x.pop();
p('从x中pop一个值出来，其值是 ' + e);
 
p('pop之后，x数组的值是:'+x);
 
</script>
```

数组x是:3,1,4
向x中push 5,得到 3,1,4,5
从x中pop一个值出来，其值是 5
pop之后，x数组的值是:3,1,4

### 自定义排序算法

sort()默认采用正排序，即小的数排在前面。 如果需要采用自定义排序的算法，就把比较器函数作为参数传递给sort()。
比较器函数:

```javascript
function comparator(v1,v2){
   return v2-v1;  //v2-v1表示大的放前面，小的放后面
}
```

调用sort函数的时候，把这个比较器函数comparator作为参数传递进去即可

```javascript
x.sort(comparator);
```

```javascript
<script>
function p(s){
  document.write(s);
  document.write("<br>");
}
 
function comparator(v1,v2){
   return v2-v1;
}
 
var x = new Array(3,1,4,1,5,9,2,6);
p('数组x是:'+x);
x.sort(comparator);
p('使用sort 进行自定义倒排序后的数组x是:'+x);
 
</script>
```

数组x是:3,1,4,1,5,9,2,6
使用sort 进行自定义倒排序后的数组x是:9,6,5,4,3,2,1,1

## 日期

| 关键字                                                      | 简介           | 示例代码                                                     |
| :---------------------------------------------------------- | :------------- | :----------------------------------------------------------- |
| new Date                                                    | 创建日期对象   | [示例代码](https://how2j.cn/k/javascript/javascript-date/440.html#step1150) |
| getFullYear getMonth getDate                                | 年/月/日       | [示例代码](https://how2j.cn/k/javascript/javascript-date/440.html#step1151) |
| getHours getMinutes getSeconds getMilliseconds              | 时:分:秒:毫秒  | [示例代码](https://how2j.cn/k/javascript/javascript-date/440.html#step1152) |
| getDay                                                      | 一周的第几天   | [示例代码](https://how2j.cn/k/javascript/javascript-date/440.html#step1153) |
| getTime                                                     | 经历的毫秒数   | [示例代码](https://how2j.cn/k/javascript/javascript-date/440.html#step1154) |
| setFullYear setMonth setDate setHours setMinutes setSeconds | 修改日期和时间 |                                                              |

### 年月日

分别获取年/月/日
需要注意的是，getMonth()返回的月数，**是基零的**，0代表1月份

```javascript
<script>
  var d = new Date();
  document.write('分别获取年月日: ');
  document.write(d.getFullYear());
  document.write("/");
  document.write(d.getMonth()+1);
  document.write("/");
  document.write(d.getDate());
</script>
```

### 一周的第几天

通过getDay()获取，今天是本周的第几天
与getMonth()一样，返回值是基0的。

```javascript
<script>
var day=new Date().getDay(); //通过日期对象获取数字形式的星期几
var weeks = new Array("星期天","星期一","星期二","星期三","星期四","星期五","星期六");
 
document.write("今天是 ： "+weeks[day]);
  
</script>
```

## Math

| 关键字                     | 简介                                 | 示例代码                                                     |
| :------------------------- | :----------------------------------- | :----------------------------------------------------------- |
| 属性E PI                   | 自然对数和圆周率                     | [示例代码](https://how2j.cn/k/javascript/javascript-math/520.html#step1142) |
| 方法 abs()                 | 绝对值                               | [示例代码](https://how2j.cn/k/javascript/javascript-math/520.html#step1143) |
| 方法 min(1,100) max(1,100) | 最小最大                             | [示例代码](https://how2j.cn/k/javascript/javascript-math/520.html#step1144) |
| 方法 pow(3,3) =9           | 求幂方法 pow 求一个数的n次方         | [示例代码](https://how2j.cn/k/javascript/javascript-math/520.html#step1145) |
| 方法 round                 | 四舍五入                             | [示例代码](https://how2j.cn/k/javascript/javascript-math/520.html#step1147) |
| 方法 random                | 随机数,方法 random 取0-1之间的随机数 |                                                              |

## 自定义对象

在JavaScript中可以自定义对象，添加新的属性，添加新的方法

```javascript
<script>
var hero = new Object();
hero.name = "盖伦"; //定义一个属性name，并且赋值
hero.kill = function(){
  document.write(hero.name + " 正在杀敌" ); //定义一个函数kill
}
  
hero.kill(); //调用函数kill
  
</script>
```

### 通过function设计一个对象

```javascript
通过new Object创建对象有个问题，就是每创建一个对象，都得重新定义属性和函数。这样代码的重用性不好
那么，采用另一种方式，通过function设计一种对象。 然后实例化它 。
这种思路很像Java里的设计一种类，但是 javascript没有类，只有对象，所以我们叫设计一种对象

<script>
function Hero(name){
  this.name = name;
  this.kill = function(){
     document.write(this.name + "正在杀敌<br>");
  }
}
 
var gareen = new Hero("盖伦");
gareen.kill();
 
var teemo = new Hero("提莫");
teemo.kill();
  
</script>
```

### 为已经存在的对象，增加新的方法

现在Hero对象已经设计好了，但是我们发现需要追加一个新的方法keng(),那么就需要通过prototype实现这一点

```javascript
<script>
function Hero(name){
  this.name = name;
  this.kill = function(){
     document.write(this.name + "正在杀敌<br>");
  }
}
  
var gareen = new Hero("盖伦");
gareen.kill();
  
var teemo = new Hero("提莫");
teemo.kill();
  
Hero.prototype.keng = function(){
  document.write(this.name + "正在坑队友<br>");
}
  
gareen.keng();
teemo.keng();
  
</script>
```

# BOM

## window

BOM即 浏览器对象模型(Browser Object Model)

浏览器对象包括
Window(窗口)
[Navigator(浏览器)](https://how2j.cn/k/javascript/javascript-bom-navigator/453.html)
[Screen (客户端屏幕)](https://how2j.cn/k/javascript/javascript-bom-screen/450.html)
[History(访问历史)](https://how2j.cn/k/javascript/javascript-bom-history/452.html)
[Location(浏览器地址)](https://how2j.cn/k/javascript/javascript-bom-location/451.html)

本章节从 Window(窗口)开始讲起

### 获取文档显示区域的高度和宽度

一旦页面加载，就会自动创建window对象，所以无需手动创建window对象。
通过window对象可以获取文档显示区域的高度和宽度

```javascript
<script>
  document.write("文档内容");
  document.write("文档显示区域的宽度"+window.innerWidth);
  document.write("<br>");
  document.write("文档显示区域的高度"+window.innerHeight);
</script>
```

### 获取外部窗体的宽度和高度

所谓的外部窗体即浏览器，可能用的是360，火狐，IE, Chrome等等。

```javascript
<script>
 
  document.write("浏览器的宽度:"+window.outerWidth);
  document.write("<br>");
  document.write("浏览器的高度:"+window.outerHeight);
 
</script>
```

### 打开一个新的窗口

有的时候，你碰到一些网站会自动打开另一个网站，那么是怎么做到的呢?
就是通过window的open方法做到的
**不建议使用**，如果需要打开一个新的网站，应该通过超级链接等方式让用户主动打开，在没有告知用户的前提下就打开一个新的网站会影响用户的体验

```javascript
<script>
function openNewWindow(){
  myWindow=window.open("/");
}
</script>
  
<button onclick="openNewWindow()">打开一个新的窗口</button>
```

## Navigator

Navigator即浏览器对象，提供浏览器相关的信息

### 打印浏览器相关信息

```javascript
<script type="text/javascript">
document.write("<p>浏览器产品名称：");
document.write(navigator.appName + "</p>");
 
document.write("<p>浏览器版本号：");
document.write(navigator.appVersion + "</p>");
 
document.write("<p>浏览器内部代码：");
document.write(navigator.appCodeName + "</p>");
 
document.write("<p>操作系统：");
document.write(navigator.platform + "</p>");
 
document.write("<p>是否启用Cookies：");
document.write(navigator.cookieEnabled + "</p>");
 
document.write("<p>浏览器的用户代理报头：");
document.write(navigator.userAgent + "</p>");
</script>
```

## Screen

Screen对象表示用户，的屏幕相关信息

返回用户的屏幕大小，以及可用屏幕大小

```javascript
<html>
<body>
<script type="text/javascript">
document.write("用户的屏幕分辨率: ")
document.write(screen.width + "*" + screen.height)
document.write("<br />")
document.write("可用区域大小: ")
document.write(screen.availWidth + "*" + screen.availHeight)
document.write("<br />")
</script>
</body>
</html>
```

## history

History用于记录访问历史

### 返回上一次的访问

```javascript
<script>
function goBack()
  {
     history.back();
  }
</script>
 
<button onclick="goBack()">返回</button>
```

### 返回上上次的访问

```javascript
<script>
function goBack()
  {
     history.go(-2); //-1表示上次，-2表示上上次，以次类推
  }
</script>
 
<button onclick="goBack()">返回上上次</button>
```

## Location

### 刷新当前页面

reload方法刷新当前页面

```javascript
<span>当前时间:</span>
<script>
  var d = new Date();
  document.write(d.getHours());
  document.write(":");
  document.write(d.getMinutes());
  document.write(":");
  document.write(d.getSeconds());
  document.write(":");
  document.write(d.getMilliseconds());
 
function refresh(){
  location.reload();
}
</script>
 
<br>
<button onclick="refresh()">刷新当前页面</button>
```

### 跳转到另一个页面

```javascript
<script>
function jump(){
  //方法1
  //location="/";
 
  //方法2
  location.assign("/");
   
}
</script>
 
<br>
<button onclick="jump()">跳转到首页</button>
```



### 其他属性

协议 location.protocol:https:
主机名 location.hostname:how2j.cn
端口号 (默认是80，没有即表示80端口)location.port:
主机加端口号 location.host: how2j.cn
访问的路径 location.pathname: /k/javascript/javascript-bom-location/451.html
锚点 location.hash:
参数列表 location.search:

## 弹出框

浏览器上常见的弹出框有
警告框，确认框，提示框 这些都是通过调用window的方法实现的。

比如警告框用的是window.alert("警告内容")，因为很常用，所以就把window省略掉，直接使用alert

| 关键字  | 简介   | 示例代码                                                     |
| :------ | :----- | :----------------------------------------------------------- |
| alert   | 警告框 | [示例代码](https://how2j.cn/k/javascript/javascript-bom-popup/454.html#step1166) |
| confirm | 确认框 | [示例代码](https://how2j.cn/k/javascript/javascript-bom-popup/454.html#step1167) |
| prompt  | 输入框 |                                                              |

### 警告框

```javascript
<script>
function register(){
   alert("注册成功");
}
</script>
  
<br>
<button onclick="register()">注册</button>
```

### 确认框

确认框 confirm，常用于危险性操作的确认提示。 比如删除一条记录的时候，弹出确认框
confirm返回基本类型的Boolean true或者false

```javascript
<script>
function del(){
var d = confirm("是否要删除");
alert(typeof d + " " + d);
}
</script>
  
<br>
<button onclick="del()">删除</button>
```

### 输入框

输入框 prompt，用于弹出一个输入框，供用户输入相关信息。 因为弹出的界面并不好看，很有可能和网站的风格不一致，所以很少会在实际工作中用到。

```javascript
<script>
function p(){
var name = prompt("请输入用户名:");
alert("您输入的用户名是:" + name);
}
</script>
  
<br>
<button onclick="p()">请输入用户名</button>
```

## 计时器

| 关键字           | 简介                                               | 示例代码                                                     |
| :--------------- | :------------------------------------------------- | :----------------------------------------------------------- |
| setTimeout       | 只执行一次                                         | [示例代码](https://how2j.cn/k/javascript/javascript-bom-timing/455.html#step1169) |
| setInterval      | 不停地重复执行                                     | [示例代码](https://how2j.cn/k/javascript/javascript-bom-timing/455.html#step1170) |
| clearInterval    | 终止重复执行                                       | [示例代码](https://how2j.cn/k/javascript/javascript-bom-timing/455.html#step1171) |
| document.write() | 不要在setInterval调用的函数中使用document.write(); |                                                              |

### 只执行一次

函数setTimeout(functionname, 距离开始时间毫秒数 );
通过setTimeout在制定的毫秒数时间后，**执行一次** 函数functionname
本例在3秒钟后，打印当前时间。
**解释:**
document.getElementById 获取id=time的div元素
.innerHTML 修改该元素的内容
更多的关于如何获取元素，请参考 [HTML DOM 获取元素](https://how2j.cn/k/dom/dom-fetch-node/458.html)

```javascript
<script>
  
function printTime(){
  var d = new Date();
  var h= d.getHours();
  var m= d.getMinutes();
  var s= d.getSeconds();
  document.getElementById("time").innerHTML= h+":"+m+":"+s;
  
}
 
function showTimeIn3Seconds(){
   setTimeout(printTime,3000); 
}
  
</script>
<div id="time"></div>
<button onclick="showTimeIn3Seconds()">点击后3秒钟后显示当前时间，并且只显示一次</button>
```

### 不停地重复执行

函数setInterval(函数名, 重复执行的时间间隔毫秒数 );
通过setInterval**重复执行同一个函数**，重复的时间间隔由第二个参数指定

```javascript
<p>每隔1秒钟，打印当前时间</p>
   
<div id="time"></div>
   
<script>
   
function printTime(){
  var d = new Date();
  var h= d.getHours();
  var m= d.getMinutes();
  var s= d.getSeconds();
  document.getElementById("time").innerHTML= h+":"+m+":"+s;
   
}
   
var t = setInterval(printTime,1000);
   
</script>
 
<br><br>
```

### 终止重复执行

通过clearInterval终止一个不断重复的任务
本例，当秒是5的倍数的时候，就停止执行

```javascript
<p>每隔1秒钟，打印当前时间</p>
   
<div id="time"></div>
   
<script>
   
var t = setInterval(printTime,1000);
 
function printTime(){
  var d = new Date();
  var h= d.getHours();
  var m= d.getMinutes();
  var s= d.getSeconds();
  document.getElementById("time").innerHTML= h+":"+m+":"+s;
  if(s%5==0)
     clearInterval(t);
}
   
</script>
<br>
```

### 不要在setInterval调用的函数中使用document.write();

**注：**部分浏览器，比如firefox有这个问题，其他浏览器没这个问题。

假设setInterval调用的函数是printTime, 在printTime中调用document.write();
只能看到一次打印时间的效果。
这是因为document.write，会创建一个新的文档，而新的文档里，只有打印出来的时间字符串，并没有setInterval这些javascript调用，所以只会看到执行一次的效果。

```javas
<p>每隔1秒钟，通过document.write打印当前时间</p>
 
<script>
 
function printTime(){
  var d = new Date();
  document.write(d.getHours());
  document.write(":");
  document.write(d.getMinutes());
  document.write(":");
  document.write(d.getSeconds());
  document.close();
}
 
var t = setInterval(printTime,1000);
 
</script>
```


