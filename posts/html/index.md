# HTML 笔记

# 概念

## html标签

HTML是Hyper Text Markup Language 超文本标记语言 的缩写

HTML是由一套标记标签 （markup tag）组成，通常就叫标签

标签由开始标签和结束标签组成
<p> 这是一个开始标签
</p> 这是一个结束标签
<p> **Hello World** </p> 标签之间的文本叫做内容

```html
<h1>大标题</h1>
<h2>小一点的标题</h2>
<h3>再小一点的标题</h3>
<h4>更小一点的标题</h4>
```



## html元素

元素指的是从开始标签到结束标签之间所有的代码
比如

<p> hello world</p>

一个完整的HTML文件，应该至少包含html元素，body元素，以及里面的内容

```html
<html>

 <body>

   <h1>标题</h1>  
 
 </body>

</html>

```



## html属性

属性用来修饰标签的
比如要设置一个标题居中

<h1 align="center">居中标题</h1>

写在开始标签里的 **align="center"** 就叫属性
align 是**属性名**
center 是**属性值**
属性值应该使用双引号括起来

## html注释

html使用<!-- --> 进行注释

# 基本元素

## html标题

标题会自动粗体，大写其中的内容，并且带有换行效果

一般会使用<h1> 到 <h6> 分别表示不同大小的标题

<h1>标题1</h1>
<h2>标题2</h2>
<h3>标题3</h3>
<h4>标题4</h4>
<h5>标题5</h5>
<h6>标题5</h6>

## html段落

p标签即表示段落 是paragraph的缩写 自带换行效果

## 粗体

<b>
<strong>
都可以用来实现粗体的效果

区别：
b是bold的缩写，仅仅表示该文本是粗体的，**并不暗示这段文字的重要性**
strong虽然也是粗体，但是更多的是强调语义上的加重，提醒用户该文本的重要性。 在SEO（搜索引擎优化）的时候，也更加容易帮助用户找到重点的内容
推荐使用strong

```html
<p>无粗体效果</p>
<b>b标签粗体效果</b>
<br/>
<strong>strong标签粗体效果</strong>
```

## 斜体

<i>和<em>都可以表示斜体效果

区别：
i是italic的缩写，仅仅表示该文本是斜体的，并不暗示这段文字的重要性

em 是 Emphasized的缩写，虽然也是斜体，但是更多的是强调语义上的加重，提醒用户该文本的重要性。 常常用于引入新的术语的时候使用。

```html
//嵌套
<p>无效果</p>
<strong>粗体</strong>
<br/>
<i>斜体</i>
<br/>
<strong><i>同时有粗体和斜体</i></strong>
```

## 预格式

有时候，需要在网页上显示代码，比如java代码

就需要用到pre

```java
<p>这里是没有用预格式的情况：</p>

public class HelloWorld {

	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}

<br/>
<br/>

<p>使用预格式的情况:</p>

<pre>
public class HelloWorld {

	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}

</pre>

```

## 删除效果

<del>即删除标签
delete的缩写

<p>无删除效果</p>
<del>使用del标签实现的删除效果</del>
<br/>
<s>使用s标签实现的删除效果，但是不建议使用，因为很多浏览器不支持s标签</s>

## 下划线

<ins>即下划线标签

<ins>使用ins标签实现的下划线效果</ins>

<br/>

<u>使用u标签实现的下划线效果，但是不建议使用</u>

## 图像

<img> 即图像标签 需要设置其属性 src指定图像的路径

```html
<img src="https://how2j.cn/example.gif"/>
```



1. 显示图像

<img src="https://how2j.cn/example.gif"/>

2. 同级目录图像

如果是本地文件，只需把图片放在同一个目录下即可
src直接使用文件名，不需要/

3. 上级目录图像

```java
图片在上级目录，则在src上加上 ../，即可访问上级目录的图片
如果是在上级目录的上级目录，则使用 ../../
```

4. 设置图像大小

<img width="200" height="200" src="https://how2j.cn/example.gif"/>

```html
<img width="200" height="200" src="https://how2j.cn/example.gif"/>
```

