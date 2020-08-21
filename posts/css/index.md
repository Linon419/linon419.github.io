# 

# 基础

## css语法

css的语法
selector {property: value}
即 选择器{属性:值}

学习css即学习有哪些选择器，哪些属性以及可以使用什么样的值

1. 选择所有p元素

```html
<style>
p{
   color:red;
}
</style>
<p>这是一个P</p>
<p>这是一个P</p>
<p>这是一个P</p>
<p>这是一个P</p>

```

2. 也可以直接在元素上增加style属性

```html
<p style="color:red">这是style为红色的</p>
<p>这是一个没有style的p</p>
```

## css选择器

选择器主要分3种
元素选择器
id选择器
类选择器

1. 元素选择器

```html
<style>
p{
   color:red;
}
</style>
<p>这是一个P</p>
<p>这是一个P</p>
<p>这是一个P</p>
<p>这是一个P</p>
```

2. id选择器

```html
<style>
p{
  color:red;
}
#p1{
  color:blue;
}
#p2{
  color:green;
}
</style>

<p>没有id的p</p>
<p id="p1">id=p1的p</p>
<p id="p2">id=p2的p</p>

```

3. 类选择器

```html
<style>
.pre{
  color:blue;
}
.after{
  color:green;
}
</style>
 
<p class="pre">前3个</p>
<p class="pre">前3个</p>
<p class="pre">前3个</p>
 
<p class="after">后3个</p>
<p class="after">后3个</p>
<p class="after">后3个</p>
```

## css注释

```
注释
以/* 开始
以*/结束
被注释掉的文字会自动隐藏
```

## css尺寸

1. 尺寸大小

