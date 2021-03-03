# React学习笔记



## JSX的介绍及使用

JSX简洁来说就是在JS中写HTML

    const element = <h1> hello world<h1>

* 在JSX中嵌入表达式

      const name = 'Yang'
      const element  = <h1> Hello,{name}<h1>
      ReactDOM.render(
      element,
      document.getElementById('root)
      )

我们可以嵌入任何js表达式在{}内，比如说：1+1，user.firstname,formatName(user)

* JSX同样也是一种表达式

在编译之后，JSX 表达式会被转为普通 JavaScript 函数调用，并且对其取值后得到 JavaScript 对象。

简单来说，你可以在JSX内部用‘if’或者‘for’，也可以从function返回JSX

    function getGreeting(){
    	if(user){
        	return <h1>Hello, {formatName(user)}<h1>
        }
        return <h1>Hello, Srtanger<h1>
    }

* JSX特定属性

You  use quote to specify string literals as attribute

    const element = <div tabIndex="0"></div>;

You may also use curly braces to embed a js in an attribute.

    const element = <img src={user.avatarUrl}></img>;

* 使用JSX指定子元素

    const element = <img src={user.avatarUrl} />;

JSX 标签里能够包含很多子元素:
