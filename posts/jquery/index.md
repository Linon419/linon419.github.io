# JQuery 笔记

## 常见方法

| 关键字 | 简介                                        | 示例代码                                                     |
| :----- | :------------------------------------------ | :----------------------------------------------------------- |
| val    | 取值                                        | [示例代码](https://how2j.cn/k/jquery/jquery-methods/528.html#step1220) |
| html   | 获取元素内容,如果有子元素，保留标签         | [示例代码](https://how2j.cn/k/jquery/jquery-methods/528.html#step1221) |
| text   | 获取元素内容,如果有子元素，不包含子元素标签 |                                                              |



### 取值

```javascript
<script src = "https://how2j.cn/study/jquery.min.js"></script>
<script>
	$(function(){
  		$("#b1").click(function(){
        	alert($("#input1").val());                	
      });
  });    
</script>

<button id="b1">取值</button>
<input type = 'text' id = 'input1' value = "hahahahahahah">
```

### 获取元素内容,如果有子元素，保留标签

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
$(function(){
   $("#b1").click(function(){
      alert($("#d1").html());
   });
});
  
</script>
  
<button id="b1">获取文本内容</button>
   
<br>
<br>
  
<div id="d1">
这是div的内容
<span>这是div里的span
</span>
</div>
```

### 获取元素内容,如果有子元素，不包含子元素标签

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
      alert($("#d1").text());
   });
});
   
</script>
   
<button id="b1">获取文本内容</button>
    
<br>
<br>
   
<div id="d1">
这是div的内容
<span>这是div里的span
</span>
</div>
```

## CSS

| 关键字      | 简介      | 示例代码                                                     |
| :---------- | :-------- | :----------------------------------------------------------- |
| addClass    | 增加class | [示例代码](https://how2j.cn/k/jquery/jquery-css/470.html#step983) |
| removeClass | 删除class | [示例代码](https://how2j.cn/k/jquery/jquery-css/470.html#step984) |
| toggleClass | 切换class | [示例代码](https://how2j.cn/k/jquery/jquery-css/470.html#step985) |
| css         | css函数   |                                                              |

### 增加class

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>

<script>
	$(function(){
  $("#b1").click(function(){
    $("#d").addClass("pink");
  });  
});
</script>
<style>
  .pink{
    background-color:pink;
  }
</style>
<div id ='d'>
  
  Hellbhvvdfvdfv
</div>  
  
```

### 删除class

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
$(function(){
   $("#b1").click(function(){
      $("#d").removeClass("pink");
   });
  
});
  
</script>
  <button id="b1">删除背景色</button>
<br>
<br>
 
<style>
.pink{
   background-color:pink;
}
</style>
  
<div id="d" class="pink">
  
Hello JQuery
  
</div>
```

### 切换class

通过toggleClass() 切换一个样式中的class
这里的**切换**，指得是：
如果存在就删除
如果不存在，就添加

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
$(function(){
   $("#b1").click(function(){
      $("#d").toggleClass("pink");
   });
   
});
   
</script>
  <button id="b1">切换背景色</button>
<br>
<br>
  
<style>
.pink{
   background-color:pink;
}
</style>
   
<div id="d" >
   
Hello JQuery
   
</div>
```

### css函数

通过css函数直接切换样式

`css(property,value)`

第一个参数是样式属性，第二个参数是样式值

`css({p1:v1,p2:v2})`

参数是 {} 包含的属性值对。
属性值对之间用 逗号，分割
属性值之间用 冒号 ：分割
属性和值都需要用引号 “

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
<script>
  $(function(){
  $("#b1").click(function(){
    $("#d1").css("background-color","pink");
  });
    
    $("#b2").click(function(){
      $("#d2").css({"background-color":"pink","color":"green"});
    });
});
</script>


<button id = "b1">danyi</button>
<button id = "b2">mult</button>
<div id="d1">
  dan yi yang shi
  </div>

<div id = "d2">
  mult yang shi
  </div>
```

## 选择器

| 关键字                                                       | 简介         | 示例代码                                                     |
| :----------------------------------------------------------- | :----------- | :----------------------------------------------------------- |
| $("tagName")                                                 | 元素         | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step968) |
| $("id")                                                      | id           | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step969) |
| $("className")                                               | 类           | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step970) |
| $("selector1 selector2")                                     | 层级         | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step971) |
| :first :last                                                 | 最先最后     | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step972) |
| :odd :even                                                   | 奇偶         | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step973) |
| :hidden :visible                                             | 可见性       | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step975) |
| [attribute] [attribute=value] [attribute!=value] [attribute^=value] [attribute$=value] [attribute*=value] | 属性         | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step976) |
| :input :button :radio :checkbox :text :file :submit :image :reset | 表单对象     | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step977) |
| :enabled :disabled :checked :selected                        | 表单对象属性 | [示例代码](https://how2j.cn/k/jquery/jquery-selector/468.html#step978) |
| this                                                         | 当前元素     |                                                              |

### 元素

$("tagName")
根据 标签名 选择所有该标签的元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
$(function(){
   $("#b1").click(function(){
      $("div").addClass("pink");
   });
   
});
   
</script>
  <button id="b1">给所有的div元素增加背景色</button>
<br>
<br>
  
<style>
.pink{
   background-color:pink;
}
</style>
   
<div >
Hello JQuery
</div>
 
<div >
Hello JQuery
</div>
 
<div >
Hello JQuery
</div>
```

### id

$("#id")
根据 id 选择元素
id应该是唯一的，如果id重复，则只会选择第一个。

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
      $("#d1").addClass("pink");
   });
    
});
    
</script>
  <button id="b1">给id=d1的div增加背景色</button>
<br>
<br>
   
<style>
.pink{
   background-color:pink;
}
</style>
    
<div id="d1">
Hello JQuery
</div>
  
<div id="d2" >
Hello JQuery
</div>
  
<div  id="d3">
Hello JQuery
</div>
```

### 类

$(".className")
根据 class 选择元素

```javascript
 <script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
      $(".d").addClass("pink");
   });
    
});
    
</script>
  <button id="b1">给class='d'的div增加背景色</button>
<br>
<br>
   
<style>
.pink{
   background-color:pink;
}
</style>
    
<div class="d">
Hello JQuery
</div>
  
<div class="d" >
Hello JQuery
</div>
  
<div  >
Hello JQuery
</div>
```

### 层级

$("selector1 selector2")
选择 selector1下的selector2元素 。
在本例中 选择id=d3的div下的span元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
$(function(){
   $("#b1").click(function(){
      $("div#d3 span").addClass("pink");
   });
     
});
     
</script>
  <button id="b1">给id='d3'的div 下的 span 增加背景色</button>
<br>
<br>
    
<style>
.pink{
   background-color:pink;
}
</style>
     
<div class="d">
  <span>Hello JQuery</span>
    
</div>
   
<div class="d" >
  <span>Hello JQuery</span>
</div>
   
<div id="d3" >
  <span>Hello JQuery</span>
</div>
```

### 最先最后

$(selector:**first**) 满足选择器条件的**第一个**元素
$(selector:**last**) 满足选择器条件的**最后一个**元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
     
<script>
$(function(){
   $("#b1").click(function(){
      $("div:first").addClass("pink");
   });
      
   $("#b2").click(function(){
      $("div:last").addClass("pink");
   });
 
});
      
</script>
  <button id="b1">第一个增加背景色</button>
  <button id="b2">最后一个增加背景色</button>
<br>
<br>
     
<style>
.pink{
   background-color:pink;
}
</style>
      
<div>
  <span>Hello JQuery</span>
     
</div>
    
<div >
  <span>Hello JQuery</span>
</div>
    
<div >
  <span>Hello JQuery</span>
</div>
```

### 奇偶

$(selector:**odd**) 满足选择器条件的**奇数**元素
$(selector:**even**) 满足选择器条件的**偶数**元素
因为是**基零**的，所以第一排的下标其实是0(是偶数)

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
      
<script>
$(function(){
   $("#b1").click(function(){
      $("div:odd").toggleClass("pink");
   });
       
   $("#b2").click(function(){
      $("div:even").toggleClass("green");
   });
  
});
       
</script>
  <button id="b1">切换奇数背景色</button>
  <button id="b2">切换偶数背景色</button>
<br>
<br>
      
<style>
.pink{
   background-color:pink;
}
.green{
   background-color:green;
}
</style>
       
<div>
  <span>Hello JQuery 0</span>
      
</div>
 
<div>
  <span>Hello JQuery 1</span>
      
</div>
     
<div >
  <span>Hello JQuery 2</span>
</div>
     
<div >
  <span>Hello JQuery 3</span>
</div>
 
<div >
  <span>Hello JQuery 4</span>
</div>
 
</div>
     
<div >
  <span>Hello JQuery 5</span>
</div>
     
<div >
  <span>Hello JQuery 6</span>
</div>
```

### 可见性

$(selector:**hidden**) 满足选择器条件的**不可见的**元素
$(selector:**visible**) 满足选择器条件的**可见的**元素
**注；** **div:visible** 和**div :visible(有空格)**是不同的意思
div:visible 表示选中可见的div
div :visible(有空格) 表示选中div下可见的元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
        
<script>
$(function(){
   $("#b1").click(function(){
     $("div:visible").hide();
   });
   $("#b2").click(function(){
      $("div:hidden").show();     
   });
});
         
</script>
  <button id="b1">隐藏可见的</button>
  <button id="b2">显示不可见的</button>
  
<br>
<br>
        
<style>
.pink{
   background-color:pink;
}
  
</style>
         
<div>
  <span>Hello JQuery 1</span>
        
</div>
       
<div >
  <span>Hello JQuery 2</span>
</div>
       
<div >
  <span>Hello JQuery 3</span>
</div>
   
<div >
  <span >Hello JQuery 4</span>
</div>
   
</div>
       
<div >
  <span>Hello JQuery 5</span>
</div>
       
<div >
  <span>Hello JQuery 6</span>
</div>
```

### 属性

$(selector**[attribute]**) 满足选择器条件的**有某属性的**元素
$(selector**[attribute=value]**) 满足选择器条件的属性**等于value**的元素
$(selector**[attribute!=value]**) 满足选择器条件的属性**不等于value**的元素
$(selector**[attribute^=value]**) 满足选择器条件的属性**以value开头**的元素
$(selector**[attribute$=value]**) 满足选择器条件的属性**以value结尾**的元素
$(selector**[attribute\*=value]**) 满足选择器条件的**属性包含value**的元素

**注：** 一般不要使用[class=className] 而应该使用.className
因为使用$("[class='className']") .toggleClass("anotherClassName")
会导致class变成**className anotherClassName**,再次 使用 [class=className] 就无法选中了
而.className没有这个问题。

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
       
<script>
$(function(){
   $("#b1").click(function(){
      $("div[id]").toggleClass("border");
   });
   $("#b2").click(function(){
      $("div[id='pink']").toggleClass("border");
   });
   $("#b3").click(function(){
      $("div[id!='pink']").toggleClass("border");
   });
   $("#b4").click(function(){
      $("div[id^='p']").toggleClass("border");
   });
   $("#b5").click(function(){
      $("div[id$='k']").toggleClass("border");
   });
   $("#b6").click(function(){
      $("div[id*='ee']").toggleClass("border");
   });
 
});
        
</script>
  <button id="b1">给有id属性的div切换边框</button>
  <button id="b2">给id=pink的div切换边框</button>
  <button id="b3">给有id!=pink属性的div切换边框</button>
  <button id="b4">给有id以p开头的div切换边框</button>
  <button id="b5">给有id以k结尾的div切换边框</button>
  <button id="b6">给有id包含ee的div切换边框</button>
 
<br>
<br>
       
<style>
.pink{
   background-color:pink;
}
.green{
   background-color:green;
}
.border{
   border: 1px blue solid;
    
}
 
button{
   margin-top:10px;
   display:block;
}
 
div{
  margin:10px;
}
</style>
        
<div id="pink">
    id=pink的div
</div>
      
<div id="green">
  id=green的div
</div>
      
<div >
   没有id的div
</div>
```

### 表单对象

表单对象选择器 指的是选中form下会出现的输入元素
**:input** 会选择所有的输入元素，不仅仅是input标签开始的那些，还包括[textarea](https://how2j.cn/k/html/html-textarea/196.html#step370),[select](https://how2j.cn/k/html/html-select/195.html#step366)和[button](https://how2j.cn/k/html/html-button/206.html)
**:button** 会选择**type=button**的input元素和**button**元素
**:radio** 会选择**单选框**
**:checkbox**会选择**复选框**
**:text**会选择**文本框**，但是不会选择文本域
**:submit**会选择**提交按钮**
**:image**会选择**图片型提交按钮**
**:reset**会选择**重置按钮**

**注意:** 第7行

$("td[rowspan!=13] "+value).toggle(500);

$("td[rowspan!=13] 后面有一个空格，表示层级选择器，如果没有就会出错
**toggle(500)** 表示在显示与隐藏之间来回切换，生效时间是500毫秒

**注：** :submit会把<button>元素选中，因为在一些浏览器中，<button>元素的type默认值是submit，所以会选中它。 关于这个问题，

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
<head>
    <script>
        $(function(){
            $(".b").click(function(){
                var value = $(this).val();
                $("td[rowspan!=13] "+value).toggle(500);
            });
        });
    </script>
</head>


<style>
    table{
        border-collapse:collapse;
            table-layout:fixed;
        width:80%;
    }
    table td{
        border-bottom: 1px solid #ddd;
        padding-bottom: 5px;
        padding-top: 5px;
    }
     
    div button{
        display:block;
    }
     
</style>
<body>
    <table>
        <tr>
            <td rowspan="13">
                <div >
                    <button value=":input" class="b">切换所有的:input</button>
                    <button value=":button" class="b">切换:button</button>
                    <button value=":radio" class="b">切换:radio</button>     
                    <button value=":checkbox" class="b">切换:checkbox</button>       
                    <button value=":text" class="b">切换:text</button>       
                    <button value=":password" class="b">切换:password</button>       
                    <button value=":file" class="b">切换:file</button>       
                    <button value=":submit" class="b">切换:submit</button>       
                    <button value=":image" class="b">切换:image</button>     
                    <button value=":reset" class="b">切换:reset</button>         
                </div> 
            </td>
        </tr>
        <tr>
            <td >input按钮</td>
            <td >:button</td>
            <td><input type="button" value="input按钮"/></td>
          </tr>
           
          <tr>
            <td>button按钮</td>
            <td >:button</td>
            <td><button>Button按钮</button></td>
          </tr>
          <tr>
            <td>单选框</td>
            <td >:radio</td>
            <td><input type="radio" ></td>
          </tr>
          <tr>
            <td>复选框</td>
            <td >:checkbox</td>
            <td><input type="checkbox"  ></td>
          </tr>
           
          <tr>
            <td>文本框</td>
            <td >:text</td>
            <td><input type="text" /></td>
          </tr>
          <tr>
            <td>文本域</td>
            <td ></td>
            <td><textarea></textarea></td>
          </tr>
          <tr>
            <td>密码框</td>
            <td >:password</td>
            <td><input type="password" /></td>
          </tr>
          <tr>
            <td>下拉框</td>
            <td ></td>
            <td><select><option>Option</option></select></td>
          </tr>
           
          <tr>
            <td>文件上传</td>
            <td >:file</td>
            <td> <input type="file" /></td>
          </tr>
           
          <tr>
            <td>提交按钮</td>
            <td >:submit</td>
            <td><input type="submit" /></td>
          </tr>
          <tr>
            <td>图片型提交按钮</td>
            <td >:image</td>
            <td><input type="image" src="https://how2j.cn/example.gif" /></td>
          </tr>
           
          <tr>
            <td>重置按钮</td>
            <td >:reset</td>
            <td><input type="reset" /></td>
          </tr>
           
    </table>
</body>
```

### 表单对象属性

**:enabled**会选择**可用的输入元素** **注：**输入元素的默认状态都是可用
**:disabled**会选择**不可用的输入元素**
**:checked**会选择**被选中的单选框和复选框** **注：** checked在部分浏览器上(火狐,chrome)也可以选中selected的option
**:selected**会选择**被选中的option元素**

```javascript
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
</head>
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
$(function(){
   $(".b").click(function(){
      var value = $(this).val();
      $("td[rowspan!=13] "+value).toggle(500);
   });
    
   $(".b2").click(function(){
      var value = $(this).val();
      var options = $("td[rowspan!=13] "+value);
      alert("选中了"+options.length+"条记录！");
   });
        
});
        
</script>
 
<style>
table{
    border-collapse:collapse;
        table-layout:fixed;
    width:80%;
}
table td{
    border-bottom: 1px solid #ddd;
    padding-bottom: 5px;
    padding-top: 5px;
}
 
div button{
    display:block;
}
 
.border{
   border: 1px blue solid;
     
}
 
</style>
 
<table>
    <tr>
         
        <td rowspan="13" valign="top" width="120">
            <div >
                <button value=":enabled" class="b">切换:enabled</button>
                <button value=":disabled" class="b">切换:disabled</button>       
                <button value=":checked" class="b">切换:checked</button>     
                <button value=":selected" class="b2">:selected数量</button>      
            </div>           
        </td>
        <td width="120">说明</td>
        <td width="120">表单对象属性</td>
        <td width="100px">示例</td>
    </tr>
<tr>
  <td >enabled的按钮</td>
  <td >:enabled</td>
  <td><input type="button" enabled="enabled" value="enabled的按钮"/></td>
</tr>
 
<tr>
  <td >disabled的按钮</td>
  <td >:disabled</td>
  <td><input type="button" disabled="disabled" value="disabled的按钮"/></td>
</tr>
 
  <td >选中的复选框</td>
  <td >:checked</td>
  <td>
     
    <input type="radio" checked="checked" ><br>
    <input type="radio" ><br>
    <input type="checkbox" ><br>
    <input type="checkbox" checked="checked" >
  </td>
 
<tr>
  <td>选中的下拉列表</td>
  <td >:selected</td>
  <td>
    <select size="3" multiple="multiple">
       <option selected="selected">苍老师</option>
       <option >高树玛利亚</option>
       <option selected="selected">遥美</option>
    </select>
  </td>
</table>
 
<form>
 
</form>
```

### 当前元素

在监听函数中使用 **$(this)**，即表示触发该事件的组件。

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
     $(this).hide();
   });
    
});
</script>
  
