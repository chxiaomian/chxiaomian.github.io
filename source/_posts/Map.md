---
title: Map - JavaScript 键值对
date: 2017-12-24 18:41:45
tags:
    - JavaScript
    - Map
    - Key-Value Pair
---

## 键值对

有没有遇到过在JavaScript中使用键值对的场景,键值对在C# Java 语言中是非常主流的概念,但是在JavaScript中,开发人员却面临一个挑战,大多数情况下,要使用自定义类型来解决这个问题.`Map`就是为了到达相同目的而设计的.

直接看代码,创建一个`Map`对象并且在示例中使用它.

```javascript
var myMap = new Map();  
var key1 = "key1",key2="key2",key3="key3";  
myMap.set(key1, "value for key1");  
myMap.set(key2, 'value for key2');  
myMap.set(key3, 'value for key3');  
console.log(myMap.get(key1));  
console.log(myMap.get(key2));  
console.log(myMap.get(key3));  
```

第一步,创建了`Map`对象,然后创建三个变量,然后给`Map`对象设置键值.

设置键值的语法
```javascript
object.set(<key>, <value>);  
```
正如示例中一样,给`Map`对象设置键值,然后输出键对应的值.

取值的语法
```javascript
object.get(<key>) ;  
```

上面的示例输出的结果是:

```
value for key1
value for key2
value for key3
```
通过移除`Map`中所有的键值对来清空`Map`对象,清空的语法:

```javascript
myMap.clear();  
```
通过`object.clear()`将清空`Map`中所有的值.
如果再次执行以下代码:

```javascript
console.log(myMap.get(key1));  
console.log(myMap.get(key2));  
console.log(myMap.get(key3));  
```
输出的结果将会是:

```
undefined
undefined
undefined
```

那么如何从`Map`中删除特定的键呢.
我们先初始化`Map`,然后删除`key2`
```javascript
myMap.set(key1, "value for key1");  
myMap.set(key2, 'value for key2');  
myMap.set(key3, 'value for key3'); 

myMap.delete(key2);
```

从`Map`中获取所有的键
```javascript
var mapIter = myMap.keys();  
```


最后,我们可以打印出`Map`中所有的键值.

```javascript
for (var [key, value] of myMap) {  
   console.log(key + ' = ' + value);  
}  
```
`Map`可以使用`for...of`循环

输出的结果:

```
key1 = value for with key1
key3 = value for with key3
```