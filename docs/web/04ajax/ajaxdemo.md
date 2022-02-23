---
title: AjaxDemo
date: 2022-01-23 14:33:50
tags:
 - AJAX
 - web
categories:
 - web
 - AJAX
---

### 验证邮箱地址唯一性

```html
<body>
	<div class="container">
		<div class="form-group">
			<label>邮箱地址</label>
			<input type="email" class="form-control" placeholder="请输入邮箱地址" id="email">
		</div>
		<!-- 错误 bg-danger 正确 bg-success -->
		<p id="info"></p>
	</div>
	<script src="/js/ajax.js"></script>
	<script>
		// 获取页面中的元素
		var emailInp = document.getElementById('email');
		var info = document.getElementById('info');

		// 当文本框离开焦点以后
		emailInp.onblur = function () {
			// 获取用户输入的邮箱地址
			var email = this.value;
			// 验证邮箱地址的正则表达式
			var reg = /^[A-Za-z\d]+([-_.][A-Za-z\d]+)*@([A-Za-z\d]+[-.])+[A-Za-z\d]{2,4}$/;
			// 如果用户输入的邮箱地址不符合规则
			if (!reg.test(email)) {
				// 给出用户提示
				info.innerHTML = '请输入符合规则的邮箱地址';
				// 让提示信息显示为错误提示信息的样式
				info.className = 'bg-danger';
				// 阻止程序向下执行
				return;
			}

			// 向服务器端发送请求
			ajax({
				type: 'get',
				url: 'http://localhost:3000/verifyEmailAdress',
				data: {
					email: email
				},
				success: function (result) {
					console.log(result);
					info.innerHTML = result.message;
					info.className = 'bg-success';
				},
				error: function (result) {
					console.log(result)
					info.innerHTML = result.message;
					info.className = 'bg-danger';
				}
			});

		}
	</script>
</body>
```

### 搜索框自动提示

```js
<body>
	<div class="container">
		<div class="form-group">
			<input type="text" class="form-control" placeholder="请输入搜索关键字" id="search">
			<ul class="list-group" id="list-box">
				
			</ul>
		</div>
	</div>
	<script src="/js/ajax.js"></script>
	<script src="/js/template-web.js"></script>
	<script type="text/html" id="tpl">
		{{each result}}
			<li class="list-group-item">{{$value}}</li>
		{{/each}}
	</script>
	<script>
		// 获取搜索框
		var searchInp = document.getElementById('search');
		// 获取提示文字的存放容器
		var listBox = document.getElementById('list-box');
		// 存储定时器的变量
		var timer = null;
		// 当用户在文本框中输入的时候触发
		searchInp.oninput = function () {
			// 清除上一次开启的定时器
			clearTimeout(timer);
			// 获取用户输入的内容
			var key = this.value;
			// 如果用户没有在搜索框中输入内容
			if (key.trim().length == 0) {
				// 将提示下拉框隐藏掉
				listBox.style.display = 'none';
				// 阻止程序向下执行
				return;
			}

			// 开启定时器 让请求延迟发送
			timer = setTimeout(function () {
				// 向服务器端发送请求
				// 向服务器端索取和用户输入关键字相关的内容
				ajax({
					type: 'get',
					url: 'http://localhost:3000/searchAutoPrompt',
					data: {
						key: key
					},
					success: function (result) {
						// 使用模板引擎拼接字符串
						var html = template('tpl', {result: result});
						// 将拼接好的字符串显示在页面中
						listBox.innerHTML = html;
						// 显示ul容器
						listBox.style.display = 'block';
					}
				})
			}, 800)
			
		}
	</script>
</body>
```

