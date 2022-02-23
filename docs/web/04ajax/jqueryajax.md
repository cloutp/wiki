---
title: jQueryAjax
date: 2022-01-21 14:13:50
tags:
 - AJAX
 - web
categories:
 - web
 - AJAX
---

## jQueryAjax

### 发送Ajax请求

```js
 $.ajax({
     type: 'get',
     url: 'http://www.example.com',
     data: { name: 'zhangsan', age: '20' },
     contentType: 'application/x-www-form-urlencoded',
     // 在请求发送之前调用
     beforeSend: function () {
        alert('请求不会被发送')
        // 请求不会被发送
        return false;
     },
     success: function (response) {},
     error: function (xhr) {}
});
```

```js
 $.ajax({
     type: 'get',
     url: 'http://www.example.com',
     data: JSON.stringify({name: 'zhangsan', age: '20'}),
     contentType: 'application/json',
     beforeSend: function () { 
         return false
     },
     success: function (response) {},
     error: function (xhr) {}
});
```

### 发送jsonp请求

```js
$.ajax({
    url: 'http://www.example.com',
    // 指定当前发送jsonp请求
    dataType: 'jsonp',
    // 修改callback参数名称
    jsonp: 'cb',
    // 指定函数名称
    jsonCallback: 'fnName',
    success: function (response) {} 
})
```

### serialize方法

> 将表单中的数据自动拼接成字符串类型的参数

```js
var params = $('#form').serialize();
// name=zhangsan&age=30
```

### $.get()、$.post()方法概述

> $.get方法用于发送get请求，$.post方法用于发送post请求

```js
$.get('http://www.example.com', {name: 'zhangsan', age: 30}, function (response) {}) $.post('http://www.example.com', {name: 'lisi', age: 22}, function (response) {})
```

### 全局事件

> 只要页面中有Ajax请求被发送，对应的全局事件就会被触发

```js
.ajaxStart()     // 当请求开始发送时触发
.ajaxComplete()  // 当请求完成时触发
```

### NProgress

> 官宣：纳米级进度条，使用逼真的涓流动画来告诉用户正在发生的事情！

```html
<link rel='stylesheet' href='nprogress.css'/>
<script src='nprogress.js'></script>
```

```js
NProgress.start();  // 进度条开始运动 
NProgress.done();   // 进度条结束运动
```