属性：width
值：可以是百分比或者像素
为了便于观察一个元素的大小设置效果，进行了[背景色的设置](https://how2j.cn/k/css2/css2-backgroud/242.html#step461)

```html
<style>
p#percentage{
  width:50%;
  height:50%;
  background-color:pink;
}
p#pix{
  width:180px;
  height:50px;
  background-color:green;
}
</style>
 
<p id="percentage"> 按比例设置尺寸50%宽 50%高</p>
 
<p id="pix"> 按象素设置尺寸  180px宽 50 px高</p>
```

## css背景

| background-color                 | 背景颜色   | [示例代码](https://how2j.cn/k/css2/css2-backgroud/242.html#step461) |
| -------------------------------- | ---------- | ------------------------------------------------------------ |
| background-image:url(imagepath); | 图片做背景 | [示例代码](https://how2j.cn/k/css2/css2-backgroud/242.html#step462) |
| url(background.jpg)              | 本地测试   | [示例代码](https://how2j.cn/k/css2/css2-backgroud/242.html#step1236) |
| background-repeat                | 背景重复   | [示例代码](https://how2j.cn/k/css2/css2-backgroud/242.html#step464) |
| background-size: contain         | 背景平铺   |                                                              |

1. 背景颜色

属性名background-color
颜色的值可以采用3种方式
\1. 预定义的颜色名字
比如red,gray,white,black,pink，参考[颜色速查手册](https://how2j.cn/k/html/html-font/644.html#step2089)
\2. rgb格式
分别代表红绿蓝的比例 rgb(250,0,255) 即表示红色是满的，没有绿色，蓝色是满的，即红色和蓝色混合在一起：紫色
\3. 16进制的表示
\#00ff00 等同于 rgb(0,255,0)

```html
<style>
p.gray {background-color: gray;}
h1 {background-color: transparent}
h2 {background-color: rgb(250,0,255)}
h3 {background-color: #00ff00}

</style>

<p class="gray">灰色</p>
<h1>透明背景，默认即透明背景</h1>
<h2>紫色</h2>
<h3>绿色背景</h3>


```



2. 图片做背景

```html
<style>
div#test
  {
    background-image:url(/study/background.jpg);
    width:200px;
    height:100px;
  }
</style>

<div id="test">
  这是一个有背景图的DIV
</div>

```

3. 背景重复

background-repeat属性
值可以选
repeat; 水平垂直方向都重复
repeat-x; 只有水平方向重复
repeat-y; 只有垂直方向重复
no-repeat; 无重复

```css
<style>
div#norepeat
  {
    background-image:url(/study/background_small.jpg);
    width:200px;
    height:100px;
    background-repeat: no-repeat;
  }
 
div#repeat-x
  {
    background-image:url(/study/background_small.jpg);
    width:200px;
    height:100px;
    background-repeat: repeat-x;
  }
</style>
 
<div id="norepeat">
  背景不重复
</div>
 
<div id="repeat-x">
  背景水平重复
</div>
```

4. 背景平铺

属性：background-size
值：contain

```html
<style>
div#contain
  {
    background-image:url(/study/background_small.jpg);
    width:200px;
    height:100px;
    background-size: contain;
  }
</style>
  
<div id="contain">
   背景平铺，通过拉伸实现，会有失真
</div>
```

## css文本

| 关键字          | 简介     | 示例代码                                                     |
| :-------------- | :------- | :----------------------------------------------------------- |
| color           | 文字颜色 | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step452) |
| text-align      | 对齐     | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step453) |
| text-decoration | 文本修饰 | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step454) |
| line-height     | 行间距   | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step455) |
| letter-spacing  | 字符间距 | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step456) |
| word-spacing    | 单词间距 | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step457) |
| text-indent     | 首行缩进 | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step458) |
| text-transform  | 大小写   | [示例代码](https://how2j.cn/k/css2/css2-text/241.html#step459) |
| white-space     | 空白格   |                                                              |

### 文本颜色

```html
<style>
div#colorful{
  color:pink
}
 
</style>
 
<div id="colorful">
  粉红色
</div>
```

### 对齐

属性:text-align
值：left,right,center
div是块级元素，其默认宽度是100%，所以文本有对齐的空间前提。

但是，span却看不出右对齐效果，为什么呢？
因为span是内联元素其默认宽度就是其文本内容的宽度
简单说就是文本已经**粑**在其边框上了，对齐是看不出效果来的

使用了后面的样式风格，让div和span的边框显露出来，便于理解本知识点
用到了[边框](https://how2j.cn/k/css2/css2-border/246.html)和[外边距](https://how2j.cn/k/css2/css2-margin/248.html)

```html
<style>
div#left{
  text-align:left;
}
/*让div和span的边框显露出来，便于理解本知识点*/
div,span{
  border: 1px gray solid;
  margin:10px;
}
 
div#right{
  text-align:right;
}
 
div#center{
  text-align:center;
}
 
span#right{
  text-align:right;
}
 
</style>
 
<div id="left">
左对齐
</div>
 
<div id="right">
右对齐
</div>
 
<div id="center">
居中
</div>
 
<span id="right">
span看不出右对齐效果
 
</span>
```

### 文本修饰

属性：text-decoration
值： overline

```html
<style type="text/css">
h1 {text-decoration: overline}
h2 {text-decoration: line-through}
h3 {text-decoration: underline}
h4 {text-decoration:blink}
.a {text-decoration: none}
</style>
 
<h1>上划线</h1>
<h2>删除效果</h2>
<h3>下划线</h3>
<h4>闪烁效果，大部分浏览器已经取消该效果</h4>
<a href="https://how2j.cn/">默认的超链</a>
<a class="a" href="https://how2j.cn/">去掉了下划线的超链</a>
```

### 行间距

```html
<style>
p{
  width:200px;
}
 
.p{
  line-height:200%;
}
</style>
 
<p>
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
默认行间距
</p>
 
<p class="p">
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
200%行间距
</p>
```

### 字符间距

属性：letter-spacing
值： 数字

```html
<style>
p{
  width:200px;
}
 
.p{
  letter-spacing:2;
}
</style>
 
<p>
abcdefg abcdefg abcdefg abcdefg abcdefg abcdefg
</p>
 
<p class="p">
abcdefg abcdefg abcdefg abcdefg abcdefg abcdefg
</p>
```

### 单词间距

属性：word-spacing
值： 数字

```html
<style>
p{
  width:200px;
}
 
.p{
  word-spacing:10;
}
</style>
 
<p>
abcdefg abcdefg abcdefg abcdefg abcdefg abcdefg
</p>
 
<p class="p">
abcdefg abcdefg abcdefg abcdefg abcdefg abcdefg
</p>
```

### 首行缩进

属性：text-indent
值： 数字

```html
<style>
p{
  width:200px;
}
 
.p{
  text-indent:50;
}
</style>
 
<p>
没有缩进效果的一段文字没有缩进效果的一段文字没有缩进效果的一段文字没有缩进效果的一段文字
</p>
 
<p class="p">
有缩进效果的一段文字有缩进效果的一段文字有缩进效果的一段文字有缩进效果的一段文字有缩进效果的一段
 
文字
</p>
```

### 大小写

属性：text-transform
值：
uppercase 全部大写
capitalize 首字母大写
lowercase 全部小写

```html
<style>
p.u {text-transform:uppercase}
p.c {text-transform:capitalize}
p.l {text-transform:lowercase}
 
</style>
 
<p class="u">
abcD
</p>
 
<p class="c">
abcD
</p>
 
<p class="l">
abcD
</p>
```

### 空白格

属性：white-space
值：
normal 默认。多个空白格或者换行符会被合并成一个空白格
pre 有多少空白格，显示多少空白格，相当于[pre标签](https://how2j.cn/k/html/html-pre/182.html),如果长度超出父容器也**不会换行**。
pre-wrap 有多少空白格，显示多少空白格，相当于[pre标签](https://how2j.cn/k/html/html-pre/182.html),如果长度超出父容器，**会换行**。
nowrap 一直不换行，直到使用br

```html
<style>
p.n {white-space:normal}
p.p {white-space:pre}
p.pw {white-space:pre-wrap}
p.nw {white-space:nowrap}
 
</style>
 
<p class="n">
在默认情况下，多个     空白格或者
换行符
 
    会被     合并成一个空白格
</p>
 
<p class="p">
保留所有的    空白格
以及换行符
相当于pre元素
特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字
</p>
 
<p class="pw">
保留所有的    空白格
以及换行符
相当于pre元素
特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字特别长的一段文字
</p>
 
<p class="nw">
不会换行
不会换行
不会换行
不会换行
不会换行
不会换行
直到br<br/>才换行
</p>
```

## 字体

| font-size   | 尺寸       | [示例代码](https://how2j.cn/k/css2/css2-font/244.html#step467) |
| ----------- | ---------- | ------------------------------------------------------------ |
| font-style  | 风格       | [示例代码](https://how2j.cn/k/css2/css2-font/244.html#step468) |
| font-weight | 粗细       | [示例代码](https://how2j.cn/k/css2/css2-font/244.html#step469) |
| font-family | 字库       | [示例代码](https://how2j.cn/k/css2/css2-font/244.html#step470) |
| font        | 声明在一起 |                                                              |

### 尺寸

属性：font-size
值：数字或者百分比

```html
<style>
p.big{
  font-size:30px;
}
 
p.small{
  font-size:50%;
}
   
p.small2{
  font-size:0.5em;
} 
</style>
 
<p >正常大小</p>
<p class="big">30px大小的文字</p>
<p class="small">50%比例的文字</p>
<p class="small2">0.5em 等同于 50%比例的文字</p>
```

### 风格

font-style:
normal 标准字体
italic 斜体

```html
<style>
p.n{
  font-style:normal;
}
 
p.i{
  font-style:italic;
}
</style>
 
<p >标准字体</p>
<p class="n">标准字体</p>
<p class="i">斜体</p>
```

### 粗细

属性 font-weight
normal 标准粗细
bold 粗一点

```html
<style>
p.n{
  font-weight:normal;
}
p.b{
  font-weight:bold;
}
</style>
 
<p >标准字体</p>
<p class="n">标准字体</p>
<p class="b">粗一点</p>
```

### 字库

属性font-family

```html
<style>
p.f1{
  font-family:"Times New Roman";
}
 
p.f2{
  font-family:Arial;
}
p.f3{
  font-family:宋体;
}
p.f4{
  font-family:黑体;
}
p.f5{
  font-family:楷体;
}
p.f6{
  font-family:微软雅黑;
}
</style>
 
<p >默认字库 font family:default </p>
<p class="f1">设置字库 font-family: Times New Roman</p>
<p class="f2">设置字库 font-family: Arial</p>
<p class="f3">设置字库 font-family: 宋体, 这种字体是IE默认字体</p>
<p class="f4">设置字库 font-family: 黑体</p>
<p class="f5">设置字库 font-family: 楷体</p>
<p class="f6">设置字库 font-family: 微软雅黑, 这个字体是火狐默认字体</p>
```

### 声明在一起

<style>
p.all{
   font:italic bold 30px "Times New Roman";
}


</style>

<p>默认字体</p>

<p class="all">斜体的 粗体的 大小是30px的 "Times New Roman" </p>

## 鼠标样式

```html
<style>
  span{
    cursor:crosshair;
  }
</style>
  
<span>鼠标移动到这段文字上，就看到鼠标样式变成了十字架</span>
```

## 表格

| table-layout:automatic\|fixed      | 表格布局 | [示例代码](https://how2j.cn/k/css2/css2-table/245.html#step472) |
| ---------------------------------- | -------- | ------------------------------------------------------------ |
| border-collapse:separate\|collapse | 表格边框 |                                                              |

### 表格布局

属性:table-layout
automatic; 单元格的大小由td的内容宽度决定
fixed; 单元格的大小由td上设置的宽度决定
**注**：只对连续的英文字母起作用，如果使用中文就看不到效果

```html
<style>
table.t1{
  table-layout:automatic;
}
 
table.t2{
  table-layout:fixed;
}
 
</style>
 
<table class="t1" border="1" width="100%">
   <tr>
      <td width="10%">abcdefghijklmnopqrstuvwxyz</td>
      <td width="90%">abc</td>
   </tr>
</table>
 
<table class="t2" border="1" width="100%">
   <tr>
      <td width="50px">abcdefghijklmnopqrstuvwxyz</td>
      <td >abc</td>
   </tr>
</table>
```

### 表格边框

属性：border-collapse
值：
separate:边框分隔
collapse:边框合并

```html
<style>
table.t1{
  border-collapse:separate;
}
 
table.t2{
   border-collapse:collapse;
}
 
</style>
 
<table class="t1" border="1" width="200px">
   <tr>
      <td width="50%">边框分离</td>
      <td width="50%">边框分离</td>
   </tr>
</table>
 
<br/>
<br/>
 
<table class="t2" border="1" width="200px">
   <tr>
      <td width="50%">边框合并</td>
      <td width="50%">边框合并</td>
   </tr>
</table>
```

## 边框

| 关键字                  | 简介                         | 示例代码                                                     |
| :---------------------- | :--------------------------- | :----------------------------------------------------------- |
| border-style            | 边框风格                     | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step474) |
| border-color            | 边框颜色                     | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step475) |
| border-width            | 边框宽度                     | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step476) |
| border                  | 都放在一起                   | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step477) |
| border-top              | 只有一个方向有边框           | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step3084) |
| border-top，border-left | 有交界的边都有边框           | [示例代码](https://how2j.cn/k/css2/css2-border/246.html#step3085) |
| div span                | 块级元素和内联元素的边框区别 |                                                              |

### 边框风格

属性： border-style
solid: 实线
dotted:点状
dashed:虚线
double:双线

```java
<style>
.solid{
   border-style:solid;
}
.dotted{
   border-style:dotted;
}
.dashed{
   border-style:dashed;
}
.double{
   border-style:double;
}
 
</style>
 
<div> 默认无边框div </div>
 
<div class="solid"> 实线边框  </div><br/>
 
<div class="dotted"> 点状边框  </div> <br/>
<div class="dashed"> 虚线边框  </div> <br/>
<div class="double"> 双线边框  </div> <br/>
```

### 边框颜色

属性：border-color
值：red,#ff0000,rgb(255,0,0)

```html
<style>
.red{
   border-style:solid;
   border-color:red;
}
 
</style>
 
<div> 默认无边框div </div>
 
<div class="red"> 实线红色边框  </div><br/>
```



### 边框宽度

属性：border-width
值：数字

```css
<style>
.red{
   border-style:solid;
   border-color:red;
   border-width:1px;
}
 
.default{
   border-style:solid;
   border-color:red;
}
 
</style>
 
<div> 默认无边框div </div>
 
<div class="red"> 实线红色细边框  </div><br/>
 
<div class="default"> 实线红色默认宽度边框  </div><br/>
```

### 都放在一起

属性：border
值：颜色 风格 宽度

```css
<style>
.red{
   border:1px dotted LightSkyBlue;
}
 
</style>
 
<div> 默认无边框div </div>
 
<div class="red"> 点状天蓝色细边框  </div><br/>
```

### 只有一个方向有边框

通过制定位置，可以只给一个方向设置边框风格，颜色和宽度

   border-top-style:solid;

   border-top-color:red;

   border-top-width: 50px;

 top,bottom,left,right分别对应上下左右

```css
<style>
 div{
   width:150px;
   height:150px;
   border-top-style:solid;
   border-top-color:red;
   border-top-width: 50px;
   background-color:lightgray;  
  }
</style>
 
<div>
只有上面有边框
</div>
```

### 有交界的边都有边框

比如上和左就是有交界的，而上和下就没有交界

当有交界的边同时出现边框的时候，就会以倾斜的形式表现交界线。

```css
<style>
 div.lefttop{
   width:150px;
   height:150px;
   border-top-style:solid;
   border-top-color:red;
   border-top-width: 50px;
   border-left-style:solid;
   border-left-color:blue;
   border-left-width: 50px;  
   background-color:lightgray;  
  }
   
  div.alldirection{
   width:150px;
   height:150px;
   border-top-style:solid;
   border-top-color:red;
   border-top-width: 50px;
   border-left-style:solid;
   border-left-color:blue;
   border-left-width: 50px;  
   border-bottom-style:solid;
   border-bottom-color:green;
   border-bottom-width: 50px;
   border-right-style:solid;
   border-right-color:yellow;
   border-right-width: 50px;     
   background-color:lightgray;  
  }
</style>
  
<div class="lefttop">
左边和上边都有边框
</div>
<br>
<div class="alldirection">
四边都有边框　
</div>
```

## 内边距

### 元素内边距

指的是元素里的内容与边框之间的距离
属性：
padding-left: 左内边距
padding-right: 右内边距
padding-top: 上内边距
padding-bottom: 下内边距
padding: 上 右 下 左

### 左内边距

属性:padding-left
值：数字
指的是，元素中的内容，与边框之间的距离

```css
<style>
.red{
   border:5px solid red;
   background-color:green;
}
 
.pad-left{
   border:5px solid red;
   background-color:green;
   padding-left:50px;
}
 
</style>
 
<span class="red"> 无内边距的span  </span><br/> <br/>
 
<span class="pad-left"> 左边距为50的span  </span><br/>
```

### 内边距，写1个和写4个的区别

属性：padding
值：如果只写一个，即四个方向的值
值：如果写四个，即四个方向的值
**上 右 下 左**,依**顺时针**的方向依次赋值

```css
<style>
.pad-left-one{
   border:5px solid red;
   background-color:green;
   padding: 20;
}
  
.pad-left-four{
   border:5px solid red;
   background-color:green;
   padding: 10 20 30 40;
}
  
</style>
<br/>
<span class="pad-left-one"> padding:20的span  </span> <br/> <br/> <br/> <br/>
  
<span class="pad-left-four">
padding: 10 20 30 40 的span </span> <br/> <br/> <br/> <br/>
```

### 当内边距的值少于4个的时候

如果**缺少左**内边距的值，则**使用右**内边距的值。
如果**缺少下**内边距的值，则**使用上**内边距的值。
如果**缺少右**内边距的值，则**使用上**内边距的值。
举例说明
这是完整4个的
padding: 10 20 40 80
如果只有3个
padding: 10 20 40
那么left取right
padding: 10 20 40 = padding: 10 20 40 **20**
如果只有两个
padding: 10 20
那么bottom取top，left取right
padding: 10 20 = padding:10 20 **10 20**
如果只有一个
padding:10
那么right取top，bottom取top，left取top
padding:10 = padding:10 **10 10 10**

## 外边距

元素外边距
指的是元素边框和元素边框之间的距离
属性：
margin-left: 左外边距
margin-right: 右外边距
margin-top: 上外边距
margin-bottom: 下外边距



### 左外边距



属性: margin-left
值：数字
指的是元素边框和元素边框之间的距离

**注**：像span这样的内联元素，默认情况下，只有左右外边距，没有上下外边距。 为了观察上下外边距的效果，可以采用块级元素，比如div.

```css
<style>
.red{
   border:1px solid red;
   background-color:green;
}
 
.margin{
   border:1px solid red;
   background-color:green;
   margin-left:10px;
}
 
</style>
 
<span class="red"> 无外边距的span  </span>
<span class="red"> 无外边距的span  </span>
 
<br/>
 
<span class="red"> 无外边距的span  </span>
<span class="margin"> 有左外边距的span  </span>
```

## 边框模型

真正决定一个元素的表现形式，是由其边框模型决定的
由图所示
蓝色框即为内容
width:70px 表示内容的大小
红色框即为边框
内容到边框之间的距离，即为内边距 5px
灰色框，是指边框与其他元素之间的距离，即为外边距：10px

```css
<style>
.box{
    width:70px;
    padding:5px;
    margin: 10px;
}
 
div{
   border:1px solid gray;
   font-size:70%;
}
</style>
 
<div>
 其他元素
</div>
 
<div class="box">
   内容宽度70px <br><br>
   内边距：5px <br> <br>
   外边距：10px <br>
</div>
 
<div>
 其他元素
</div>
```

## 超链状态

超链状态有4种
link - 初始状态，从未被访问过
visited - 已访问过
hover - 鼠标悬停于超链的上方
active - 鼠标左键点击下去，但是尚未弹起的时候

### 超链状态

伪类，所谓的伪类即被选中的元素处于某种状态的时候
超链状态有4种
link - 初始状态，从未被访问过
visited - 已访问过
hover - 鼠标悬停于超链的上方
active - 鼠标左键点击下去，但是尚未弹起的时候

```css
<style>
a:link {color: #FF0000}
a:visited {color: #00FF00}
a:hover {color: #FF00FF}
a:active {color: #0000FF}
</style>
  
<a href="http://www.12306.com">超链的不同状态</a>
```

### 去除超链的下划线

默认状态下，超链是有下划线的，但是现在网站上的超链普遍采用无下划线风格。

使用 text-decoration: none [文本修饰的样式](https://how2j.cn/k/css2/css2-text/241.html#step454)来解决

```css
<style>
a.no_underline {text-decoration: none}
</style>
   
<a href="http://www.12306.com">默认的超链</a>
<br>
<a class="no_underline" href="http://www.12306.com">去除了下划线的超链</a>
```

## css隐藏

隐藏元素有两种方式
display:none;
visibility:hidden;

使用display:none; 隐藏一个元素，这个元素将不再占有原空间 “坑” 让出来了
使用 visibility:hidden;隐藏一个元素，这个元素继续占有原空间，只是“看不见”

```css
<style>
div.d{
  display:none;
}
 
div.v{
  visibility:hidden;
}
</style>
 
<div>可见的div1</div>
<div class="d">隐藏的div2,使用display:none隐藏</div>
<div>可见的div3</div>
<div class="v">隐藏的div4,使用visibility:hidden隐藏</div>
<div>可见的div5</div>
```

## css文件

如果把所有的css都写在html文件里面，一旦样式比较多的时候，就会显得不易维护

这个时候就会选择把所有的css内容，放在一个独立文件里

然后在html中引用该文件

通常这个文件会被命名为style.css

### 把样式代码写在style.css，并在html中包含它

创建一个文件叫[style.css](https://how2j.cn/study/style.css)
其内容为

```css
.p1{
  color:red;
}
.span1{
  color:blue;
}
```

然后在html中包含该文件

```css
<link rel="stylesheet" type="text/css" href="/study/style.css" />

```

**注：**style.css文件里，**就不要再使用style标签了**

### css是本地文件 如何包含

在测试的时候，大家写的css文件都是放在本地的，比如d:/style.css
这时就应该写成
href="file://d:/style.css"

# 布局

## css绝对定位

绝对定位
属性：position
值： absolute

通过指定left,top绝对定位一个元素

### 绝对定位

属性：position
值： absolute
设置了绝对定位的元素，相当于该元素被从原文档中删除了
所以”正常文字4“会紧接着出现在 ”正常文字2“后面，而不会留下空档

```css
<style>
p.abs{
  position: absolute;
  left: 150px;
  top: 50px;
}
 
</style>
 
<p >正常文字1</p>
<p >正常文字2</p>
<p class="abs" >绝对定位的文字3</p>
<p >正常文字4</p>
<p >正常文字5</p>
```

![Screen Shot 2020-02-03 at 6.58.29 PM](/Volumes/Untitled 1/笔记/前端/img/绝对定位.png)

### 绝对定位是基于最近的一个定位了的父容器

对于 "绝对定位的文字" 这个p，其定位了的父容器即 class="absdiv" 的div
所以 "绝对定位的文字" 这个p 出现的位置是以这个div 为基础的

```css
<style>
p.abs{
  position: absolute;
  left: 100px;
  top: 50px;
}
.absdiv{
  position: absolute;
  left: 150px;
  top: 50px;
  width:215px;
  border: 1px solid blue;
}
</style>
 
<div>
<p >正常文字a</p>
<p >正常文字b</p>
<p >正常文字c</p>
<p >正常文字d</p>
<p >正常文字e</p>
<p >正常文字f</p>
<p >正常文字g</p>
</div>
 
<div class="absdiv">
这是一个定位了的div
<p class="abs" >绝对定位的文字</p>
</div>
```

![Screen Shot 2020-02-03 at 7.03.52 PM](/Volumes/Untitled 1/笔记/前端/img/绝对定位是基于最近的一个定位了的父容器.png)

### 如果没有定位了的父容器

"绝对定位的文字" 这个p 的父容器div，并没有定位。 所以它的”最近的一个定位了的父容器” 即body

```css
<style>
p.abs{
  position: absolute;
  left: 100px;
  top: 50px;
}
 
</style>
 
<div>
<p >正常文字a</p>
<p >正常文字b</p>
<p >正常文字c</p>
<p >正常文字d</p>
<p >正常文字e</p>
<p >正常文字f</p>
<p >正常文字g</p>
</div>
 
<div>
这个div没有定位
<p class="abs" >绝对定位的文字</p>
</div>
```

![Screen Shot 2020-02-03 at 7.05.18 PM](/Volumes/Untitled 1/笔记/前端/img/如果没有定位了的父容器.png)

### z-index

通过绝对定位可以把一个元素放在另一个元素上，这样位置就重复了。

重复了，就存在一个谁掩盖谁的问题。 这个时候就可以使用

z-index属性， 当z-index的值越大，就表示放上面，z-index:越小就表示放下面。

```css
<style>
img#i1{
  position: absolute;
  left: 60px;
  top: 20px;
  z-index:1;
}
   
  img#i2{
  position: absolute;
  left: 60px;
  top: 120px;
  z-index:-1;
}
  
</style>
  
<div>
<p >正常文字a</p>
<p >正常文字b</p>
<p >正常文字c</p>
<p >正常文字d</p>
<p >正常文字e</p>
<p >正常文字f</p>
<p >正常文字g</p>
</div>
 
<img id="i1" src="https://how2j.cn/example.gif" />
<img id="i2" src="https://how2j.cn/example.gif" />
```

![Screen Shot 2020-02-03 at 7.07.08 PM](/Volumes/Untitled 1/笔记/前端/img/z-index.png)

## css相对定位
属性：position
值：relative
与绝对定位不同的是，相对定位不会把该元素从原文档删除掉，而是在原文档的位置的基础上，移动一定的距离

```css
<style>
p.r{
  position: relative;
  left: 150px;
  top: 50px;
}
  
</style>
  
<p >正常文字1</p>
<p >正常文字2</p>
<p class="r" >相对定位的文字3</p>
<p >正常文字4</p>
<p >正常文字5</p>
```



![Screen Shot 2020-02-03 at 7.09.06 PM](/Volumes/Untitled 1/笔记/前端/img/相对定位.png)

## css浮动

浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。

属性：float
值： left,right

### 文字向右浮动

文字向右浮动
浮动后，原来的“**坑**”就让出来了
并且是在原来的高度的基础上，向右浮动

```css
<style>
.f{
  float:right;
}
 
</style>
 
<div >正常文字1</div>
<div >正常文字2</div>
<div class="f">浮动的文字</div>
<div >正常文字4</div>
<div >正常文字5</div>
```

![Screen Shot 2020-02-03 at 7.10.59 PM](/Volumes/Untitled 1/笔记/前端/img/ 文字向右浮动.png)

### 文字向左浮动

文字向左浮动
首先，向左浮动后，会把“坑”让出来，这个时候"正常的文字4“ 就会过来试图占这个坑，但是，发现 “浮动的文字”并没有走，结果，就只好排在它后面了

```css
<style>
.f{
  float:left;
}
 
</style>
 
<div >正常文字1</div>
<div >正常文字2</div>
<div class="f">浮动的文字</div>
<div >正常文字4</div>
<div >正常文字5</div>
```

效果

```
正常文字1
正常文字2
浮动的文字正常文字4
正常文字5
```

### 文字围绕图片

当图片不浮动时，文字就会换行出现在下面
当图片浮动时，文字围绕着图片
和步骤2一样，当图片浮动的时候，就会让出这个“坑”出来，这个时候文字就试图去填补这个“坑”，结果发现，尼玛，图片没走，那就只好围绕图片摆放了

```css
<style>
.f{
  float:left;
}
 
div{
  width:320px;
}
</style>
 
<div >
 <img src="https://how2j.cn/example.gif"/>
 
<p>  当图片不浮动时，文字就会换行出现在下面
  当图片不浮动时，文字就会换行出现在下面
  当图片不浮动时，文字就会换行出现在下面
  当图片不浮动时，文字就会换行出现在下面
  当图片不浮动时，文字就会换行出现在下面
  当图片不浮动时，文字就会换行出现在下面
</p>
</div>
 
<div >
 <img  class="f" src="https://how2j.cn/example.gif"/>
 
<p>  当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
</p>
</div>
```

### 文字不想围绕图片

不允许出现浮动元素
属性:clear
值: left right both none
如果p左边出现了浮动的元素，如此例，则设置clear:left 即达到不允许浮动元素出现在左边的效果

```css
<style>
.f{
  float:left;
}
 
div{
  width:320px;
}
 
.clearp{
  clear:left;
}
 
</style>
 
<div >
 <img  class="f" src="https://how2j.cn/example.gif"/>
 
<p>  当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
 当图片浮动时，文字围绕着图片
</p>
</div>
 
<div >
 <img  class="f" src="https://how2j.cn/example.gif"/>
 
<p class="clearp">  当图片浮动时，文字却不想围绕图片
当图片浮动时，文字却不想围绕图片
当图片浮动时，文字却不想围绕图片
当图片浮动时，文字却不想围绕图片
 
</p>
</div>
```

![Screen Shot 2020-02-03 at 7.15.55 PM](/Volumes/Untitled 1/笔记/前端/img/文字不想围绕图片.png)

### 水平排列div

默认的div排列是会换行的
如果使用float就可以达到水平排列的效果，通常会用在菜单，导航栏等地方
如果超出了父容器，还会有自动换行的效果

```css
<style>
div#floatingDiv{
  width:200px;
}
div#floatingDiv div{
   float:left;
}
</style>
默认的div排列是会换行的
 
 <div>
       菜单1
 </div>
 <div>
       菜单2
 </div>
 <div>
       菜单3
 </div>
 
如果使用float就可以达到水平排列的效果，通常会用在菜单，导航栏等地方
 
如果超出了父容器，还会有自动换行的效果
 
<div id="floatingDiv">
  <div>
       菜单1
 </div>
 <div>
       菜单2
 </div>
 <div>
       菜单3
 </div>
 <div>
       菜单4
 </div>
 <div>
       菜单5
 </div>
 <div>
       菜单6
 </div>
</div>
```

![Screen Shot 2020-02-03 at 7.21.56 PM](/Volumes/Untitled 1/笔记/前端/img/水平排列div.png)

## css显示方式

元素的display显示方式有多种，隐藏、块级、内联、内联-块级

| 关键字               | 简介      | 示例代码                                                     |
| :------------------- | :-------- | :----------------------------------------------------------- |
| display:none         | 隐藏      | [示例代码](https://how2j.cn/k/css2/css2-display/767.html#step2906) |
| display:block        | 块级      | [示例代码](https://how2j.cn/k/css2/css2-display/767.html#step2907) |
| display:inline       | 内联      | [示例代码](https://how2j.cn/k/css2/css2-display/767.html#step2908) |
| display:inline-block | 内联-块级 | [示例代码](https://how2j.cn/k/css2/css2-display/767.html#step2909) |
|                      |           |                                                              |

### 隐藏

**display:none;** 使得被选择的元素隐藏，并且不占用原来的位置

```css
<style>
div.d{
  display:none;
}
 
</style>
  
<div>可见的div1</div>
<div class="d">隐藏的div2,使用display:none隐藏</div>
<div>可见的div3</div>
```

效果：

可见的div1

可见的div3

### 块级

**display:block;** 表示块级元素
块级元素会自动在前面和后面加上换行，并且在其上的width和height也能够生效

div默认是块级元素
span默认是内联元素(不会有换行,width和height也不会生效)

```css
<style>
div,span{
   border: 1px solid lightgray;
   margin:10px;
   width:200px;
   height:100px;
}
 
.d{
  display:block;
}
</style>
  
<div>普通的div块</div>
<span>这是普通span</span> <span>这是普通span</span> <span>这是普通span</span>
<span class="d">这是span,被改造成了块级元素</span>
```

![Screen Shot 2020-02-03 at 7.29.24 PM](/Volumes/Untitled 1/笔记/前端/img/块级.png)

### 内联

**display:inline;** 表示内联元素
内联元素前后没有换行，并且在其上的width和height也无效。 其大小由其中的内容决定

div默认是块级元素
span默认是内联元素

```css
<style>
div,span{
   border: 1px solid lightgray;
   margin:10px;
   width:200px;
   height:100px;
}
 
.s{
  display:inline;
}
</style>
 
<span>这是普通span</span> <span>这是普通span</span> <span>这是普通span</span>
  
<div class="s">这是div，被改造成了内联元素</div>
```

 ### 内联-块级

内联是不换行，但是不能指定大小
块级时能指定大小，但是会换行

有时候，需要元素处于同一行，同时还能指定大小，这个时候，就需要用到**内联-块级** inline-block

```css
<style>
span{
   display:inline-block;
   border: 1px solid lightgray;
   margin:10px;
   width:100px;
}
</style>
像这样 ，每个都能设置宽度 ，同时还能在同一行。
<br>
 
<span>盖伦</span>
<span>蒙多医生</span>
<span>奈德丽</span>
<span>蒸汽机器人</span>
```

![Screen Shot 2020-02-03 at 7.32.44 PM](/Volumes/Untitled 1/笔记/前端/img/内联-块级.png)

## 水平居中

### 内容居中

```css
<style>
div{
  border:1px solid lightgray;
  margin:10px;
}
</style>
<div align="center">
通过设置属性align="center" 居中的内容
</div>
 
<div  style="text-align:center">
通过样式style="text-align:center" 居中的内容
</div>
```

### 元素居中

```css
<style>
  div{
     border: solid 1px lightgray;
     margin: 10px;
  }
  span{
     border: solid 1px lightskyblue;
  }
</style>
<div> 默认情况下div会占用100%的宽度,所以无法观察元素是否居中</div>
 
<div style="width:300px;margin:0 auto">
  设置本div的宽度，然后再使用样式 margin: 0 auto来使得元素居中</div>
 
<span style="width:300px;margin:0 auto">
  span 是内联元素，无法设置宽度，所以不能通过margin:0 auto居中</span>
 
<div style="text-align:center">
  <span>span的居中可以通过放置在div中，然后让div text-align实现居中</span>
</div>
```

![Screen Shot 2020-02-03 at 7.36.02 PM](/Volumes/Untitled 1/笔记/前端/img/元素居中.png)

## 左侧固定

```css
<style>
 .left{
   width:200px;
   float:left;
   background-color:pink
  }
  .right{
    overflow:hidden;
    background-color:lightskyblue;
  }
</style>
 
<div class="left">左边固定宽度</div>
 
<div class="right">右边自动填满</div>
```

## 垂直居中

### line-height方式

```css
<style>
#d {
line-height: 100px;
}
div{
  border:solid 1px lightskyblue;
}
</style>
 
<div id="d">line-height 适合单独一行垂直居中</div>
```

![Screen Shot 2020-02-03 at 7.41.54 PM](/Volumes/Untitled 1/笔记/前端/img/垂直居中.png)

### 内边距方式

借助设置相同的上下内边距，实现垂直居中效果，可以用在多行文本上

```css
<style>
#d {
    padding: 30 0;
}
div{
    border:solid 1px lightskyblue;
}
</style>
 
<div id="d">多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容 多行内容  </div>
```

### table方式

首先通过**display: table-cell;**把div用单元格的形式显示，然后借用单元格的垂直居中**vertical-align: middle;** 来达到效果。
这样对图片也可以居中，上一步 line-height就不能对图片居中。

```css
<style>
#d {
display: table-cell;
vertical-align: middle;
height:200px;
}
 
div{
  border:solid 1px lightskyblue;
}
</style>
  
<div id="d">
<img src="https://how2j.cn/example.gif">
</div>
```

## 贴在下方

首先把蓝色div设置为相对定位

然后把内部的绿色div设置为绝对定位， **bottom: 0**表示贴在下面

```css
<style>
  #div1
    {
      position: relative;
      height: 300px;
      width: 90%;
      background-color: skyblue;
    }
  #div2
  {
    position: absolute;
    bottom: 0;
    height: 30px;
    width: 100%;
    background-color: lightgreen;
  }
</style>
 
<div id="div1">
    <div id="div2"> 无论蓝色div高度如何变化，绿色div都会贴在下面
    </div>
</div>
```

## css块之间的空格

### 块之间有空格

如果多个span连续编写，像这样：

```css
<span>连续的span</span><span>连续的span</span>
```

是不会有空格的
但是真正开发代码的时候，一般不会连续书写span,而是不同的span之间有回车换行，比如这样：

```css
<span>有换行的span</span>
<span>有换行的span</span>
<span>有换行的span</span>
```

```css
// 结果
连续的span连续的span连续的span连续的span
有换行的span 有换行的span 有换行的span
```

### 解决办法

使用float来解决。
float使用完毕之后，记得在下面加上 <div style="clear:both"></div> 用于使得后续的元素，不会和这些span重复在一起

```css
<style>
div.nocontinue span{
border-bottom:2px solid lightgray;
  float:left;
}
</style>
  
<div class="nocontinue">
<span>有换行的span</span>
<span>有换行的span</span>
<span>有换行的span</span>
</div>
 
<div style="clear:both"></div>
 
<div>后续的内容</div>
```

```
//结果
有换行的span有换行的span有换行的span
后续的内容
```