<button id="b1">点击隐藏</button>
```

## 筛选器

| 关键字                 | 简介                   | 示例代码                                                     |
| :--------------------- | :--------------------- | :----------------------------------------------------------- |
| first() last() eq(num) | 第一个 最后一个 第几个 | [示例代码](https://how2j.cn/k/jquery/jquery-535/535.html#step1247) |
| parent() parents()     | 父 祖先                | [示例代码](https://how2j.cn/k/jquery/jquery-535/535.html#step1248) |
| children() find()      | 儿子 后代              | [示例代码](https://how2j.cn/k/jquery/jquery-535/535.html#step1249) |
| siblings()             | 同级                   |                                                              |

### 第一个，最后一个，第几个

首先通过 $("div") 选择了多个div元素，接下来做进一步的筛选
**first()** 第1个元素
**last()** 最后一个元素
**eq(num)** 第num个元素
**注:** num基0

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
       
<script>
$(function(){
   $("#b1").click(function(){
      $("div").first().toggleClass("pink");
   });
 
   $("#b2").click(function(){
      $("div").last().toggleClass("pink");
   });
 
   $("#b3").click(function(){
      $("div").eq(4).toggleClass("pink");
   });
        
});
        
</script>
  <button id="b1">切换第1个div背景色</button>
  <button id="b2">切换最后1个div背景色</button> 
  <button id="b3">切换第5个div背景色</button>
 
<br>
<br>
       
<style>
.pink{
   background-color:pink;
}
 
</style>
        
<div>
  <span>Hello JQuery 1</span>
       
</div>
      
<div >
  <span>Hello JQuery 2</span>
</div>
      
<div >
  <span>Hello JQuery 3</span>
</div>
  
<div >
  <span>Hello JQuery 4</span>
</div>
  
</div>
      
<div >
  <span>Hello JQuery 5</span>
</div>
      
<div >
  <span>Hello JQuery 6</span>
</div>
```

