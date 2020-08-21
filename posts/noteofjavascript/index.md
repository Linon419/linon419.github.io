# JavaScript高级程序设计笔记


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
2. 标识符-  第一个字符必须是一个字母，下划线(_)或一个美元符号($). 其他字符可以是字母，下划线，美元符号或数字
3. 严格模式- 一些不确定的行为将得到处理，而且对于某些不安全错误也会抛出提示：用法"use strict";

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

所有类型都可以转换为boolean类型，用方法Boolean()


