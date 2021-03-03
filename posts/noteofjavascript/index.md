# JavaScript高级程序设计读书笔记


## 第1章 JavaScript简介

JavaScript是一种专门为与网页交互而设计的脚本语言，由三个不同的部分组成

- ECMAscript,由ECMA-262定义，提供核心语言

- 文档对象模型(DOM),提供访问和操作网页内容的方法和接口
- 浏览器对象模型(BOM),提供与浏览器交互的方法和接口

## 第2章 在HTML中使用JavaScript

### 2.1 <script>元素

向HTML中插入JavaScript的主要方法，用该标签

1. 所有的<script>标签会按照在页面的出现顺序执行。在不使用defer和async属性的情况下，只有在解析完<script>后才会执行后面代码
2. 浏览器会先解析不使用defer的代码，所以一般把<script>标签。放在主要内容最后,即</body>前
3. 使用defer属性可以让脚本在文档完全呈现之后在执行
4. 使用async可以表示当前脚本不必等待其他脚本

## 第3章 基本概念

### 3.1 语法

1.  区分大小写
2.  标识符-  第一个字符必须是一个字母，下划线(_)或一个美元符号($). 其他字符可以是字母，下划线，美元符号或数字
3.  严格模式- 一些不确定的行为将得到处理，而且对于某些不安全错误也会抛出提示：用法"use strict";

### 3.2 关键字和保留字

### 3.3 变量

EMCAScript中变量是松散类型的，可以用来保存任何类型的变量

### 3.4 数据类型

5种简单数据类型：Undefined, Null, Boolean, Number, String.一种复杂数据类型:Object

typeof 操作符用法

```javascript
var message = "some";
alert (typeof message); //"String"
alert (typeof (messge)); //"String". 括号可以使用，但不是必须
alert (typeof 95); //"number"
alert (typeof function()); function--值是函数
alert (typeof object); 值是对象或null       
```

**Boolean**

所有类型都可以转换为boolean类型，用方法Boolean()，该类型只有两个字面值: true, false. 两个字面值区分大小写。

```javascript
var message = "Hello world!";
var messageAsBoolean = Boolean(message);

```

**Number**

最基本的是十进制

```js
var intNum = 55;
```

八进制字面值第一位必须是0， 然后是8进制数字序列（0-7）如果字面值超出了范围，前导0会被忽略，后面的值会当成当作十进制解析

```js
var Num1 = 070  //8进制的86
var Num2 = 079 //无效的8进制，解析为79
var Num3 = 08  //无效的8进制，解析为8
```

十六进制字面值前两位必须是0x， 后跟任何16进制数字（0-9，A-F）字母A-F可以小写

```js
var hexNum1 = 0xA  //十进制的10
var hexNum2 = 0x1F  //十进制的31
```

在进行算数计算，所有8，16进制都会转换为10进制

1. 浮点数值

数值中必须包含一个小数点，小数点后必须有一个数字

```js
var floatNum1 = 1.1;
var floatNum2 = 0.1;
var floatNum3 = .1; //有效不推荐
```

由于保存浮点数值需要的内存空间是保存整数值的两倍，ECMAScript会不失时机的把浮点转换为整数

```js
var floatNum1 = 1.;  //小数点后没有数字解析为1
var floatNum2 = 10.0;  //整数--解析为10

```

浮点数的最高精度是17位小数，但进行算数时精度不如整数。例如0.1+0.2的结果不是0.3 而是0.30000000000000004

2. 数值范围

超出的数值会被转换为-Infinity, Infinity. 后面无法参加下一次运算

3. NaN

NAN(Not a Number) 是一个特殊的数值，用来表示本来要返回数值的操作数值未返回的情况。例如在其他编程语言中任何数字/0 会返回错误，但在ECMAScript中，结果返回NaN，不会影响其他代码执行

任何涉及NaN的操作会返回NaN，NaN与任何值都不相等包括NaN。