## 父，祖先

**parent()** 选取最近的一个父元素
**parents()** 选取所有的祖先元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
        
<script>
$(function(){
  $("#b1").click(function(){
     $("#currentDiv").parent().toggleClass("b");
  });
  $("#b2").click(function(){
     $("#currentDiv").parents().toggleClass("b");
  });
 
});
</script>
 
<style>
div{
   padding:20px;
}
 
div#grandParentDiv{
 background-color:pink;
}
 
div#parentDiv{
 background-color:green;
}
 
div#currentDiv{
 background-color:red;
}
 
.b{
   border: 2px solid black;
}
 
</style>
 
<button id="b1">改变parent()的边框</button>
 
<button id="b2">改变parents()的边框</button>
 
<div id="grandParentDiv" >
  祖先元素
  <div id="parentDiv">
  父元素
    <div id="currentDiv">当前元素</div> 
  </div>
</div>
```



## 儿子，后代

**children():** 筛选出儿子元素 (紧挨着的子元素)
**find(selector):** 筛选出后代元素
注: find() 必须使用参数 selector

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
          
<script>
$(function(){
  $("#b1").click(function(){
     $("#currentDiv").children().toggleClass("b");
  });
  $("#b2").click(function(){
     $("#currentDiv").find("div").toggleClass("b");
  });
   
});
</script>
   
<style>
div{
   padding:20px;
}
   
div.grandChildrenDiv{
 background-color:pink;
}
   
div.childrenDiv{
 background-color:green;
 margin:10px;
}
   
div#currentDiv{
 background-color:red;
}
   
.b{
   border: 2px solid black;
}
   
</style>
   
<button id="b1">改变children()的边框</button>
   
<button id="b2">改变find()的边框</button>
   
<div id="currentDiv" >
  当前元素
  <div class="childrenDiv">
  儿子元素1
    <div class="grandChildrenDiv">后代元素n</div> 
  </div>
  <div class="childrenDiv">
  儿子元素2
    <div class="grandChildrenDiv">后代元素n</div> 
  
  </div>
    
</div>
```

