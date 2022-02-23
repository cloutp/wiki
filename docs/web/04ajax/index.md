---
title: AJAX
date: 2022-01-23 11:33:50
tags:
 - AJAX
 - web
categories:
 - web
 - AJAX
---

# AJAX

> Ajax：标准读音 [ˈeɪˌdʒæks] ，中文音译：阿贾克斯

> 实现页面无刷新更新数据，提高用户浏览网站应用的体验。

> Ajax 技术需要运行在网站环境中才能生效，后续会使用Node创建的服务器作为网站服务器。

### 应用场景

1. 页面上拉加载更多数据

2. 列表数据无刷新分页

3. 表单项离开焦点数据验证

4. 搜索框提示文字下拉列表

### Ajax运行原理

> Ajax 相当于浏览器发送请求与接收响应的代理人，以实现在不影响用户浏览页面的情况下，局部更新页面数据，从而提高用户体验。

![image-20220128121532972](https://raw.githubusercontent.com/cloutp/blog_img/main/202201281215546.png)



### 使用

1. 创建 Ajax 对象

   ```js
    var xhr = new XMLHttpRequest();
   ```

2. 告诉 Ajax 请求地址以及请求方式

   ```js
   xhr.open('get', 'http://www.example.com');	
   // 异步
   xhr.open('get', 'http://localhost:3000/first', false);
   ```

3. 发送请求

   ```js
    xhr.send();
   ```

4. 获取服务器端给与客户端的响应数据

   ```js
    xhr.onload = function () {
       // console.log(typeof xhr.responseText)
       // 将JSON字符串转换为JSON对象
       var responseText = JSON.parse(xhr.responseText);
       // 测试：在控制台输出处理结果
       console.log(responseText)
       // 将数据和html字符串进行拼接
       var str = '<h2>'+ responseText.name +'</h2>';
       // 将拼接的结果追加到页面中
       document.body.innerHTML = str;
    }
   ```

### 服务器端响应的数据格式

> 在真实的项目中，服务器端大多数情况下会以 JSON 对象作为响应数据的格式。当客户端拿到响应数据时，要将 JSON 数据和 HTML 字符串进行拼接，然后将拼接的结果展示在页面中。

> 在 http 请求与响应的过程中，无论是请求参数还是响应内容，如果是对象类型，最终都会被转换为对象字符串进行传输

```js
 JSON.parse() // 将 json 字符串转换为json对象
```

### 请求参数传递

1. GET 请求方式

   ```js
   xhr.open('get', 'http://www?name=zhangsan&age=20');
   xhr.send();
   ```

2. POST 请求方式

   ```js
   xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded') xhr.send('name=zhangsan&age=20');
   // or
   xhr.setRequestHeader('Content-Type', 'application/json');
   xhr.send(JSON.stringify({name: 'lisi', age:50}));
   ```

   请求参数的格式

   1. application/x-www-form-urlencoded

      ` name=zhangsan&age=20&sex=男` 

   2. application/json

      > 在请求头中指定 Content-Type 属性的值是 application/json，告诉服务器端当前请求参数的格式是 json	

      ```js
       JSON.stringify() // 将json对象转换为json字符串
      ```

      > get 请求是不能提交 json 对象数据格式的，传统网站的表单提交也是不支持 json 对象数据格式的。



### Ajax状态码

> 在创建ajax对象，配置ajax对象，发送请求，以及接收完服务器端响应数据，这个过程中的每一个步骤都会对应一个数值，这个数值就是ajax状态码。

0：请求未初始化(还没有调用open())

1：请求已经建立，但是还没有发送(还没有调用send())

2：请求已经发送

3：请求正在处理中，通常响应中已经有部分数据可以用了

4：响应已经完成，可以获取并使用服务器的响应了

```js
 xhr.readyState // 获取Ajax状态码
```

**onreadystatechange事件**

> 当 Ajax 状态码发生变化时将自动触发该事件。

> 在事件处理函数中可以获取 Ajax 状态码并对其进行判断，当状态码为 4 时就可以通过 xhr.responseText 获取服务器端的响应数据了。

```js
 // 当Ajax状态码发生变化时
 xhr.onreadystatechange = function () {
     // 判断当Ajax状态码为4时
     if (xhr.readyState == 4) {
         // 获取服务器端的响应数据
         console.log(xhr.responseText);
     }
 }
```

| **区别描述**           | onload事件 | onreadystatechange事件 |
| ---------------------- | ---------- | ---------------------- |
| 是否兼容IE低版本       | 不兼容     | 兼容                   |
| 是否需要判断Ajax状态码 | 不需要     | 需要                   |
| 被调用次数             | 一次       | 多次                   |

### 错误处理

1. 网络畅通，服务器端能接收到请求，服务器端返回的结果不是预期结果。

   可以判断服务器端返回的状态码，分别进行处理。xhr.status 获取http状态码

2. 网络畅通，服务器端没有接收到请求，返回404状态码。

   检查请求地址是否错误。

3. 网络畅通，服务器端能接收到请求，服务器端返回500状态码。

   服务器端错误，找后端程序员进行沟通。

4. 网络中断，请求无法发送到服务器端。

   会触发xhr对象下面的onerror事件，在onerror事件处理函数中对错误进行处理。

5. 在低版本的 IE 浏览器中，Ajax 请求有严重的缓存问题，即在请求地址不发生变化的情况下，只有第一次请求会真正发送到服务器端，后续的请求都会从浏览器的缓存中获取结果。即使服务器端的数据更新了，客户端依然拿到的是缓存中的旧数据。

   在请求地址的后面加请求参数，保证每一次请求中的请求参数的值不相同

   ```js
    xhr.open('get', 'http://www.example.com?t=' + Math.random());
   ```

   

### Ajax封装

> 发送一次请求代码过多，发送多次请求代码冗余且重复。将请求代码封装到函数中，发请求时调用函数即可

```js
 ajax({ 
     type: 'get',
     url: 'http://www.example.com',
     success: function (data) { 
         console.log(data);
     }
 })
```

```js
function ajax (options) {
			// 存储的是默认值
			var defaults = {
				type: 'get',
				url: '',
				data: {},
				header: {
					'Content-Type': 'application/x-www-form-urlencoded'
				},
				success: function () {},
				error: function () {}
			};

			// 使用options对象中的属性覆盖defaults对象中的属性
			Object.assign(defaults, options);

			// 创建ajax对象
			var xhr = new XMLHttpRequest();
			// 拼接请求参数的变量
			var params = '';
			// 循环用户传递进来的对象格式参数
			for (var attr in defaults.data) {
				// 将参数转换为字符串格式
				params += attr + '=' + defaults.data[attr] + '&';
			}
			// 将参数最后面的&截取掉 
			// 将截取的结果重新赋值给params变量
			params = params.substr(0, params.length - 1);

			// 判断请求方式
			if (defaults.type == 'get') {
				defaults.url = defaults.url + '?' + params;
			}

			/*
				{
					name: 'zhangsan',
					age: 20
				}

				name=zhangsan&age=20

			 */

			// 配置ajax对象
			xhr.open(defaults.type, defaults.url);
			// 如果请求方式为post
			if (defaults.type == 'post') {
				// 用户希望的向服务器端传递的请求参数的类型
				var contentType = defaults.header['Content-Type']
				// 设置请求参数格式的类型
				xhr.setRequestHeader('Content-Type', contentType);
				// 判断用户希望的请求参数格式的类型
				// 如果类型为json
				if (contentType == 'application/json') {
					// 向服务器端传递json数据格式的参数
					xhr.send(JSON.stringify(defaults.data))
				}else {
					// 向服务器端传递普通类型的请求参数
					xhr.send(params);
				}

			}else {
				// 发送请求
				xhr.send();
			}
			// 监听xhr对象下面的onload事件
			// 当xhr对象接收完响应数据后触发
			xhr.onload = function () {

				// xhr.getResponseHeader()
				// 获取响应头中的数据
				var contentType = xhr.getResponseHeader('Content-Type');
				// 服务器端返回的数据
				var responseText = xhr.responseText;

				// 如果响应类型中包含applicaition/json
				if (contentType.includes('application/json')) {
					// 将json字符串转换为json对象
					responseText = JSON.parse(responseText)
				}

				// 当http状态码等于200的时候
				if (xhr.status == 200) {
					// 请求成功 调用处理成功情况的函数
					defaults.success(responseText, xhr);
				}else {
					// 请求失败 调用处理失败情况的函数
					defaults.error(responseText, xhr);
				}
			}
		}
```

### 同源政策

> Ajax 只能向自己的服务器发送请求。比如现在有一个A网站、有一个B网站，A网站中的 HTML 文件只能向A网站服务器中发送 Ajax 请求，B网站中的 HTML 文件只能向 B 网站中发送 Ajax 请求，但是 A 网站是不能向 B 网站发送 Ajax请求的，同理，B 网站也不能向 A 网站发送 Ajax请求。

> 如果两个页面拥有相同的协议、域名和端口，那么这两个页面就属于同一个源，其中只要有一个不相同，就是不同源。

> 同源政策是为了保证用户信息的安全，防止恶意的网站窃取数据。最初的同源政策是指 A 网站在客户端设置的 Cookie，B网站是不能访问的。

> 随着互联网的发展，同源政策也越来越严格，在不同源的情况下，其中有一项规定就是无法向非同源地址发送Ajax 请求，如果请求，浏览器就会报错。

#### 使用 JSONP 解决同源限制问题

> jsonp 是 json with padding 的缩写，它不属于 Ajax 请求，但它可以模拟 Ajax 请求。

1. 将不同源的服务器端请求地址写在 script 标签的 src 属性中

   ```html
    <script src="www.example.com"></script>
    <script src=“https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
   ```

2. 服务器端响应数据必须是一个函数的调用，真正要发送给客户端的数据需要作为函数调用的参数。

   ```js
   const data = 'fn({name: "张三", age: "20"})';
   res.send(data);
   ```

3. 在客户端全局作用域下定义函数 fn

   ```js
    function fn (data) { }
   ```

4. 在 fn 函数内部对服务器端返回的数据进行处理

   ```js
    function fn (data) { console.log(data); }
   ```



#### **CORS 跨域资源共享**

> 全称为 Cross-origin resource sharing，即跨域资源共享，它允许浏览器向跨域服务器发送 Ajax 请求，克服了 Ajax 只能同源使用的限制

![image-20220128125141136](C:\Users\HS_HG\AppData\Roaming\Typora\typora-user-images\image-20220128125141136.png)

Node 服务器端设置响应头示例代码：

```js
 app.use((req, res, next) => {
     res.header('Access-Control-Allow-Origin', '*');
     res.header('Access-Control-Allow-Methods', 'GET, POST');
     next();
 })
```



**服务器端解决方案**

> 同源政策是浏览器给予Ajax技术的限制，服务器端是不存在同源政策限制。

#### withCredentials属性

在使用Ajax技术发送跨域请求时，默认情况下不会在请求中携带cookie信息。

withCredentials：指定在涉及到跨域请求时，是否携带cookie信息，默认值为false

Access-Control-Allow-Credentials：true 允许客户端发送请求时携带cookie



### Ajax补充

{% post_link web/ajax/fromdata %}

{% post_link web/ajax/ajaxdemo %}

{% post_link web/ajax/jqueryajax %}