处理整数的时候更常用的是parseInt()函数，在转换字符串，会忽略字符串前面的空格，直到找到第一个非空格字符，如果第一个字符不是数字或负号，返回NaN

```js
var num1 = parseInt("1234blue");  //1234
var num2 = parseInt("");  //NaN
var num3 = parseInt("22.2") //22小数点不是有效数字字符
```

**String**

单双引号都相同

1. 字符字面量

转义字符

2. 字符串的特点

一但创建，字符串的值不可变

3. 转换为字符串

toString()方法，null和undefined没有这个方法

String(), null 返回“null”， undefined返回“undefined”

**Object**

 ```js
var o = new Object()；
 ```

### 3.5 操作符

**一元操作符**

后置递增和递减与前置递增和递减有一个非常重要的区别，后置递增是在包含他们的语句被求值之后才执行。

```js
var num1 = 2;
var num2 = 20;
var num3 = num1-- + num2;  //22
var num4 = num1 + num2;  //21
```

**位操作符**

位操作符不直接操作64位的值，首先将64位转换为32位然后执行操作，最后将结果转换为64位。注意负数使用的是二进制补码。

1. 换位非（NOT）~
2. 换位与（AND）&
3. 换位或（OR）|
4. 换位异或（XOR）^

换位异或在两个数值对应位上只有1时才会返回1，如果对应的两位都是1或0，则返回0

**左移**

符号（<<）会将数值的所有位向左移指定的位数，如果将数值2（二进制10）向左移动5位，结果64（二进制1000000）

```js
var oldValue = 2;
var newValue = oldValue << 5;
```

**有符号的右移**

符号（>>）操作符会将数值向右移动，与左移相反

**无符号右移**

符号（>>>）会将数值的所有32位都向右移动。对正数来讲，与有符号右移相同

对负数来讲，首先无符号右移是以0来填充空位，其次无符号右移会把负数的二进制码当成正数的二进制码，而且负数以其绝对值的二进制补码形式表示

**布尔操作值**

1. 逻辑非（！）

无论这个值是什么数据类型，都会转换为一个布尔值再求反。

2. 逻辑与（&&）
3. 逻辑或（||）

只要有一个true 就是true

**相等操作符**

1. 相等和不相等（==，!=）

这两个操作符都会先转换操作数（强制转型）

2. 全等和不全等（===，！==）

```js
var res1 = ("55" == 55); //true
var res2 = ("55" === 55); //false
```

**条件操作符**

```js
var max = (num1 > num2) ? num1 : num2;
```

**赋值操作符**

**逗号操作符**

var num1 = 1, num2 = 2, num3 = 3;

可以用于声明多个变量，还可以用于赋值，总会返回逗号表达式的最后一项。

var num = (5, 1, 4, 8, 0) //为0；

### 3.6 语句

**if语句**

**do-while语句**

**while**

**for语句**

**for-in**

用来枚举

```js
for (var propName in window) {
	document.write(propName);
}
```

**label**

**break, continue**

break: 立即退出循环，执行循环后的

continue：退出循环但从循环顶部继续执行

**with**

作用是将代码的作用域设置到一个特定的对象中

```js
var qs = location.search.substring(1);
var hostName = location.hostname;
var url = location.href;

with(location) {
    var qs = search.substring(1);
	var hostName = hostname;
	var url = href;
}
```

**switch**

### 3.7 函数

return 之后的语句都不会再执行

```js
function sum(num1,num2){
	return num1+num2;
	alert("Hello world"); //这一句永远不会执行
}
```

**理解参数**

ECMAScript 函数不介意传递进来多少个参数，也不介意什么类型。在函数体内可以通过arguments对象来访问参数数组

```js
function sayHi() {
	alert("Hello"+arguments[0]+","+arguments[1]);
}
```

**没有重载**

在其他语言中，可以为一个函数编写两个定义，只要这两个定义的签名不同（接受参数的类型和数量）即可。而ECMAScript没有函数签名，故无重载