## 同级

**siblings():** 同级(同胞)元素

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
         
<script>
$(function(){
  $("#b1").click(function(){
     $("#currentDiv").siblings().toggleClass("b");
  });
  
});
</script>
  
<style>
div{
   padding:20px;
   background-color:pink;
   margin:10px;
}
  
div#parentDiv{
 background-color:green;
}
  
div#currentDiv{
 background-color:red;
}
  
.b{
   border: 2px solid black;
}
  
</style>
  
<button id="b1">给同级加上边框</button>
  
<div id="parentDiv" >
  父元素
  <div id="currentDiv">
    当前元素
  </div>
  <div >
    同级元素
  </div>
  <div >
    同级元素
  </div>
</div>
```

## 属性

| 关键字        | 简介             | 示例代码                                                     |
| :------------ | :--------------- | :----------------------------------------------------------- |
| attr          | 获取             | [示例代码](https://how2j.cn/k/jquery/jquery-attribute/469.html#step980) |
| attr(属性,值) | 修改             | [示例代码](https://how2j.cn/k/jquery/jquery-attribute/469.html#step981) |
| removeAttr    | 删除             | [示例代码](https://how2j.cn/k/jquery/jquery-attribute/469.html#step982) |
| prop与attr    | prop与attr的区别 |                                                              |

### 获取

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
$(function(){
   $("#b1").click(function(){
      alert("align属性是:" + $("#h").attr("align") );
   });
   $("#b2").click(function(){
      alert("game属性是:" + $("#h").attr("game") );
   });
});
  
</script>
  
<button id="b1">获取align属性</button>
  
<button id="b2">获取自定义属性 game</button>
  
<br>
<br>
  
<h1 id="h" align="center" game="LOL">居中标题</h1>
```

### 修改

通过attr(attr,value)修改属性

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
      $("#h").attr("align","right") ;
   });
 
});
   
</script>
   
<button id="b1">修改align属性为right</button>
   
<br>
<br>
   
<h1 id="h" align="center" >居中标题</h1>
```

### 删除

通过removeAttr(attr)删除属性

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
   $("#b1").click(function(){
         $("#h").removeAttr("align");
   });
});
   
</script>
   
<button id="b1">删除align属性</button>
 
<br>
<br>
   
<h1 id="h" align="center" game="LOL">居中标题</h1>
```

### prop与attr的区别

与**prop**一样**attr**也可以用来获取与设置元素的属性。
区别在于，对于**自定义属性**和**选中属性**的处理。
选中属性指的是 checked,selected 这2种属性
\1. 对于自定义属性 attr能够获取，prop不能获取
\2. 对于选中属性
attr **只能获取初始值**， 无论是否变化
prop 能够访问变化后的值，并且以**true|false**的布尔型返回。
所以在访问表单对象属性的时候，应该采用prop而非attr

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
$(function(){
   $("#b1").click(function(){
      alert("game属性是:" + $("#c").attr("game") );
   });
 
   $("#b2").click(function(){
      alert("game属性是:" + $("#c").prop("game") );
   });
 
   $("#b3").click(function(){
      alert("checked属性是:" + $("#c").attr("checked") );
   });
 
   $("#b4").click(function(){
      alert("checked属性是:" + $("#c").prop("checked") );
   });
 
});
  
</script>
  
<style>
button{
  display:block;
}
</style>
 
<button id="b1">通过attr获取自定义属性 game</button>
<button id="b2">通过prop获取自定义属性 game</button>
<button id="b3">通过attr获取 checked属性</button>
<button id="b4">通过prop获取 checked属性</button>
  