5. 图像居中

img不能够自己居中，需要放在其他能够居中的标签中实现这个效果，比如h1标签,p标签.
经常采用的手段是放在div中居中

```java
<div align="left">
  <img src="https://how2j.cn/example.gif"/>
</div>

<div align="center">
  <img src="https://how2j.cn/example.gif"/>
</div>

<div align="right">
  <img src="https://how2j.cn/example.gif"/>
</div>
```

<div align="left">
  <img src="https://how2j.cn/example.gif"/>
</div>

<div align="center">
  <img src="https://how2j.cn/example.gif"/>
</div>

<div align="right">
  <img src="https://how2j.cn/example.gif"/>
</div>

## 替换图片上的字

如果图片不存在，默认会显示一个缺失图片，这是不友好的
所以可以加上alt属性。
当图片存在的时候，alt是不会显示的
当图片不存在的时候，alt就会出现

```java
  <img src="https://how2j.cn/example_not_exist.gif" />

  <br/>

  <img src="https://how2j.cn/example.gif" alt="这个是一个图片" />

  <br/>
  <img src="https://how2j.cn/example_not_exist.gif" alt="这个是一个图片" />
```

  <img src="https://how2j.cn/example_not_exist.gif" />

  <br/>

  <img src="https://how2j.cn/example.gif" alt="这个是一个图片" />

  <br/>
  <img src="https://how2j.cn/example_not_exist.gif" alt="这个是一个图片" />

## 超链

```java
<a>标签即用来显示超链

完整元素是

<a href="跳转到的页面地址">超链显示文本</a>
```



<a>标签即用来显示超链  完整元素是  <a href="跳转到的页面地址">超链显示文本</a>

1. <a href="http://www.12306.com">12306</a>

2. 在新的页面打开超链

新增属性target

```html
<a href="http://www.12306.cn" target="_blank">http://www.12306.cn</a>

```

3. 超链上提示文字

当鼠标放在超链上的时候，就会弹出提示文字

```html
<a href="http://www.12306.com" title="跳转到http://www.12306.com">www.12306.com</a>

```

4. 使用图片作为超链

```html
<a href="http://www.12306.com">
<img src="https://how2j.cn/example.gif"/>
</a>
```

## 表格

```html
<table>标签用于显示一个表格
<tr> 表示行
<td> 表示列又叫单元格
```

1. 3行2列表格

```html
tr(table row)表示行，所有3个tr元素
td(table data)表示列，每一行，有2列，所以每一个tr元素里，有2个td元素
```

```html
<table>
  <tr>
      <td>1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

```

2. 带边框的表格

   设置table的属性border

```java
<table border="1">
  <tr>
      <td>1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

```

3. 设置table宽度

```html
设置table的属性 width
px即像素的意思。
比如你的分辨率是1024X768,则你的屏幕横向就有1024个像素
```

```html
<table border="1" width="200px">
  <tr>
      <td>1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

```

4. 单元格宽度绝对值

设置td的属性width
在示例里，1单元格设置了宽度，那么3，和a单元格，自动继承该宽度
2单元格的宽度由table宽度和1单元格的宽度决定

```html
<table border="1" width="200px">
  <tr>
      <td width="50px">1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

```

5. 单元格宽度相对值

设置td的属性width为百分数

```html
<table border="1" width="200px">
  <tr>
      <td width="80%">1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

```

6. 单元格水平对齐

```html
<table border="1" width="200px">
  <tr>
      <td width="50%" align="left">1</td>
      <td>2</td>
  </tr>

  <tr>
      <td align="center">3</td>
      <td>4</td>
  </tr>

  <tr>
      <td align="right">a</td>
      <td>b</td>
  </tr>

</table>

```

7. 单元格垂直对齐

设置td的属性valign