如果定义了两个名字相同的函数，则该名字只属于后者

## 第4章 变量，作用域和内存问题

###  4.1 **基本类型和引用类型的值**

ECMAScript的变量可能包含两种不同类型的值：基本类型值指的是简单的数据段，比如“Undefined，Null，Boolean，Number，String”。引用类型指的是保存在内存中的对象

**动态的属性**

我们可以给引用类型的值添加和删除属性和方法，但是基本类型不行

，尽管不会发生错误。

```js
var person = new Object();
person.name = "Nicholas";
alert(person.name);  //"Nicholas"

-------------------------------
    
var name = "Nicholas";
name.age = 27;
alert(name.age);  //undefined
```

**复制变量值**

对于基本类型值来说，如果从一个变量向另一个变量复制基本类型的值，会在变量对象上创建一个新值，然后把该值复制到为新变量分配的位置上

```js
var num1 = 5;
var num2 = num1
```

num2的5 与num1的5是完全独立的，两个变量可以参与任何操作而不会互相影响

对于引用类型来说，当从一个变量向另一个变量复制引用类型的值时，同样也会将存储在变量对象中的值复制一份到为新变量分配的空间中，不同的是，这个值的副本是一个***指针*** ，而这个指针指向存储中的一个对象。复制结束后，**两个变量实际上将引用同一个对象**，因此改变其中一个变量，会影响另一个变量。

```js
var obj1 = new Object();
var obj2 = obj1;
obj1.name = "Nicholas";
alert(obj.name);  //"Nicholas"

```

**传递参数**

所有函数都是按值传递的，基本类型值的传递如同基本类型变量的复制一样，引用类型值的传递如同引用类型变量的复制一样。

在向参数传递基本类型的值时候，被传递的值会被复制给一个局部变量（即命名参数，就是arguments对象中的一个元素）在向参数传递引用类型的值时候，会把这个值在内存中的地址复制给一个局部变量，这个局部变量的变化会反映在函数的外部

```js
function addTen(num){
	num += 10;
	return num;
}
var count = 20;
var resukt = addTen(count);
alert(count);  //20,nothing changed
alert(result); //30
------
function setName(obj) {
    obj.name = "Nicholas";
}
var person = new Object();
setName(person);
alert(person.name);   //"Nicholas"
--------------
function setName(obj) {
    obj.name = "Nicholas"；
    obj = new Object();
    obj.name = "Greg";
}
var person = new Object();
setName(person);
alert(person.name);  //"Nicholas" 
```

**检测类型**

```js
typeof
instanceof

var s = "Nicholas";
alert(typeof s); //string
result = variable instanceof constructor
alert(person instanceof Object); //person 是 Object吗？
```

### 4.2 执行环境及作用域（*）

 **执行环境**是JS中最为重要的一个概念，执行环境定义了变量或函数有权访问的其他数据，决定了他们各自的行为。每个执行环境都有一个与之关联的**变量对象** 环境中定义的所有变量和函数都保存在这个对象中。

每个函数都有自己的执行环境，当执行流进入一个函数时，函数的环境就会被推入一个环境栈，在函数执行之后，栈将其环境弹出，把控制权返回给之前的执行环境。

当代码在一个环境中执行，会创建变量对象的一个**作用域链（scope chain）** ,作用域链的用途是保证对执行环境有权访问的所有变量和函数的有序访问。作用域链的前端，始终都是当前执行的代码所在环境的变量。

**延长作用链**
当执行流进入下列任何一个语句时，作用域链会加长

try-catch语句的catch块

with语句 

**没有块级作用域**

```js
for (var i=10; i < 10; i++) {
	doSomething(i);
}
alert(i);  //10
```

对有块级作用域的语言来说for语句初始化变量的表达式所定义的变量，只会存在于循环境中，但对于js来说变量i在for结束依旧存在循环外部环境

1. 声明变量

使用var声明的变量会自动被添加到最接近的环境中，如果初始变量没用var声明，该变量会自动被添加到函数环境中。