<br>
<br>
  
<input type="checkbox"  id="c" game="LOL" checked="checked"> 选中的复选框
```

### 效果

| 关键字                           | 简介                                | 示例代码                                                     |
| :------------------------------- | :---------------------------------- | :----------------------------------------------------------- |
| show hide toggle                 | 显示 隐藏 切换                      | [示例代码](https://how2j.cn/k/jquery/jquery-effect/472.html#step987) |
| slideUp slideDown slideToggle    | 向上滑动 向下滑动 滑动切换          | [示例代码](https://how2j.cn/k/jquery/jquery-effect/472.html#step988) |
| fadeIn fadeOut fadeToggle fadeTo | 淡入 淡出 淡入淡出切换 指定淡入程度 | [示例代码](https://how2j.cn/k/jquery/jquery-effect/472.html#step989) |
| animate                          | 自定义动画效果                      | [示例代码](https://how2j.cn/k/jquery/jquery-effect/472.html#step990) |
| callback                         | 回调函数                            |                                                              |

### 显示，隐藏，切换

**显示 隐藏 切换** 分别通过**show()**, **hide()**,**toggle()**实现
也可以加上毫秒数，表示延时操作,比如**show(2000)**

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
$(function(){
var div = $("#d");
   $("#b1").click(function(){
      div.hide();
   });
   $("#b2").click(function(){
      div.show();
   });
   $("#b3").click(function(){
      div.toggle();
   });
   $("#b4").click(function(){
      div.show(1000);
   });
   $("#b5").click(function(){
      div.hide(1000);
   });
   $("#b6").click(function(){
      div.toggle(1000);
   });
  
});
   
</script>
   
<style>
button{
  display:block;
}
div{
  border:solid 1px gray;
  background-color:pink;
  width:300px;
  height:100px;
}
</style>
 
<button id="b1">立即隐藏</button>
<button id="b2">立即显示</button>
<button id="b3">立即切换</button>
 
<button id="b4">延时显示</button>
<button id="b5">延时隐藏</button>
<button id="b6">延时切换</button>
 
<br>
<br>
   
<div id="d">
用于演示效果的DIV
</div>
```

### 向上滑动 向下滑动 滑动切换

**向上滑动 向下滑动 滑动切换** 分别通过**slideUp()**, **slideDown()**,**slideToggle()**实现
也可以加上毫秒数，表示延时操作，比如**slideUp(2000)**

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
$(function(){
var div = $("#d");
   $("#b1").click(function(){
      div.slideUp();
   });
   $("#b2").click(function(){
      div.slideDown();
   });
   $("#b3").click(function(){
      div.slideToggle();
   });
   $("#b4").click(function(){
      div.slideUp(2000);
   });
   $("#b5").click(function(){
      div.slideDown(2000);
   });
   $("#b6").click(function(){
      div.slideToggle(2000);
   });
   
});
    
</script>
    
<style>
button{
  display:block;
}
div{
  border:solid 1px gray;
  background-color:pink;
  width:300px;
  height:100px;
}
</style>
   
<button id="b1">向上滑动</button>
<button id="b2">向下滑动</button>
<button id="b3">滑动切换</button>
  
<button id="b4">延时向上滑动</button>
<button id="b5">延时向下滑动</button>
<button id="b6">延时滑动切换</button>
  
<br>
<br>
    
<div id="d">
用于演示效果的DIV
</div>
```

## 淡入，淡出

**淡入 淡出 淡入淡出切换 指定淡入程度** 分别通过**fadeIn()**, **fadeOut()**,**fadeToggle()** **fadeTo()**实现
也可以加上毫秒数，表示延时操作，比如**fadeIn(2000)**
fadeTo跟的参数是0-1之间的小数。 0表示不淡入，1表示全部淡入

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
$(function(){
var div = $("#d");
   $("#b1").click(function(){
      div.fadeIn();
   });
   $("#b2").click(function(){
      div.fadeOut();
   });
   $("#b3").click(function(){
      div.fadeToggle();
   });
   $("#b4").click(function(){
      div.fadeIn(2000);
   });
   $("#b5").click(function(){
      div.fadeOut(2000);
   });
   $("#b6").click(function(){
      div.fadeToggle(2000);
   });
 
   $("#b7").click(function(){
      $("#d1").fadeTo("slow",0.2);
      $("#d2").fadeTo("slow",0.5);
      $("#d3").fadeTo("slow",0.8);
   });
   
});
    
</script>
    
<style>
button{
  display:block;
}
table div{
    border:solid px gray;
  background-color:pink;
  width:80px;
  height:50px;
}
div{
  border:solid 1px gray;
  background-color:pink;
  width:300px;
  height:100px;
}
</style>
<button id="b2">淡出</button> 
<button id="b1">淡入</button>
<button id="b3">淡入淡出切换</button>
<button id="b5">延时淡出</button>
<button id="b4">延时淡入</button>
<button id="b6">延时淡入淡出切换</button>
 
<button id="b7">fadeTo</button>
 
<br>
<br>
    
<div id="d">
用于演示效果的DIV
</div>
 
<table>
<tr>
   <td>
      <div id="d1">
       用于演示fadeTo 20%
      </div>
   </td>
   <td>
     <div id="d2">
       用于演示fadeTo 50%
     </div>  
   </td>
 
   <td>
     <div id="d3">
      用于演示fadeTo 80%
     </div>  
   </td>
 
</tr>
 
</table>
```

## 自定义动画效果

通过**animate** 可以实现更为丰富的动画效果
animate()第一个参数为css样式
animate()第二个参数为延时毫秒
**注：** 默认情况下，html中的元素都是固定，并且无法改变的位置的。 为了使用animate()自定义动画效果，需要通过css把元素的**position设置为relative、absolute或者fixed**。

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
$(function(){
var div = $("#d");
   $("#b1").click(function(){
    div.animate({left:'100px'},2000);
    div.animate({left:'0px',top:'50px',height:'50px'},2000);
   });
});
    
</script>
    
<style>
button{
  display:block;
}
 
div{
  background-color:pink;
  width:200px;
  height:80px;
  font-size:12px;
  position:relative;
}
</style>
   
<button id="b1">自定义动画</button>
 
<br>
<br>
    
