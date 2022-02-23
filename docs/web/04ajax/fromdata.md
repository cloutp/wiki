---
title: FromData对象
date: 2022-01-23 15:33:50
tags:
 - AJAX
 - web
categories:
 - web
 - AJAX
---

## FromData对象

> 模拟HTML表单，相当于将HTML表单映射成表单对象，自动将表单对象中的数据拼接成请求参数的格式。

> 异步上传二进制文件

### 使用

1. .  准备 HTML 表单

   ```html
    <form id="form">
        <input type="text" name="username" />
        <input type="password" name="password" />
        <input type="button"/>
   </form>
   ```

2. 将 HTML 表单转化为 formData 对象

   ```js
   var form = document.getElementById('form'); 
   var formData = new FormData(form);
   ```

3. 提交表单对象

   ```js
   xhr.send(formData);
   ```

**注意：**

1. Formdata 对象不能用于 get 请求，因为对象需要被传递到 send 方法中，而 get 请求方式的请求参数只能放在请求地址的后面。

2. 服务器端 bodyParser 模块不能解析 formData 对象表单数据，我们需要使用 formidable 模块进行解析。



### FormData 对象的实例方法

1. 获取表单对象中属性的值`formData.get('key');` 
2. 设置表单对象中属性的值`formData.set('key', 'value');` 
3. 删除表单对象中属性的值` formData.delete('key');`
4. 向表单对象中追加属性值`formData.append('key', 'value');`

注意：set 方法与 append 方法的区别是，在属性名已存在的情况下，set 会覆盖已有键名的值，append会保留两个值。

### FormData 二进制文件上传

```html
<input type="file" id="file"/>
```

```js
 var file = document.getElementById('file')
// 当用户选择文件的时候
 file.onchange = function () {
     // 创建空表单对象
     var formData = new FormData();
     // 将用户选择的二进制文件追加到表单对象中
     formData.append('attrName', this.files[0]);
     // 配置ajax对象，请求方式必须为post
     xhr.open('post', 'www.example.com');
     xhr.send(formData);
 }
```

**显示上传进度**

```js
 // 当用户选择文件的时候
 file.onchange = function () {
     // 文件上传过程中持续触发onprogress事件
     xhr.upload.onprogress = function (ev) {
         // 当前上传文件大小/文件总大小 再将结果转换为百分数
         // 将结果赋值给进度条的宽度属性 
         bar.style.width = (ev.loaded / ev.total) * 100 + '%';
     }
 }
```

**上传图片即时预览**

```js
 xhr.onload = function () {
     var result = JSON.parse(xhr.responseText);
     var img = document.createElement('img');
     img.src = result.src;
     img.onload = function () {
         document.body.appendChild(this);
     }
 }
```