```html
<table border="1" width="200px">
  <tr>
      <td width="50%" valign="top" >1</td>
      <td>
             2   <br/>
             2   <br/>
             2   <br/>
      </td>
  </tr>
 
  <tr>
      <td valign="middle"  >3</td>
      <td>
             4   <br/>
             4   <br/>
             4   <br/>
      </td>
  </tr>
 
  <tr>
      <td valign="bottom" >a</td>
      <td>
             b   <br/>
             b   <br/>
             b   <br/>
      </td>
  </tr>
 
</table>

```

8. 横跨两列, 水平合并

设置td的属性colspan



```html
<table border="1" width="200px">
  <tr>
      <td colspan="2" >1，2</td>
  </tr>
 
  <tr>
      <td>3</td>
      <td>4</td>
  </tr>
 
  <tr>
      <td>a</td>
      <td>b</td>
  </tr>
 
</table>
```

9. 横跨两行，垂直合并

设置td的属性rowspan

 ```html
<table border="1" width="200px">
  <tr>
      <td rowspan="2">1,3</td>
      <td>2</td>
  </tr>

  <tr>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td>b</td>
  </tr>

</table>

 ```

10. 背景色

设置tr或者td的属性bgcolor

```html
<table border="1" width="200px">
  <tr bgcolor="gray">
      <td width="50%">1</td>
      <td>2</td>
  </tr>

  <tr>
      <td>3</td>
      <td>4</td>
  </tr>

  <tr>
      <td>a</td>
      <td  bgcolor="pink">b</td>
  </tr>

</table>
```

## 列表

列表分无序列表和有序列表
分别用<ul>标签和<ol>标签表示

1. 无序列表

```html
<ul>
<li>DOTA</li>
<li>LOL</li>
</ul>

```

2. 有序列表

```html
<ol>
<li>地卜师</li>
<li>卡尔</li>
</ol>

```

## 块 div span

1. 看不出任何效果

```html
<div>

<span>

这两种标签都是布局用的

这种标签本身没有任何显示效果

通常是用来结合css进行页面布局
  
  
  
这没有标签
<div> 这是一个div </div>
<span>这是一个span</span>
```

2. div布局