<div id="d">
<p>1. 向右移动100px</p>
<p>2. 向左下移动50px，同时高度变小</p>
</div>
```

## 回调函数

效果一般需要一定的时间，并且这个时间可长可短，所以就无法精确的确定该效果何时结束。
好在，效果方法都提供对回调函数callback()的支持。
只需要在**调用效果方法的最后一个参数传入一个function**，当效果结束的时候，就会自动调用该function了

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
$(function(){
var div = $("#d");
   $("#b1").click(function(){
    div.animate({left:'100px'},2000);
    div.animate({left:'0px',top:'50px',height:'50px'},2000,function(){
     alert("动画演示结束");
    });
   });
});
    
</script>
    
<style>
button{
  display:block;
}
 
div{
  background-color:pink;
  width:200px;
  height:80px;
  font-size:12px;
  position:relative;
}
</style>
   
<button id="b1">自定义动画结束时，会有提示框</button>
 
<br>
<br>
    
<div id="d">
<p>1. 向右移动100px</p>
<p>2. 向左下移动50px，同时高度变小</p>
</div>
```

## 事件

| 关键字                                                       | 简介     | 示例代码                                                     |
| :----------------------------------------------------------- | :------- | :----------------------------------------------------------- |
| $(document).ready() $() load()                               | 加载     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step991) |
| click() dblclick()                                           | 点击     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step996) |
| keydown() keypress() keyup                                   | 键盘     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step994) |
| mousedown() mouseup() mousemove() mouseenter() mouseleave() mouseover() mouseout() | 鼠标     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step995) |
| focus() blur()                                               | 焦点     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step992) |
| change()                                                     | 改变     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step993) |
| submit()                                                     | 提交     | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step998) |
| on()                                                         | 绑定事件 | [示例代码](https://how2j.cn/k/jquery/jquery-event/473.html#step3006) |
| trigger()                                                    | 触发事件 |                                                              |

### 加载

页面加载有两种方式表示
\1. **$(document).ready()**;
\2. **$();** 这种比较常用
图片加载用**load()**函数

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
  $(document).ready(function(){
    $("#message1").html("页面加载成功");
   
  });
  $(function(){
    $("#img").load(function(){
      $("#message2").html("图片加载成功");
    });
  });
 
</script>
  
<div id="message1"></div>
<div id="message2"></div>
 
<img id="img" src="https://how2j.cn/example.gif">
```

### 点击

**click()** 表示单击
**dblclick()** 表示双击
注: 空白键和回车键也可以造成click事件，但是只有**双击鼠标**才能造成dblclick事件

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
  $(function(){
      $("#b").click(function(){
          $("#message").html("单击按钮");
      });
      $("#b").dblclick(function(){
          $("#message").html("双击按钮");
      });
  });
</script>
   
<div id="message"></div>
 
<button id="b">测试单击和双击</button>
```



### 键盘

```
keydown 表示按下键盘
keypress 表示按住键盘
keyup 表示键盘弹起
这三者的区别分别表现在发生的 先后顺序，获取到的键盘按钮值，已经对输入框的文本取值这三方面
先后顺序： 按照 keydown keypress keyup 顺序发生
键盘按钮值：
通过event对象的which属性获取键盘的值
keydown和keyup 能获取所有按键，不能识别大小写
keypress 不能获取功能键，如F1 SHIFT等，能够识别大小写
文本取值：
keydown和keypress：不能获取最后一个字符
keyup： 获取所有字符
如图所例，敲入ab
发生的先后顺序是 keydown,keypress,keyup
keydown和keyup取到大写B的ASCII码表 66,keypress取到小写b的ASCII码表 98.
keydown和keypress只能取到文本值a, keyup可以取到ab
```

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
var order = 0;
var clearTimer=null;
$(function(){
  $("#i").keydown(function(e){
     var selector = "keydown";
  
     show(selector,e,$(this).val());
  });
  
  $("#i").keypress(function(e){
     var selector = "keypress";
     show(selector,e,$(this).val());
  });
  
  $("#i").keyup(function(e){
     var selector = "keyup";
     show(selector,e,$(this).val());
  });
    
});
  
function show(selector,e,inputvalue){
     clearTimeout(clearTimer);
     action(selector);
     key(selector,e);
     value(selector,inputvalue);
     clearTimer= setTimeout(clear,4000);
}
  
function action(selector){
    $("#"+selector+"Action").css("background-color","green");
    $("#"+selector+"Action").html("顺序: " + (++order ) );
}
  
function value(selector,value){
    $("#"+selector+"Value").html(value);
}
  
function key(selector,e){
    $("#"+selector+"Key").html(e.which);
}
 
function clear(){
  order = 0;
  $("tr#action div").css("background-color","red");
  $("tr div").html("");
}
  
</script>
<style>
tr#action div{
  border: 1px solid black;
  height:50px;
  background-color:red;
}
 
tr#value div,tr#key div{
  
  height:50px;
  background-color:#d1d1d1;
}
  
td{
 width:25%;
}
</style>
输入框：<input id="i">
<table width="100%">
<tr>
  <td></td>
  <td>keydown</td>
  <td>keypress</td>
  <td>keyup</td>
</tr>
<tr id="action">
  <td>行为</td>
  <td><div id="keydownAction"></div></td>
  <td><div id="keypressAction"></div></td>
  <td><div id="keyupAction"></div></td>
</tr>
  
<tr id="key">
  <td>按键</td>
  <td><div id="keydownKey"></div></td>
  <td><div id="keypressKey"></div></td>
  <td><div id="keyupKey"></div></td>
</tr>
  
<tr id="value">
  <td>取值</td>
  <td><div id="keydownValue"></div></td>
  <td><div id="keypressValue"></div></td>
  <td><div id="keyupValue"></div></td>
</tr>
  
