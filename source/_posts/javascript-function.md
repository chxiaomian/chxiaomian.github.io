---
title: JavaScript Function
date: 2017-12-22 14:32:20
tags:
    - JavaScript
    - Function
---



JavaScript中,通常情况下,我们都把代码卸载函数里面,我们大部分代码执行都是函数调用的结果,为了更好的理解Function,我们需要了解javascript对象的一些特性.
javascript对象有以下一些特性:

- 可以使用字面量创建
- 可以赋值给变量/数组/其他对象的属性
- 可以作为函数的参数传递
- 有属性
- 可以作为返回值返回

JavaScript函数拥有JavaScript对象的所有特性,而且还可以被调用.那就可以这么说,JavaScript函数就是对象.

函数同样拥有上面的特性:

- 字面量创建

```javascript
function myFunc() { };
```

- 赋值给变量/数组/和属性

```javascript
var myFunc = function() { };     //赋值给变量

myArray.push(function() { });    //添加到数组中

myObj.myFunc = function() { };   //赋值给对象的属性

```

- 作为参数传递

```javascript
function myFunc(someFunc) {
    someFunc();
}
myFunc(function() { });
```

- 拥有属性

```javascript
var myFunc = function() { };
myFunc.someProperty = "Property";

```

- 作为参数返回

```javascript
function myFunc(){
     return function() { };
}
```


## 定义JavaScript函数

JavaScript中 Function 可以通过多种方式去定义:

#### 函数声明和函数表达式

JavaScript定义函数最常用的两种方式就是通过**函数声明**和**函数表达式**
函数声明是`function` 关键字后面跟着函数名和参数的括号以及大括号.

```javascript
function myFunc() {
     return "Function Declaration";
}
```
另外一种方式,**函数表达式**就像编写任何JavaScript表达式一样,只有`function`关键字/参数和函数体,如下

```javascript
var myFunc = function() { return "Function Expression"; };
```

#### 立即执行函数

立即执行函数,就是在定义函数的写入表达式以后被立即执行,可以应用在JavaScript的模块开发中.

```javascript
var sum = (function (param1, param2) { return param1 + param2;  })(2,3);
```

#### 箭头函数

箭头函数是在ES6中添加的新特性,可以看做是通过语法糖的形式对函数表达式进行的简化,箭头函数使用`=>`符号定义:

```javascript
var var1 = name => "Hi " + name;   //定义箭头函数
var var2 = var1("George");
```

如果箭头函数没有参数的话,还可以这样定义:

```javascript
var myFunc = () => alert('Arrow Function 调用');
```