一个简单的div布局的例子
注： 这里使用了[style外边距样式](https://how2j.cn/k/css2/css2-margin/248.html)，margin-left:50px 指的是左边距50个像素
需要对两个图片进行左边距控制
如果不使用div,则需要对每一个图像设置边距
使用了div后，先把两个图像都放在一个div里
只需要设置div的边距，就可以达到两个图片都移动的效果

```html
 <img style="margin-left:50px" src="https://how2j.cn/example.gif"/>
  <br/>
 <img style="margin-left:50px" src="https://how2j.cn/example.gif"/>

<div style="margin-left:100px" >
 <img src="https://how2j.cn/example.gif"/>
  <br/>
 <img src="https://how2j.cn/example.gif"/>
</div>

```

 <img style="margin-left:50px" src="https://how2j.cn/example.gif"/>
  <br/>
 <img style="margin-left:50px" src="https://how2j.cn/example.gif"/>

<div style="margin-left:100px" >
 <img src="https://how2j.cn/example.gif"/>
  <br/>
 <img src="https://how2j.cn/example.gif"/>
</div>

3. div和span的区别

div是块元素，即自动换行
常见的块元素还有h1,table,p
span是内联元素，即不会换行
常见的内联元素还有img,a,b,strong

```html
<div>
 第一个div
</div>

<div>
 第二个div
</div>

<span>
 第一个span
</span>

<span>
 第二个span
</span>
```

## 字体

1. 字体元素

<font color="green">绿色默认大小字体</font>
<br>
<font color="blue" size="+2">蓝色大2号字体</font>
<br>
<font color="red" size="-2">红色小2号字体</font>

```html
<font color="green">绿色默认大小字体</font>
<br>
<font color="blue" size="+2">蓝色大2号字体</font>
<br>
<font color="red" size="-2">红色小2号字体</font>

```

2. 颜色表示方法 

在html中，颜色通常使用两种方式来表示：

1. 颜色名，比如red, blue
2. 颜色对应的16进制，比如#ff0000 就表示红色

<font color="red" >用red表示红色字体</font>
<br>
<font color="#ff0000" >用#ff0000表示红色字体</font>

## 内联框架

```html
<iframe> 即内联框架

通过内联框架 可以实现在网页中“插入”网页
  
<iframe src="https://how2j.cn/" width="600px" height="400px">
</iframe>

```

<iframe src="https://linon419.github.io/" width="600px" height="400px">
</iframe>

# 表单元素

## 文本框

<input type="text"> 即表示文本框

并且只能够输入一行

如果要输入多行

使用[文本域](https://how2j.cn/k/html/html-textarea/196.html)

注： <input> 标签很特别，一般是不需要写成<input />或者<input></input> 这样的。
并且<input> 这样的写法也是满足标准的

1. 文本框

```
<input type="text"> 
```

2. 设置文本框长度

```html
<input type="text" size="10">
```

3. 设置默认文本值

```html
<input type="text" size="10" value = "Hello"> 

```

<input type="text" size="10" value = "Hello"> 

4. 有背景文字的文字框

使用属性placeholder
placeholder是一个html5的属性，对于大多数的已经支持html5的浏览器来说，是可以看到效果的，但是对于老的不支持html5的浏览器，比如ie8，就看不到效果

```html
<input type="text" placeholder="请输入账号">

```

<input type="text" placeholder="请输入账号">

## 密码框

<input type="password"> 即表示密码框

1. 密码框输入为星号

```html
<input type="password">
```

## 表单

1. 表单

```html
action="/study/login.jsp" 表示把账号和密码提交到login.jsp这个页面去

注: 这里把数据提交到服务端的login.jsp去了，鉴于当前学习的进度，就不对JSP的内容展开了。 JSP的内容可以到JSP章节进行学习
注: 有好奇的同学可以参考图片中的login.jsp

<form>用于向服务器提交数据，比如账号密码

<form action="https://how2j.cn/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>

```

<form action="https://how2j.cn/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>

2. method="get"

使用method="get" 提交数据 是常用的提交数据的方式
如果form元素没有提供method属性，**默认就是get**方式提交数据
get方式的一个特点就是，可以在浏览器的**地址栏看到提交的参数**，即便是密码也看得到

```html
<form method="get" action="https://how2j.cn/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>
```

3. method="post"

使用method="post" 也可以提交数据
**post****不会**在地址栏显示提交的参数
如果要提交二进制数据，比如上传文件，必须采用post方式

```html
<form method="post" action="https://how2j.cn/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>
```

4. get和post的区别

get和post的区别
get
是form默认的提交方式
如果通过一个超链访问某个地址，是get方式
如果在地址栏直接输入某个地址，是get方式
提交数据会在浏览器显示出来
**不可以**用于提交二进制数据，比如上传文件
post
必须在form上通过 method="post" 显示指定
提交数据**不会**在浏览器显示出来
可以用于提交二进制数据，比如上传文件

## 单选框

<input type="radio" > 表示单选框

1. 单选框

两个单选，都可以同时选中。 为了达到，同一时间，只能选中其一的效果，需要使用[分组](https://how2j.cn/k/html/html-checkbox/193.html#step364)

```html
单选1 <input type="radio" >
单选2 <input type="radio" >

```

单选1 <input type="radio" >
单选2 <input type="radio" >

2. 默认选中

默认选中 <input type="radio" checked="checked" >

3. 分组

分组即，多个单选框，都在一个分组里，同一时间，只能选中一个单选框
设置name属性相同即可

```html
<p>今天晚上做什么？</p>

学习java<input type="radio" name="activity" value="学习java" > <br/>
东京热<input type="radio" checked="checked"  name="activity" value="tokyohot" > <br/>
dota<input type="radio" name="activity" value="dota" > <br/>
LOL<input type="radio" name="activity"  value="lol"> <br/>


<input type="radio" name="xxx" checked="checked" />
当name一致时，被默认分为一组，只能选其一，
checked 是默认选择

```

## 复选框

<input type="checkbox"> 即表示复选框

```html
<p>今天晚上做什么？</p>
 
学习java<input type="checkbox" value="学习java" > <br/>
东京热<input type="checkbox" checked="checked"  name="activity" value="tokyohot" > <br/>
dota<input type="checkbox" value="dota" > <br/>
LOL<input type="checkbox" value="lol"> <br/>
```

<p>今天晚上做什么？</p>

学习java<input type="checkbox" value="学习java" > <br/>
东京热<input type="checkbox" checked="checked"  name="activity" value="tokyohot" > <br/>
dota<input type="checkbox" value="dota" > <br/>
LOL<input type="checkbox" value="lol"> <br/>

## 下拉列表

```html
<select> 即下拉列表
需要配合<option>使用
```

1. 下拉列表

<select >
 <option >苍老师</option>
 <option >高树玛利亚</option>
 <option >遥美</option>
</select>

```]
<select >
 <option >苍老师</option>
 <option >高树玛利亚</option>
 <option >遥美</option>
</select>

```

2. 设置高度

使用属性size

```html
<select  size="2">
 <option >苍老师</option>
 <option >高树玛利亚</option>
 <option >遥美</option>
</select>

```

<select  size="2">
 <option >苍老师</option>
 <option >高树玛利亚</option>
 <option >遥美</option>
</select>

3. 设置可以多选

使用ctrl或者shift进行多选

```html
<select size="3" multiple="multiple">
 <option >苍老师</option>
 <option >高树玛利亚</option>
 <option >遥美</option>
</select>

```

4. 默认选中

对option元素设置selected="selected" 属性

```html
<select size="3" multiple="multiple">
 <option >苍老师</option>
 <option selected="selected">高树玛利亚</option>
 <option selected="selected">遥美</option>
</select>
```

<select size="3" multiple="multiple">
 <option >苍老师</option>
 <option selected="selected">高树玛利亚</option>
 <option selected="selected">遥美</option>
</select>

5. 文本域

```html
<textarea> 即文本域
与文本框不同的是，文本域可以有多行，并且可以有滚动条
```

1. 文本yu

```html

<textarea>abc
def
</textarea>

```

<textarea>abc
def
</textarea>

2. 设置高度和行数

<textarea cols="30" rows="8">123456789012345678901234567890
1234567890
1234567890
1234567890
1234567890
1234567890
1234567890
1234567890</textarea>

```html
<textarea cols="30" rows="8">123456789012345678901234567890
1234567890
1234567890
1234567890
1234567890
1234567890
1234567890
1234567890</textarea>

```

## 普通按钮

<input type="button"> 即普通按钮

1. <input type="button" value="一个按钮">
2. 普通按钮不具备提交form的效果

## 提交按钮

<input type="submit"> 即为提交按钮
用于提交form，把数据提交到服务端

<form action="/study/login.jsp" method="get">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>


```html
<form action="/study/login.jsp" method="get">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="登陆">
</form>

```

## 重置按钮

<input type="reset"> 重置按钮 可以把输入框的改动复原

```html
<form action="/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="提交">
<input type="reset" value="重置">
</form>

```

<form action="/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="submit" value="提交">
<input type="reset" value="重置">
</form>

## 图像提交

<input type="image" > 即使用图像作为按钮进行form的提交

<form action="/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="image" src="https://how2j.cn/example.gif">
</form>

```html
<form action="/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>
<input type="image" src="https://how2j.cn/example.gif">
</form>

```

## 按钮

1. Button

<button></button>即按钮标签
与<input type="button">不同的是，<button>标签功能更为丰富

按钮标签里的内容可以是文字也可以是图像

如果button的type=“submit” ，那么它就具备提交form的功能

```html
<button>按钮</button>
```

<button>按钮</button>

2. 里面是图

<button><img src="https://how2j.cn/example.gif"/></button>

```html
<button><img src="https://how2j.cn/example.gif"/></button>

```

3. 提交数据

设置type="submit"
IE下button的type的默认值为button不具备提交功能
其他浏览器type的默认值是submit

```html
<form action="/study/login.jsp">
账号：<input type="text" name="name"> <br/>
密码：<input type="password" name="password" > <br/>

<button type="submit">登陆</button>

</form>

```