</table>
```

### 鼠标

**mousedown** 表示鼠标按下
**mouseup**表示鼠标弹起


**mousemove**表示鼠标进入
**mouseenter**表示鼠标进入
**mouseover**表示鼠标进入


**mouseleave**表示鼠标离开
**mouseout**表示鼠标离开




进入事件有3个 mousemove mouseenter mouseover
**mousemove** ：当鼠标进入元素，**每移动一下**都会被调用
**mouseenter** ：当鼠标进入元素，调用一下，**在其中移动，不调用**
**mouseover**：当鼠标进入元素，调用一下，**在其中移动，不调用**


mouseenter 和 mouseover的区别
**mouseenter**: 当鼠标经过其子元素**不会**被调用
**mouseover**：当鼠标经过其子元素**会**被调用

mouseleave 和 mouseout的区别
**mouseleave**: 当鼠标经过其子元素**不会**被调用
**mouseout**：当鼠标经过其子元素**会**被调用

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
$(function(){
$("#downup").mousedown(function(){
   $(this).html("鼠标按下");
});
$("#downup").mouseup(function(){
   $(this).html("鼠标弹起");
});
var moveNumber  =0;
var enterNumber  =0;
var leaveNumber  =0;
var overNumber  =0;
var outNumber  =0;
 
var enterNumber1  =0;
var overNumber1  =0;
 
var leaveNumber1  =0;
var outNumber1  =0;
 
$("#move").mousemove(function(){
  $("#move span.number" ).html(++moveNumber);
});
$("#enter").mouseenter(function(){
  $("#enter span.number" ).html(++enterNumber);
});
$("#leave").mouseleave(function(){
  $("#leave span.number" ).html(++leaveNumber);
});
$("#over").mouseover(function(){
  $("#over span.number" ).html(++overNumber);
});
$("#out").mouseout(function(){
  $("#out span.number" ).html(++outNumber);
});
 
$("#enter1").mouseenter(function(){
  $("#enter1 span.number" ).html(++enterNumber1);
});
$("#over1").mouseover(function(){
  $("#over1 span.number" ).html(++overNumber1);
});
 
$("#leave1").mouseleave(function(){
  $("#leave1 span.number" ).html(++leaveNumber1);
});
 
$("#out1").mouseout(function(){
  $("#out1 span.number" ).html(++outNumber1);
});
 
});
 
</script> 
 
<style>
div{
  background-color:pink;
  margin:20px;
  padding:10px;
}
 
.subDiv{
  background-color:green;
  margin:10px;
}
 
.parentDiv{
  background-color:pink;
  height:80px;
}
 
table{
 width:100%;
 border-collapse:collapse;
  table-layout:fixed;
}
td{
  border: 1.5px solid #d1d1d1;
  vertical-align:top;
  padding:20 0;
}
 
</style>
<table >
  <tr>
    <td width="100px">事件</td>
    <td>效果演示</td>
  </tr>
  <tr>
    <td>mousedown <br />
    mouseup<br /></td>
    <td>
      <button id="downup" style="margin-left:20px">鼠标按下弹起测试</button>    </td>
  </tr>
  <tr>
    <td>mousemove<br />
      mouseenter<br />
      mouseover<br />
      mouseleave<br />
    mouseout</td>
    <td>
        <div id="move">mousemove 当鼠标进入元素，每移动一下都会被调用 次数<span class="number">0</span></div>
        <div id="enter">mouseenter 当鼠标进入元素，调用一下，在其中移动，不调用 次数<span class="number">0</span></div>
        <div id="over">mouseover 当鼠标进入元素，调用一下，在其中移动，不调用 次数<span class="number">0</span></div>
        <div id="leave">mouseleave 当鼠标离开元素，调用一下 次数<span class="number">0</span></div>
  <div id="out">mouseout 当鼠标离开元素，调用一下 <span class="number">0</span></div>  </tr>
  <tr>
    <td>mouseenter<br />
    mouseover</td>
    <td>
     
    <div id="enter1" class="parentDiv">
    mouseenter 经过其子元素不会被调用 次数<span class="number">0</span>
     
       <div class="subDiv">div中的子元素      </div>
    </div>
     
        <div id="over1" class="parentDiv">
    mouseover  经过其子元素会被调用 次数<span class="number">0</span>
     
       <div class="subDiv">div中的子元素      </div>
    </div>    </td>
  </tr>
  <tr>
    <td>mouseleave<br />
      mouseout    </td>
    <td>
    <div id="leave1" class="parentDiv">
    mouseleave 经过其子元素不会被调用 次数<span class="number">0</span>
     
       <div class="subDiv">div中的子元素      </div>
    </div>
     
    <div id="out1" class="parentDiv">
 
    mouseout 经过其子元素会被调用 次数<span class="number">0</span>
     
       <div class="subDiv">div中的子元素      </div>
    </div>    </td>
  </tr>
</table>
```

### 焦点

**focus()** 获取焦点
**blur()** 失去焦点

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
$(function(){
 $("input").focus(function(){
    $(this).val("获取了焦点");
 });
  
  $("input").blur(function(){
    $(this).val("失去了焦点");
 });
 
});
 
</script> 
 
<style>
 
</style>
 
<input type="text" >
 
<input type="text" >
```



### 改变

**change()** 内容改变
**注：** 对于文本框，只有当该文本**失去焦点**的时候，才会触发change事件。

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
$(function(){
 $("#input1").change(function(){
    var text = $(this).val();
    $("#message").html("input1的内容变为了"+text);
 });
  
});
 
</script> 
 
<style>
 
</style>
 
<div id="message"></div>
 
<input id="input1" type="text" >
<br>
<input size="50" id="input2"type="text" value="只有当input1失去焦点的时候，才会触发change事件" >
```

###  提交

**submit()** 提交form表单

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<form id="form" action="https://how2j.cn/study/login.jsp">
账号 : <input name="name" type=""> <br>
密码: <input name="password" type=""><br>
<input type="submit" value="登陆">
  
</form>
   
<script>
$(function(){
 
   $("#form").submit(function(){
      alert("提交账号密码");
   });
});
  
</script>
```

### 绑定事件

以上所有的事件处理，都可以通过on() 绑定事件来处理

` $("selector").on("event",function);`

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
  $(function(){
      $("#b").on("click",function(){
          $("#message").html("单击按钮");
      });
      $("#b").on("dblclick",function(){
          $("#message").html("双击按钮");
      });
 
  });
</script>
    
<div id="message"></div>
  
<button id="b">测试单击和双击</button>
```

### 触发事件

触发事件，在本例中，文档加载好之后，就触发dblclick双击事件，而不是通过去手动双击。

`$("selector").trigger("event");`

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
  $(function(){
      $("#b").on("click",function(){
          $("#message").html("单击按钮");
      });
      $("#b").on("dblclick",function(){
          $("#message").html("双击按钮");
      });
     $("#b").trigger("dblclick");
  });
</script>
    
<div id="message"></div>
  
