# 

## 节点概念

DOM 是Document Object Model( 文档对象模型 )的缩写。

DOM是把html里面的各种数据当作对象进行操作的一种思路。

比如一个超链，作为一个DOM对象，就可以使其隐藏，修改其href指向的地址。

DOM把所有的html都转换为节点
**整个文档** 是一个节点
**元素** 是节点
**元素属性** 是节点
**元素内容** 是节点
**注释** 也是节点
如本例
通过document.getElementById获取了id=d1的**div标签**对应的**元素节点**
然后通过**attributes** 获取了该节点对应的**属性节点**
接着通过**childNodes**获取了**内容节点**

```html
<html>
<body>
<div id="d1">hello HTML DOM</div>
  
</body>
  
<script>
function p(s){
    document.write(s);
    document.write("<br>");
}
var  div1 = document.getElementById("d1");
p("文档节点"+document);
p("元素"+div1);
p("属性节点"+div1.attributes[0]);
p("内容节点"+div1.childNodes[0]);
</script>
  
</html>
```

```
hello HTML DOM
文档节点[object HTMLDocument]
元素[object HTMLDivElement]
属性节点[object Attr]
内容节点[object Text]
```

## 获得节点

| 关键字                  | 简介                           | 示例代码                                                     |
| :---------------------- | :----------------------------- | :----------------------------------------------------------- |
| document.getElementById | 通过id获取元素节点             | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step953) |
| getElementsByTagName    | 通过标签名称获取元素节点       | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step954) |
| getElementsByClassName  | 通过类名获取元素节点           | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step955) |
| getElementsByName       | 通过表单元素的name获取元素节点 | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step2963) |
| null                    | 为什么会获取不到?              | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step1188) |
| attributes              | 获取属性节点                   | [示例代码](https://how2j.cn/k/dom/dom-fetch-node/458.html#step2958) |
| childNodes              | 获取内容节点                   |                                                              |

## 节点的属性

| 关键字             | 简介           | 示例代码                                                     |
| :----------------- | :------------- | :----------------------------------------------------------- |
| nodeName           | 节点名称       | [示例代码](https://how2j.cn/k/dom/dom-attribute/459.html#step1175) |
| nodeValue          | 节点值         | [示例代码](https://how2j.cn/k/dom/dom-attribute/459.html#step1176) |
| nodeType           | 节点类型       | [示例代码](https://how2j.cn/k/dom/dom-attribute/459.html#step1177) |
| innerHTML          | 元素的文本内容 | [示例代码](https://how2j.cn/k/dom/dom-attribute/459.html#step1178) |
| id value className | 元素上的属性   |                                                              |

### 节点名称

nodeName表示一个节点的名字
如本例：
document.nodeName 文档的节点名，是 **固定的#document**
div1.nodeName 元素的节点名，是**对应的标签名** div
div1.attributes[0].nodeName 属性的节点名，是**对应的属性名** id
div1.childNodes[0].nodeName 内容的节点名，是**固定的 #text**

```html
<html>
  
<div id="d1">hello HTML DOM</div>
<script>
function p(s){
    document.write(s);
    document.write("<br>");
}
var  div1 = document.getElementById("d1");
p("document的节点名称:"+document.nodeName);
p("div元素节点的节点名称:"+div1.nodeName);
p("div下属性节点的节点名称:"+div1.attributes[0].nodeName);
p("div下内容节点的节点名称:"+div1.childNodes[0].nodeName);
</script>
</html>
```

hello HTML DOM

document的节点名称:#document
div元素节点的节点名称:DIV
div下属性节点的节点名称:id
div下内容节点的节点名称:#text

### 节点值

nodeValue表示一个节点的值
如本例：
document.nodeValue 文档的节点值，是 **null**
div1.nodeValue 元素的节点值，是**null**
div1.attributes[0].nodeValue 属性的节点值，是对应的**属性值** d1
div1.childNodes[0].nodeValue 内容的节点值，是**内容** 即： #text

```javascript
<html>
   
<div id="d1">hello HTML DOM</div>
<script>
function p(s){
    document.write(s);
    document.write("<br>");
}
var  div1 = document.getElementById("d1");
p("document是没有nodeValue的："+document.nodeValue);
p("元素节点是没有nodeValue的："+div1.nodeValue);
p("属性节点id的nodeValue："+div1.attributes[0].nodeValue);
p("内容节点的nodeValue："+div1.childNodes[0].nodeValue);
</script>
</html>
```



hello HTML DOM

document是没有nodeValue的：null
元素节点是没有nodeValue的：null
属性节点id的nodeValue：d1
内容节点的nodeValue：hello HTML DOM

### 节点类型

nodeType表示一个节点的类型
不同的节点类型，对应的节点类型值是不一样的
如本例：
document.nodeType 文档的节点类型，是 **9**
div1.nodeType 元素的节点类型，是 **1**
div1.attributes[0].nodeType 属性的节点类型，是 **2**
div1.childNodes[0].nodeType 内容的节点类型，是 **3**

![节点类型](/Volumes/Untitled 1/笔记/前端/img/节点类型png.png)

### 元素的文本内容

修改与获取内容的值可以通过 **childNodes[0].nodeValue**进行
还有个简便办法就是通过**innerHTML**进行。 效果是一样的。

```javascript
<html>
    
<div id="d1">hello HTML DOM</div>
<script>
 
function changeDiv1(){
  document.getElementById("d1").childNodes[0].nodeValue= "通过childNode[0].value改变内容";
}
function changeDiv2(){
  document.getElementById("d1").innerHTML= "通过innerHTML改变内容";
}
</script>
 
<button onclick="changeDiv1()">通过内容节点方式改变div的内容</button>
<button onclick="changeDiv2()">通过innerHTML改变div的内容</button>
 
</html>
```

### 元素上的属性

元素上的属性，比如id,value 可以通过 . 直接访问
如果是自定义属性，那么可以通过如下两种方式来获取

```javascript
getAttribute("test")
attributes["test"].nodeValue
```

## 样式

一个元素节点的style属性即对应的css

### 隐藏和显示

通过给元素的**style.display** 赋值，改变显示还是隐藏

```javascript
<button onclick="hide()">隐藏div</button>
  
<button onclick="show()">显示div</button>
  
<br>
<br>
  
<div id="d">
  
这是一个div
  
</div>
  
<script>
function hide(){
 var d = document.getElementById("d");
 d.style.display="none";
}
  
function show(){
 var d = document.getElementById("d");
 d.style.display="block";
}
  
</script>
```

### 改变背景色

通过给元素的**style.backgroundColor** 赋值，修改样式
你也许注意到了style.backgroundColor 这里的**backgroundColor**和[css中的背景色background-color](https://how2j.cn/k/css2/css2-backgroud/242.html#step461) 是有所不同的
换句话说，通过DOM的style去修改样式，需要重新记忆另一套样式名称，这是很累赘的事情。
最好能够通过[CSS](https://how2j.cn/k/css2/css2-tutorial/238.html)的属性名，直接就进行修改了。比如通过这样的方式：

d1.css("background-color","green");

```javascript
<div id="d1" style="background-color:pink">Hello HTML DOM</div>
 
<button onclick="change()">改变div的背景色</button>
 
<script>
function change(){
  var d1 = document.getElementById("d1");
  d1.style.backgroundColor="green";
}
</script>
```

## 事件

DOM的事件有很多，下表把工作中常用的事件列出来，并进行讲解

| 关键字                                       | 简介           | 示例代码                                                     |
| :------------------------------------------- | :------------- | :----------------------------------------------------------- |
| onfocus onblur                               | 焦点事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1189) |
| onmousedown onmouseup onmousemove onmouseout | 鼠标事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1190) |
| onkeydown onkeypress onkeyup                 | 键盘事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1191) |
| onclick ondblclick                           | 点击事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1192) |
| onchange                                     | 变化事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1193) |
| onsubmit                                     | 提交事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1194) |
| onload                                       | 加载事件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1195) |
| this                                         | 当前组件       | [示例代码](https://how2j.cn/k/dom/dom-event/464.html#step1204) |
| return false                                 | 阻止事件的发生 |                                                              |

### 焦点事件

```javascript
<input type="text" onfocus="f()" onblur="b()" id="input1" placeHolder="输入框1" >
<br>
<br>
<input type="text" id="input2" placeHolder="输入框2">
<br>
<br>
<div id="message"></div>
 
<script>
function f(){
 document.getElementById("message").innerHTML="输入框1获取了焦点";
}
 
function b(){
 document.getElementById("message").innerHTML="输入框1丢失了焦点";
}
 
</script>
```

### 鼠标事件

鼠标事件，由鼠标按下，鼠标弹起，鼠标经过，鼠标进入，鼠标退出几个事件组成
当在组件上**鼠标按下**的时候，会触发**onmousedown**事件
当在组件上**鼠标弹起**的时候，会触发**onmouseup**事件

当在组件上**鼠标经过**的时候，会触发**onmousemove**事件
当在组件上**鼠标进入**的时候，会触发**onmouseover**事件
当在组件上**鼠标退出**的时候，会触发**onmouseout**事件
**注:** 当鼠标进入一个组件的时候，onmousemove和onmouseover都会被触发，区别在于无论鼠标在组件上如何移动，onmouseover只会触发一次，onmousemove每次移动都会触发

```css
<input type="button" onmousedown="down()" onmouseup="up()" value="用于演示按下和弹起" >
<br>
<br>
 
<input type="button" onmousemove="move()"  value="用于演示鼠标经过" >
<br>
<br>
 
<input type="button" onmouseover="over()" value="用于演示鼠标进入" >
<br>
<br>
 
<input type="button" onmouseout="out()" value="用于演示鼠标退出" >
 
<br>
<br>
<div id="message"></div>
  
<script>
var number = 0;
 
function down(){
document.getElementById("message").innerHTML="按下了鼠标";
}
  
function up(){
document.getElementById("message").innerHTML="弹起了鼠标";
}
 
function move(){
document.getElementById("message").innerHTML="鼠标经过次数:"+(++number);
}
 
function over(){
document.getElementById("message").innerHTML="鼠标进入次数:"+(++number);
}
 
function out(){
document.getElementById("message").innerHTML="鼠标退出";
number = 0;
}
 
</script>
```

### 键盘事件

键盘事件，由键盘按下keydown，键盘按下keypress,键盘弹起几个事件组成
当在组件上**键盘按下**的时候，会触发**onkeydown**事件
当在组件上**键盘按下**的时候，也会触发**onkeypress**事件
当在组件上**键盘弹起**的时候，会触发**onkeyup**事件
**注:** onkeypress 是当**按下并弹起**的组合动作，这个说法是**错误的**
都是用于表示键盘按下，onkeydown和onkeypress的区别在什么呢？
onkeydown
可以获取所有键，除了打印键Prts
可以获取用户是否点击了修饰键 (ctrl,shift,alt)
不能判断输入的是大写还是小写
onkeypress
只能获取字符键
不能获取用户是否点击了修饰键 (ctrl,shift,alt)
可以判断输入的是大写还是小写

**但是！** 在不同的浏览器上，以上规则是不成立的。说这些都**没有卵用**，你无法控制用户到底使用哪种浏览器。 所以，只要记得keydown和keypress都表示点下了键。。。即可

```javascript
“记得要先用鼠标选中该组件，然后敲击键盘”
<br>
<input type="button" onkeydown="down(event)" value="用于演示按下keydown" >
<br>
<br>
 
<input type="button" onkeypress="press(event)" value="用于演示按下keypress" >
<br>
<br>
 
<input type="button" onkeyup="up()" value="用于演示弹起" >
<br>
<br>
 
<div id="message">
  
</div>
  
<script>
var number =0;
function down(e){
 
var text = "按下了键" + e.keyCode;
if(e.shiftKey==1)
   text += " 并且按下了shift键";
 
document.getElementById("message").innerHTML=text ;
}
 
function up(){
document.getElementById("message").innerHTML="弹起了键盘";
}
 
function press(e){
var text = "按下了键" + e.keyCode;
if(e.shiftKey==1)
   text += " 并且按下了shift键";
 
document.getElementById("message").innerHTML=text ;
}
 
</script>
```

### 点击事件

点击事件，由单击，双击按两个事件组成
当在组件上**单击**的时候，会触发**onclick**事件
当在组件上**双击**的时候，会触发**ondblclick**事件
**注1**：在组件上，按下空格或则回车键也可以造成单击的效果，但是却不能造成双击的效果
**注2:** 自定义函数不要使用click()，这是保留函数名。

```javascript
<input type="button" onclick="singleClick()" ondblclick="doubleClick()"  value="用于演示单击和双击" >
 
<br>
<br>
<div id="message"></div>
  
<script>
function singleClick(){
document.getElementById("message").innerHTML="单击按钮";
}
  
function doubleClick(){
 
document.getElementById("message").innerHTML="双击按钮";
}
</script>
```

### 变化事件

当组件的值**发生变化**的时候，会触发**onchange**事件
**注**：对于输入框而言，只有在失去焦点的时候，才会触发onchange，所以需要点击一下"按钮" 造成输入框失去焦点

```javascript
<input type="text" id="t1" onchange="change()"  value="" >
  
<br>
<br>
<input type="button" value="令输入框失去焦点的按钮" >
<br>
<br>
<div id="message"></div>
   
<script>
function change(){
var message = document.getElementById("message");
var t1 = document.getElementById("t1");
message.innerHTML = "输入框的值变为了: "+ t1.value;
}
   
</script>
```

### 提交事件

可以在form元素上，监听提交事件
当form元素@提交的时候，会触发**onsubmit**事件
本例使用 [提交账号密码](https://how2j.cn/k/html/html-form/190.html#step360) 来进行演示

```css
<form action="/study/login.jsp" onsubmit="login()">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登录">
</form>
 
<script>
  function login(){
      alert("提交表单");
  }
</script>
```

### 加载事件

当整个文档加载成功，或者一个图片加载成功，会触发加载事件
当body元素或者img@加载的时候，会触发**onload**事件

```javascript
<script>
  function loadBody(){
document.getElementById("message1").innerHTML="文档加载成功";
  }
  function loadImg(){
document.getElementById("message2").innerHTML="图片加载成功";
  }
 
</script>
 
<body onload="loadBody()">
  <div id="message1"></div>
  <div id="message2"></div>
</body>
 
<img onload="loadImg()" src="https://how2j.cn/example.gif"/>
```

### 当前组件

this表示触发事件的组件，可以在调用函数的时候，作为参数传进去

```css
<input type="button" onclick="singleClick(this)" value="演示this的按钮1" >
<input type="button" onclick="singleClick(this)" value="演示this的按钮2" >
 
<br>
<br>
<div id="message"></div>
  
<script>
function singleClick(button){
var s = "被点击的按钮上的文本是: "+button.value;
document.getElementById("message").innerHTML=s;
}
 
</script>
```

### 阻止事件的发生

比如在提交一个表单的时候，如果用户名为空，弹出提示，并阻止原本的提交
\1. 在调用函数的时候，增加一个return
\2. 在函数中，如果发现用户名为空，则返回false
\3. 当onSubmit得到的返回值是false的时候，表单的提交功能就被取消了

```css
<form method="post" action="/study/login.jsp" onsubmit="return login()">
账号：<input id="name" type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登录">
</form>
  
<script>
  function login(){
   var name = document.getElementById("name");
   if(name.value.length==0){
     alert("用户名不能为空");
     return false;
   }
   return true;
    
  }
</script>
```

## 节点关系

| 关键字                                          | 简介                       | 示例代码                                                     |
| :---------------------------------------------- | :------------------------- | :----------------------------------------------------------- |
| ![img](https://how2j.cn/img/site/module/67.png) | 节点关系图                 | [示例代码](https://how2j.cn/k/dom/dom-children/523.html#step1186) |
| parentNode                                      | 父节点关系                 | [示例代码](https://how2j.cn/k/dom/dom-children/523.html#step1183) |
| previousSibling nextSibling                     | 同胞节点关系               | [示例代码](https://how2j.cn/k/dom/dom-children/523.html#step1184) |
| childNodes                                      | 子节点关系                 | [示例代码](https://how2j.cn/k/dom/dom-children/523.html#step1182) |
| childNodes children                             | childNodes和children的区别 |                                                              |

### 节点关系图

假设html代码如实例中，那么各个元素节点的关系如下:
d1 d2 d3 的**parentNode**是parentDiv
parentDiv的**firstNode**是 d1
parentDiv的**lastNode**是d3
d2的**previousSibling**是d1
d2的**nextSibling**是d3
parentDiv的**children**是 d1 d2 d3

```css
<div id="parentDiv">
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div>
</div>
```

### 父节点关系

```css
<html>
<body>
<script>
var node = null;
function showParent(){
   if(null==node)
      node = document.getElementById("d1");
    
   if(document == node)
      alert("已是根节点:document");
   else{
      alert(node.parentNode);
      node = node.parentNode;
   }
}
</script>
 
<div id="parentDiv">
   父Div的内容
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div></div>
 
<button onclick="showParent()">不断递归d1的父节点</button>
</body>
</html>
```

### 同胞节点关系

分别通过 **previousSibling**和**nextSibling**属性获取前一个，以及后一个同胞节点。
在本例中，首先获取d2元素节点
通过previousSibling获取前一个节点d1.
**注意** d1和d2标签是**紧挨着**的，所以d2前一个节点是d1。
通过nextSibling 获取后一个节点#text.
**注意** d2和d3**不是紧挨着** 标签之间有任何**字符、空白、换行**都会产生文本元素。 所以获取到的节点是#text.

```css
<script>
 
function showPre(){
    var d2 = document.getElementById("d2");
    alert(d2.previousSibling.innerHTML);
}
 
function showNext(){
    var d2 = document.getElementById("d2");
    alert(d2.nextSibling.nodeName);
}
</script>
  
<div id="parentDiv">
   父Div的内容
 <div id="d1">第一个div</div><div id="d2">第二个div</div>
<div id="d3">第三个div</div></div>
  
<button onclick="showPre()">获取d2的前一个同胞</button>
 
<button onclick="showNext()">获取d2的后一个同胞</button>
```

### 子节点关系

子节点关系有:
firstChild 第一个子节点
lastChild 最后一个子节点
childNodes 所有子节点
**注:**firstChild 如果父节点的开始标签和第一个元素的开始标签之间有**文本、空格、换行**，那么firstChild第一个子节点将会是**文本节点**，不会是第一个元素节点
**注:**lastChild 和firstChild同理。 在本例中故意让第3个元素的结束标签与div的结束标签**紧挨着**，所以最后一个子节点就是第三个标签
**注:** 子元素个数一共是6个。 因为parentDiv的子节点是 **文本节点接着一个元素节点**，重复3次。 所以一共是6个。

```javascript
<script>
function showfirst(){
   var div = document.getElementById("parentDiv");
   alert(div.firstChild.nodeName);
}
 
function showlast(){
   var div = document.getElementById("parentDiv");
   alert(div.lastChild.nodeName);
}
 
function showall(){
   var div = document.getElementById("parentDiv");
     alert(div.childNodes.length);
}
</script>
 
<div id="parentDiv">
   父Div的内容
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div></div>
 
<button onclick="showfirst()">第一个子节点</button>
<button onclick="showlast()">最后一个子节点</button>
<button onclick="showall()">所有子节点数量</button>
```

### childNodes和children的区别

**childNodes**和**children**都可以获取一个元素节点的子节点。
childNodes 会**包含**文本节点
children 会**排除**文本节点

```javascript
<div id="parentDiv">
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div></div>
 
<button onclick="showNumber1()">通过childNodes获取子节点总数</button>
 
<button onclick="showNumber2()">通过children()获取子节点总数</button>
 
<script>
 
function showNumber1(){
  alert(document.getElementById("parentDiv").childNodes.length);
}
 
function showNumber2(){
  alert(document.getElementById("parentDiv").children.length);
}
 
</script>
```

## 创建节点

| 关键字          | 简介         | 示例代码                                                     |
| :-------------- | :----------- | :----------------------------------------------------------- |
| createElement   | 创建元素节点 | [示例代码](https://how2j.cn/k/dom/dom-create/462.html#step958) |
| createTextNode  | 创建文本节点 | [示例代码](https://how2j.cn/k/dom/dom-create/462.html#step960) |
| createAttribute | 创建属性节点 |                                                              |

### 创建元素节点

通过**createElement** 创建一个新的元素节点
接着把该元素节点，通过**appendChild**加入到另一个元素节点div1中

```javascript
<html>
<div id="d">Hello HTML DOM</div>
<script>
function add(){
  var hr=document.createElement("hr");
  var div1 = document.getElementById("d");
  div1.appendChild(hr);
}
</script>
 
<button onclick="add()">在div中追加一个hr元素</button>
 
</html>
```

### 创建文本节点

首先创建一个元素节点p (p是p标签，不是随便命名的变量名)
接着通过**createTextNode**创建一个**内容节点**text
把text加入到p
再把p加入到div

```javascript
<html>
<div id="d">Hello HTML DOM</div>
<script>
function add(){
 
  var p=document.createElement("p");
  var text = document.createTextNode("这是通过DOM创建出来的<p>");
  p.appendChild(text);
 
  var div1 = document.getElementById("d");
  div1.appendChild(p);
 
}
</script>
  
<button onclick="add()">在div中追加一个p元素</button>
  
</html>
```

### 创建属性节点

首先创建一个元素节点a
接着创建一个内容节点content
把content加入到a
然后通过**createAttribute**创建一个**属性节点** href
设置href的值为http:12306.com
通过**setAttributeNode**把该属性设置到元素节点a上
最后把a加入到div

```javascript
<html>
<div id="d">Hello HTML DOM<br></div>
 
<script>
function add(){
  
  var a=document.createElement("a");
  var content = document.createTextNode("http://12306.com");
  a.appendChild(content);
 
  var href = document.createAttribute("href");
  href.nodeValue="http://12306.com";
  a.setAttributeNode(href);
 
  var div1 = document.getElementById("d");
  div1.appendChild(a);
}
</script>
   
<button onclick="add()">在div中追加一个超链</button>
   
</html>
```

## 删除节点

| 关键字          | 简介         | 示例代码                                                     |
| :-------------- | :----------- | :----------------------------------------------------------- |
| removeChild     | 删除元素节点 | [示例代码](https://how2j.cn/k/dom/dom-delete/461.html#step1179) |
| removeAttribute | 删除属性节点 | [示例代码](https://how2j.cn/k/dom/dom-delete/461.html#step1180) |
| removeChild     | 删除文本节点 |                                                              |

### 删除元素节点

要删除某个元素节点有两步
第一：先获取该元素的父节点
第二：通过父节点，调用**removeChild** 删除该节点

```javascript
<script>
function removeDiv(){
  var parentDiv = document.getElementById("parentDiv");
  var div2= document.getElementById("div2");
  parentDiv.removeChild(div2);
}
 
</script>
 
<div id="parentDiv">
  <div id="div1">安全的div</div>
  <div id="div2">即将被删除的div</div>
</div>
 
<button onclick="removeDiv()">删除第二个div</button>
```



### 删除属性节点

要删除某个属性节点有两步
第一：先获取该元素节点
第二：元素节点，调用**removeAttribute**删除指定属性节点

```javascript
<script>
function removeHref(){
  var link= document.getElementById("link");
  link.removeAttribute("href");
}
 
</script>
 
<a id="link" href="http://12306.com">http://12306.com</a>
 
<br>
<button onclick="removeHref()">删除超链的href属性</button>
```

### 删除文本节点

删除文本节点
\1. 通过childNodes[0] 获取文本节点
**注:**children[0] 只能获取第一个子元素节点，不能获取文本节点
\2. 通过removeChild删除该文本节点
但是这种方式比较麻烦，一般都是直接通过[innerHTML](https://how2j.cn/k/dom/dom-attribute/459.html#step1178)设置为空即可。
**注:** 通过innerHTML=""的方式，同样会导致文本子节点被删除。

```javascript
<script>
 
function removeDiv1(){
  var parentDiv = document.getElementById("parentDiv");
  var textNode = parentDiv.childNodes[0];
  parentDiv.removeChild(textNode);
}
function removeDiv2(){
  var parentDiv = document.getElementById("parentDiv");
  parentDiv.innerHTML="";
}
function recover(){
  var parentDiv = document.getElementById("parentDiv");
  parentDiv.innerHTML="这里是文本 ";
}
 
</script>
 
<style>
button{
display:block;
}
</style>
 
<div id="parentDiv">
   这里是文本
 
</div>
 
<button onclick="removeDiv1()">通过removechild删除div下的文本节点</button>
<button onclick="removeDiv2()">通过innerHTML让内容置空</button>
<button onclick="recover()">恢复内容</button>
```

## 替换节点

与[删除节点](https://how2j.cn/k/dom/dom-delete/461.html)一样，替换节点也需要先获取父节点，然后通过父节点替换子节点。
\1. 获取父节点
\2. 创建子节点
\3. 获取被替换子节点
\4. 通过replaceChild进行替换
注: **replaceChild** 第一个参数是保留的节点，第二个参数是被替换的节点

```javascript
<div id="parentDiv">
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div>
</div>
  
<script>
  
function replaceDiv(){
  var d4=  document.createElement("div");
  var text = document.createTextNode("第四个div");
  
  d4.appendChild(text);
  
  var d3 = document.getElementById("d3");
  
  var parentDiv = document.getElementById("parentDiv");
  
  parentDiv.replaceChild(d4,d3);
}
 
</script>
  
<button onclick="replaceDiv()">替换第3个div</button>
```

## 插入节点

| 关键字       | 简介           | 示例代码                                                     |
| :----------- | :------------- | :----------------------------------------------------------- |
| appendChild  | 追加节点       | [示例代码](https://how2j.cn/k/dom/dom-insert/463.html#step961) |
| insertBefore | 在前方插入节点 |                                                              |

### 追加节点

通过**appendChild**追加节点。 追加节点一定是把新的节点**插在最后面**
\1. 创建新节点
\2. 获取父节点
\3. 通过appendChild追加

```javascript
<div id="parentDiv">
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div>
</div>
   
<script>
   
function appendDiv(){
  var d4=  document.createElement("div");
  var text = document.createTextNode("第四个div");
  d4.appendChild(text);
   
  var parentDiv = document.getElementById("parentDiv");
   
  parentDiv.appendChild(d4);
}
  
</script>
   
<button onclick="appendDiv()">追加第4个div</button>
```

### 在前方插入节点

有时候，需要在指定位置插入节点，而不是只是[追加在后面](https://how2j.cn/k/dom/dom-insert/463.html#step961)。
这个时候就需要用到**insertBefore**
\1. 创建新节点
\2. 获取父节点
\3. 获取需要加入的子节点
\4. 通过insertBefore插入
**注:** insertBefore的第一个参数是新元素，第二个参数是插入位置

```javascript
<div id="parentDiv">
 <div id="d1">第一个div</div>
 <div id="d2">第二个div</div>
 <div id="d3">第三个div</div>
</div>
   
<script>
   
function insertDiv(){
  var d25=  document.createElement("div");
  var text = document.createTextNode("第二点五个div");
  d25.appendChild(text);
   
  var parentDiv = document.getElementById("parentDiv");
  var d3 = document.getElementById("d3");
   
  parentDiv.insertBefore(d25,d3);
}
  
</script>
   
<button onclick="insertDiv()">在第二和第三之间，插入第二点五个div</button>
```