```js
function add(num1,num2) {
	var sum = num1+num2;
	return sum;
}
var result = add(10,20);
alert(sum); //sum不是有效变量，会导致错误

-------
function add(num1,num2) {
	sum = num1+num2;
	return sum;
}
var result = add(10,20);
alert(sum); //30
```



2. 查询标识符

```js
var color = "blue";
function getColor(){
	return color;
}
alert(getColor()); //blue

----
var color = "blue";
function getColor(){
    var color = "red"
	return color;
}
alert(getColor()); //red

```

### 4.3 垃圾收集

局部变量只在函数执行的过程中存在 ,在这个过程中会为局部变量在栈或堆内存上分配相应的空间，直到函数执行结束

**标记清除**

当变量进入环境时，就将这个变量标记为“进入环境”，永远不能释放进入环境的变量所占用的内存，而当变量离开环境时，则将其标记为“离开环境”。

**引用计数**

跟踪记录每一个值被引用的次数。当声明一个变量并将一个引用类型赋值给该变量时，这个值的引用次数是1，如果同一个值又被赋给另一个变量，该值引用次数加1. 相反，如果包含对这个值又取得另外一个值，这个值的引用次数减一。当这个值的引用次数变成0时，则说明没有办法，则说明没有办法再访问这个值了。

## 第5章 引用类型

引用类型的值是引用类型的实例，在ECMAScript中，引用类型是一种数据结构，也被称为类

### 5.1 Object类型

创建Object实例的方式有两种，第一种是使用new操作符

```js
var person = new Object();
person.name = "Nicholas";
person.age = 22;
```

还有一种是使用对象字面量表示法，目的在于简化创建包含大量属性的对象的过程。

```js
var preson = {
	name: "Nicholas",
	age: 28
};

```

一般来说，访问对象时都是点表示法，在js中也可以使用方括号表示法来访问对象属性，应将要访问的属性以字符串形式放在方括号中。

```js
alert(person["name"]);  //"Nicholas"
alert(person.name); //"Nicholas"
```

### 5.2 Array类型

创建数组有两种方式，第一种是使用Array构造函数

```js
var color = new Array();
var color = new Array(4);
var color = new Array("red","blue","green");
var color = Array(3); //new 可省略
```

第二种基本方式是使用数组字面量表示法

```js
var colors = ["red", "blue","green"];  
var name = [];  //空数组
var value = [1,2,] //不要这样
```

数组的length属性很有特点--他 不只是只读的，可以通过设置属性，可以从数组的末尾移除项或添加新项。

```js
var colors = ["red", "blue","green"];  
colors.length = 2;
alert(colors[2]);  //undefined
```

新增的一项会取得undefined值

```js
var colors = ["red", "blue","green"];  
colors.length = 4;
alert(colors[3]);  //undefined
```

**转换方法**

所有对象都有 toLocaleString(), toString()和valueOf()方法。toString()方法返回以逗号分隔的字符串，而valueOf()返回的还是数组

**栈方法**

栈是一种后进先出的数据结构

push方法可以接受任意数量的参数，把他们逐个添加到数组末尾，并返回修改后的数组长度，

pop方法则从数组末尾移除最后一项，减少数组的length值，然后返回移除的项

```js
var colors = new Array();
var count = colors.push("red","blue");
alert(count);  //2

count = colors.push("black");
alert(count);   //3

var item = colors.pop();
alert(item);  //"black"
alert(colors.length); //2
```

**队列方法**

队列是先进先出

shift()方法能够移除数组中的第一个项并返回该项，同时长度减一

```js
var colors = new Array();
var count = color.push("red","green");
var item = colors.shift();
alert(item);  //"red"
```

unshift()方法能在数组前端添加任意项并返回新数组的长度。

```js
var colors = new Array();
var count = colors.unshift("red","green");
alert(count);  //2
count = colors.unshift("black");
alert(count); //3
```

数组中各项的顺序为“black”,"red","green"