<button id="b">测试单击和双击</button>
```



## AJAX

| 关键字      | 简介                   | 示例代码                                                     |
| :---------- | :--------------------- | :----------------------------------------------------------- |
| $.ajax()    | 提交AJAX请求           | [示例代码](https://how2j.cn/k/jquery/jquery-ajax/474.html#step1002) |
| $.get()     | 使用get方式提交ajax    | [示例代码](https://how2j.cn/k/jquery/jquery-ajax/474.html#step999) |
| $.post      | 使用post方式提交ajax   | [示例代码](https://how2j.cn/k/jquery/jquery-ajax/474.html#step1000) |
| serialize() | 格式化form下的输入数据 |                                                              |
| load()      | 最简单的调用ajax的方式 | [示例代码](https://how2j.cn/k/jquery/jquery-ajax/474.html#step1001) |

### 提交请求

 $.ajax({

   url: page,

   data:{"name":value},

   success: function(result){

​      $("#checkResult").html(result);

   }

});

$.ajax采用参数集的方式 {param1,param2,param3} 不同的参数之间用,隔开
第一个参数 **url**:page 表示访问的是page页面
第二个参数 **data**:{name:value} 表示提交的参数
第三个参数 **success**: function(){} 表示服务器成功返回后对应的响应函数

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<div id="checkResult"></div>
  
输入账号 :<input id="name" type="text">
  
<script>
$(function(){
   $("#name").keyup(function(){
     var page = "/study/checkName.jsp";
     var value = $(this).val();
        $.ajax({
            url: page,
            data:{"name":value},
            success: function(result){
              $("#checkResult").html(result);
            }
        });
   });
});
 
</script>
```

### 使用get方式提交ajax

```
$.get(
            page,
            {"name":value},
            function(result){
              $("#checkResult").html(result);
            }
);
```

$.get 使用3个参数
第一个参数: page 访问的页面
第二个参数: {name:value} 提交的数据
第三个参数: function(){} 响应函数
只有**第一个**参数是**必须的**，其他参数都是可选

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<div id="checkResult"></div>
  
输入账号 :<input id="name" type="text">
  
<script>
$(function(){
   $("#name").keyup(function(){
     var page = "/study/checkName.jsp";
     var value = $(this).val();
 
        $.get(
            page,
            {"name":value},
            function(result){
              $("#checkResult").html(result);
            }
        );
   });
});
 
</script>
```

### 使用post方式提交ajax

```
$.post(
    page,
    {"name":value},
    function(result){
        $("#checkResult").html(result);
    }
);
```

$.post 使用3个参数
第一个参数: page 访问的页面
第二个参数: {name:value} 提交的数据
第三个参数: function(){} 响应函数
只有**第一个**参数是**必须的**，其他参数都是可选

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<div id="checkResult"></div>
   
输入账号 :<input id="name" type="text">
   
<script>
$(function(){
   $("#name").keyup(function(){
     var page = "/study/checkName.jsp";
     var value = $(this).val();
  
        $.post(
            page,
            {"name":value},
            function(result){
              $("#checkResult").html(result);
            }
        );
   });
});
  
</script>
```

### 最简单的调用ajax的方式

load比起 [$.get](https://how2j.cn/k/jquery/jquery-ajax/474.html#step1000),[$.post](https://how2j.cn/k/jquery/jquery-ajax/474.html#step999) 就更简单了
$("#id").load(page,[data]);
**id**: 用于显示AJAX服务端文本的元素Id
**page**: 服务端页面
**data**: 提交的数据，可选。 在本例中，直接在page里加上了参数列表

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<div id="checkResult"></div>
    
输入账号 :<input id="name" type="text">
    
<script>
$(function(){
   $("#name").keyup(function(){
     var value = $(this).val();
     var page = "/study/checkName.jsp?name="+value;
     $("#checkResult").load(page);
   });
});
   
</script>
```

### 格式化form下的输入数据

**serialize()：** 格式化form下的输入数据
有的时候form下的输入内容比较多，一个一个的取比较麻烦，就可以使用serialize() 把输入数据格式化成字符串

```javascript
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<div id="checkResult"></div>
<div id="data"></div>
<a href="https://how2j.cn/study/checkName.jsp">https://how2j.cn/study/checkName.jsp</a>
 
<form id="form">   
输入账号 :<input id="name" type="text" name="name"> <br>
输入年龄 :<input id="age" type="text" name="age"> <br>
输入手机号码 :<input id="mobile" type="text" name="mobile"> <br>
     
</form>
 
<script>
$(function(){
   $("input").keyup(function(){
      var data = $("#form").serialize();
      var url = "https://how2j.cn/study/checkName.jsp";
      var link = url+"?"+ data;
      $("a").html(link);
      $("a").attr("href",link);
   });
});
    
</script>
```

## 数组操作

| 关键字      | 简介              | 示例代码                                                     |
| :---------- | :---------------- | :----------------------------------------------------------- |
| $.each()    | 遍历              | [示例代码](https://how2j.cn/k/jquery/jquery-array/475.html#step1003) |
| $.unique()  | 去除重复          | [示例代码](https://how2j.cn/k/jquery/jquery-array/475.html#step1004) |
| $.inArray() | 是否存在$.inArray |                                                              |

### 遍历

**$.each** 遍历一个数组
第一个参数是数组
第二个参数是回调函数 i是下标，n是内容

```js
<script src="https://how2j.cn/study/jquery.min.js"></script>
 
<script>
var a = new Array(1,2,3);
$.each( a, function(i, n){
  document.write( "元素[" + i + "] : " + n + "<br>" );
})
document.close();
 
</script> 
```

### 去除重复

**$.unique()** 去掉重复的元素

注意 ： 执行unique之前，要先[调用sort对数组的内容进行排序](https://how2j.cn/k/javascript/javascript-array/441.html#step1137)。

```js
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
var a = new Array(5,2,4,2,3,3,1,4,2,5);
a.sort();
$.unique(a);
$.each( a, function(i, n){
  document.write( "元素[" + i + "] : " + n + "<br>" );
})
document.close();
  
</script> 
```

### 是否存在$.inArray

**$.inArray** 返回元素在数组中的位置 ，如果不存在返回-1

```js
<script src="https://how2j.cn/study/jquery.min.js"></script>
  
<script>
var a = new Array(1,2,3,4,5,6,7,8);
document.write($.inArray(9,a));
document.close();
  
</script> 
```

## 字符串

**$.trim()** 去除首尾空白

```js
<script src="https://how2j.cn/study/jquery.min.js"></script>
   
<script>
 
document.write($.trim(" Hello JQuery    "));
document.close();
   
</script> 
```

## JSON

**$.parseJSON** 将JSON格式的字符串，转换为JSON对象

```js
<script src="https://how2j.cn/study/jquery.min.js"></script>
    
<script>
  
var s1 = "{\"name\":\"盖伦\"";
var s2 = ",\"hp\":616}";
var s3 = s1+s2;
  
document.write("这是一个JSON格式的字符串:" + s3);
document.write("<br>");
var gareen = $.parseJSON(s3);
  
document.write("这是一个JSON对象: " + gareen);
   
</script>
```


