---
title: JavaScript 类型判断
---

## 数据类型
在 ECMAScript  规范中，共定义了 7 种数据类型，分为 基本类型 和 引用类型 两大类，如下所示：

基本类型：`String、Number、Boolean、Symbol、Undefined、Null` 
引用类型：`Object`

`Symbol`  是在ES6中引入的一种新的原始数据类型，表示独一无二的值。

## 常见的几种判断JavaScript类型的方式

### 1. `typeof`
`typeof` 是一个操作符，其右侧跟一个一元表达式，并返回这个表达式的数据类型。返回的结果用该类型的字符串(全小写字母)形式表示
`typeof`只有两个用途，就是检测一个元素是否为`undefined`，或者是否为`function`。
```javascript
typeof ''; // string 有效
typeof 1; // number 有效
typeof Symbol(); // symbol 有效
typeof true; //boolean 有效
typeof undefined; //undefined 有效
typeof null; //object 无效
typeof [] ; //object 无效
typeof new Function(); // function 有效
typeof new Date(); //object 无效
typeof new RegExp(); //object 无效
```


_`typeof` 存在的问题_


### 2. `instanceof`
instanceof 是用来判断 A 是否为 B 的实例，表达式为：A instanceof B，如果 A 是 B 的实例，则返回 true,否则返回 false

instanceof 检测的是原型

### 3. `constructor`

当一个函数 F被定义时，JS引擎会为F添加 prototype 原型，然后再在 prototype上添加一个 constructor 属性，并让其指向 F 的引用

当执行 var f = new F() 时，F 被当成了构造函数，f 是F的实例对象，此时 F 原型上的 constructor 传递到了 f 上，因此 f.constructor == F


### 4. `Object.prototype.toString()`
`toString()` 是 `Object` 的原型方法，调用该方法，默认返回当前对象的 [[Class]]

它会返回正确的类型。我们需要做的就是**手动处理其返回的字符串**，最终便能获得typeof应该返回的正确字符串。

可以用来区分：`Boolean, Number, String, Function, Array, Date, RegExp, Object, Error`等等。


```javascript
Object.prototype.toString.call('') ;   // [object String]
Object.prototype.toString.call(1) ;    // [object Number]
Object.prototype.toString.call(true) ; // [object Boolean]
Object.prototype.toString.call(Symbol()); //[object Symbol]
Object.prototype.toString.call(undefined) ; // [object Undefined]
Object.prototype.toString.call(null) ; // [object Null]
Object.prototype.toString.call(new Function()) ; // [object Function]
Object.prototype.toString.call(new Date()) ; // [object Date]
Object.prototype.toString.call([]) ; // [object Array]
Object.prototype.toString.call(new RegExp()) ; // [object RegExp]
Object.prototype.toString.call(new Error()) ; // [object Error]
Object.prototype.toString.call(document) ; // [object HTMLDocument]
Object.prototype.toString.call(window) ; //[object global] window是全局对象 global 的引用
```