**重排序方法**

数组中已经存在两个可以直接用重排序的方法：reverse(),sort()

```js
var values = [1,2,3,4,5];
values.reverse();
alert(values);  //5,4,3,2,1
```

sort()方法按升序排序数组项。 先调用每个数组项的toString()转型方法，然后比较得到的字符串，即使数组的每一项都是数值，sort()方法比较的也是字符串。

```js
var values = [0,1,5,15,10];
values.sort();
alert(values); //[ 0, 1, 10, 15, 5 ]
```

sort()函数再加上比较函数可保持正确的升序

```js
function compare(value1, value2) {
	if (value1 < value2) {
		return -1;
	} else if (value1 > value2) {
		return 1;
	} else {
		return 0;
	}
}

var values = [0,1,5,10,15];
values.sort(compare);
alert(values);  //0,1,5,10,15
```

**操作方法**

concat()方法：如果没有传递参数，只是复制当前数组并返回副本，如果有值或参数，则添加到结果数组中。

```js
var colors = ["red","green","blue"];
var colors2 = colors.concat("yellow",["black","brown"]);
alert(colors);  //red,green,blue
alert(colors2);  //red,green,blue,yellow,brown
```



slice()方法：能够基于当前数组的一个或多个项创建一个新数组。slice()可以接受一个或两个参数,即要返回项的起始位置和结束位置

```js
var colors = ["red","green","blue","yellow","purple"];
var colors2 = colors.slice(1);
var colors3 = colors.slice(1,4);
alert(colors2) //green,blue,yellow,purple
alert(colors3) //green,blue,yellow
```

splice()方法主要用途是向数组的中部插入项，使用这种方法的方式有3种。

删除：可以删除任意数量的项，只需要指定2个参数：要删除的第一项位置和要删除的项数，比如：splice(0,2)会删除数组中的前两项、

插入： 可以向指定位置插入任意数量的项，只需提供3个参数：起始位置，0（要删除的项数）和要插入的项。例如`splice(2,0,"red","green")`会从当前数组的位置2开始插入字符串“red”，“green”

替换： 可向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定3个参数起始位置，要删除的项数和要插入的任意数量的项，插入的项数不必与删除的项数相等

```js
var colors = ["red","green","blue"];
var removed = colors.splice(0,1);  //删除第一项
alert(colors);   //green,blue
alert(removed);  //red

removed = colors.splice(1,0,"yellow","orange");//从位置1开始插入两项
alert(colors);  //green,yellow,orange,blue
alert(removed); //返回的是一个空数组

removed = colors.splice(1,1,"red","purple");  //插入两项，删除一项
alert(colors);  //green,red,purple,orange,blue
alert(removed); //yellow

```



**位置方法**

indexOf(), lastIndexOf()

**迭代方法**



**归并方法**

### 5.3 Date类型

var now = new Date();

### 5.4 RegExp类型

var expression =  /pattern/flags;

其中pattern是正则表达式，每个正则表达式都可以带一个或多个标志（flags）用以表明正则表达式的行为：

g：表示全局模式，该模式被应用于所有字符串

i：不区分大小写模式

m：表示多行模式，即在到达一行文本末尾时还会继续查找下一行是否存在与模式匹配的项。

### 5.5 Function类型

函数名是对象，因此函数名实际上也是一个指向函数对象的指针，不会与某个函数绑定

**没有重载**

```js
var addSomeNumber = function (num) {
	return num + 100;
}

addSomeNumber = function (num) {
	return num + 200;
}
```

在创建第二个函数的，实际上覆盖了引用第一个函数的变量

**函数声明与函数表达式**

解释器在向执行环境中加载数据时，会率先读取函数声明，并使其在执行任何代码之前可用；函数表达式，等到解析器执行到它所在的代码行，才会真正被执行

```js
alert(sum(10,10));
function sum(num1,num2){
	return num1+num2;
}
```

