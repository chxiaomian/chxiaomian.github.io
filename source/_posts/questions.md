---
title:  最近开发中遇到的问�
date:  2017-12-27 22:53:55
tags: 
    - BootStrap
    - jQuery
---

### 1.BootStrap模态框回车刷新的问�

最近开发一个需�需要在BootStrap的模态框中实现回车键查询功能,每次按下回车键的时�页面就会刷新,点击查询按钮则没有问�
Google了一下发现很多人遇到了这个问�

[How to avoid refreshing the page in a bootstrap modal?](https://stackoverflow.com/questions/14938290/how-to-avoid-refreshing-the-page-in-a-bootstrap-modal)

[Keep a Modal Window open after form submission.](https://teamtreehouse.com/community/keep-a-modal-window-open-after-form-submission)

也有人在Github提了Issue:

[Modal closes on `Enter` key press when there's a form](https://github.com/react-bootstrap/react-bootstrap/issues/1128)




问题的原因可能是: form表单提交的默认行为导致的. 按下Enter�form表单可能会被提交.具体的原因暂时还没有时间研究.以后有时间再研究.

[Press Enter to Submit 背后的那些事](http://david-chen-blog.logdown.com/posts/177766-how-forms-submit-when-pressing-enter)

提出的解决方案有以下几种:

- 把输入控件`type='submit'`改成其他的类�

```html
<button class="btn" id="signin_button">Sign in</button>
```

- 阻止表单提交的默认行�

```javascript
$( "form" ).submit(function( event ) {
    event.preventDefault();
});
```

我使用第二种方案解决了这个问�




