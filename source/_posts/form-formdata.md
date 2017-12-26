---
title: Form 表单  Formdata
date: 2017-12-21 21:40:09
tags:
    - JavaScript
    - Form
---

## Form表单

```html
<form> 标签用于为用户输入创建 HTML 表单。

< form>
...
< /form >
里面包含的数据将被提交到服务器.

可以使用表单来上传文件。
```
### 三个部分

**表单标签**：定义表单要提交到的服务器的地址和提交的http方法。

**表单域**：包含了文本框、密码框、隐藏域、多行文本框、复选框、单选框、下拉选择框和文件上传框等。

**表单按钮**：包括提交按钮、复位按钮和一般按钮；用于将数据传送到服务器上或者取消输入，还可以用表单按钮来控制其他定义了处理脚本的处理工作。


### 成功控件
浏览器并不是将所有的表单控件全部发送到服务器的，而是会查找所有的【成功控件】，只将这些成功控件的数据发送到服务端

成功控件就是：每个表单中的控件都应该有一个**name属性**和”当前值“  **value属性**， 在提交时，它们将以 name=value 的形式做为提交数据的一部分。

成功控件有以下规定：
1. 控件不能是【禁用】状态，即指定【disabled="disabled"】。即：禁用的控件将不是成功控件。
2. 如果一个表单包含了多个提交按键，那么仅当用户点击的那个提交按钮才算是成功控件。
3. 对于checkbox控件来说，只有被用户勾选的才算是成功控件。
4. 对于radio button来说，只有被用户勾选的才算是成功控件。
5. 对于select控件来说，所有被选择的选项都做为成功控件，name由select控件提供。
6. 对于file上传文件控件来说，如果它包含了选择的文件，那么它将是一个成功控件。


#### 需要注意的几点：

提交方式：
如果是【post】，那么表单数据将放在请求体中被发送出去。
如果是【get】，那么表单数据将会追加到查询字符串中，以查询字符串的形式提交到服务端。
建议：表单通常还是以post方式提交比较好，这样可以不破坏URL，况且URL还有长度限制。


### 浏览器处理过程

浏览是如何处理表单数据的。这个过程大致分为4个阶段：
1. 识别所有的成功控件。
2. 为所有的成功控件创建一个数据集合，它们包含 control-name/current-value 这样的值对。
3. 按照form.enctype指定的编码规则对前面准备好的数据进行编码。编码规则将放在请求中，用【Content-Type】指出。
4. 提交编码后的数据。此时会区分post,get二种情况，提交的地址由form.action属性指定的。


## Formdata


`FormData`是XMLHttpRequest Level 2新添加的一个接口,使用`FormData`对象可以把Form表单中所有符合条件的表单元素的name与value的执组成一个queryString提交到后台.`FormData`可以减少queryString的拼接.

`FormData`可以让我们很方便的组织一个键值对的集合.其实就是表单元素的序列化.主要的作用就是用来发送表单数据.但是可以独立于表单传输的数据.

`FormData`最大的优势就是可以上传二进制文件. 创建新FormData对象,然后把表单元素作为参数传入,就能得到Form表单的FormData对象.


```html
<form id="uploadForm" enctype="multipart/form-data">
    <input id="file" type="file" name="file"/>
    <button id="upload" type="button">upload</button>
</form>
```

```javascript
$.ajax({
    url: '/upload',
    type: 'POST',
    cache: false,
    data: new FormData($('#uploadForm')[0]),
    processData: false,
    contentType: false
})
.done(function(res) {})
.fail(function(res) {});
```


## Reference

1. http://www.cnblogs.com/fish-li/archive/2011/07/17/2108884.html
2. http://blog.csdn.net/ajianyingxiaoqinghan/article/details/77678772

3. https://developer.mozilla.org/zh-CN/docs/Web/API/FormData
4. https://developer.mozilla.org/zh-CN/docs/Web/API/FormData/Using_FormData_Objects