以上代码完全可以执行，在代码执行之前，解析器已经通过函数声明的提升过程，读取并将函数声明添加到执行。

如果将函数声明改为函数表达式，出现错误

```js
alert(sum(10,10));
var sum = function(num1,num2){
	return num1+num2;
}
```

**作为值的函数**

因为函数名本来就是变量，所以函数也可以作为值来使用。

**函数内部属性**



**函数的属性和方法**

length属性可以表示函数希望接受的命名参数个数

```js
function sum(num1, num2) {
	return num1+num2;
}
alert(sum.length);  //2
```

### 5.6基本包装类型

String，Boolean，Number

### 5.7 单体内置对象

由ECMAScript实现提供的，不依赖宿主环境的对象，这些对象在ECMAScript程序执行之前就已经存在了

**eval()**方法

就像一个完整的ECMAScript解析器，他接受一个参数，即要执行的ECMAScript字符串

eval("alert('hi')");

等价于

alert("hi");

**Global对象的属性**



**window对象**

**Math**对象

## 第6章 面向对象的程序设计

对象定义：无序属性的集合，其属性可以包含基本值，对象或者函数。

每个对象都是基于一个引用类型创建的

对象字面量语法：

```js
var person = {
	name: "Nicholas",
	age: 29,
	job: "Software Engineer",
	
	sayName: function() {
		alert(this.name);
	}
}
```

### 6.1 理解对象

**属性类型**

1. 数据属性

[[Configurable]]: 表示能否通过delete删除属性从而从而重新定义属性，能否把属性修改为访问器属性

[[Enumerable]]: 能否通过for-in 循环返回属性。

[[Writable]]: 表示能否修改属性的值

[[Value]]:包含这个属性的数据值

要修改属性默认属性属性，必须使用Object.defineProperty()方法，接收三个参数，属性所在的对象，属性的名字和一个描述符对象（以上的属性）

```js
var person = {};
Object.defineProperty(person,"name",{
	writable: false,
	value: "Nicho"
});
alert(person.name);//"Nicho"
person.name = "Grog";
alert(person.name);//"Nicho"
```

2. 访问器属性

不包含数据值，包含getter和setter属性

[[Configurable]]: 表示能否通过delete删除属性从而重新定义属性，能否修改属性的特性，或者能否把属性修改为数据属性,默认true

[[Enumerable]]:表示能否通过for-in循环，默认true

[[Get]]:读取属性时调用的函数

[[Set]]:写入属性时调用的函数

通过Object.defineProperty()定义

```js
var book = {
	_year: 2004,
	edition: 1
};
Object.defineProperty(book,"year", {
	get: function(){
		return this._year;
	},
	set: function(newValue) {
		if(newValue>2004) {
			this._year = newValue;
			this.edition += newValue - 2004;
		}
	}

});
book.year = 2005;
alert(book.edition); //2
```

**定义多个属性**

Object.defineProperties()

**读取属性的特性**

```js
var descriptor = Object.getOwnPropertyDescriptor(book,"_year");
alert(descriptor.value);//2004
alert(descriptor.configurable); //false
```

### 6.2 创建对象

**工厂模式**

 ```js
function createPerson(name,age,job) {
	var o = new Object();
	o.name = name;
	o.age = age;
	o.job = job;
	o.sayName = function(){
		alert(this.name);
	};
	return o;
}
var person1 = createPerson("Nicholas",29,"Software Engineer");
 ```

**构造函数模式**

```js
function Person(name, age, job){
	this.name = name;
	this.age = age;
	this.job = job;
	this.sayName = function(){
        alert(this.name);
    };
}
var person1 = new Person("Nicho",29,"Software Engineer");
```

与工厂模式不同：

1. 没有显式的创建对象
2. 直接将属性和方法赋予给this对象
3. 没有return语句

**原型模式**

我们创建的每一个函数都有一个prototype属性，这个属性是一个指针，指向一个对象，而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法，好处是可以让所有对象实例共享它所包含的属性和方法
