---
title: head下标签
date: 2022-01-08 13:30:40
tags:
 - web
categories:
 - web

---



### 网站标题

title 具有不可替代性，是我们的内页第一个重要标签，是搜索引擎了解网页的入口，和对网页主题归属的最佳判断点。

```html
<head>
	<title>you title</title>
</head>
```

建议：

首页标题：网站名（产品名）- 网站的介绍



### 网站 ico 图标

* **首先把 favicon.ico 这个图标放到根目录下。**
* **再 html 里面，  head 之间 引入 代码。**

```css
<link rel="shortcut icon" href="favicon.ico"  type="image/x-icon"/>   
```

### base 标签

```html
<base target="_blank" />
```

**总结：**

1. base 可以设置整体链接的打开状态
2. base 写到 ` <head></head> ` 之间
3. 把所有的连接 都默认添加` target="_blank"`

### meta

> 元数据（metadata）是关于数据的信息。

> 标签提供关于 HTML 文档的元数据。元数据不会显示在页面上，但是对于机器是可读的。
>
> 典型的情况是，meta 元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据。
>
> 标签始终位于 head 元素中。
>
> 元数据可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务

meta里的数据是供机器解读的，告诉机器该如何解析这个页面，还有一个用途是可以添加服务器发送到浏览器的http头部内容，例如我们为页面中添加如下meta标签：

```html
<meta http-equiv="charset" content="iso-8859-1">
<meta http-equiv="expires" content="31 Dec 2008">
```

那么浏览器的头部就会包括这些:

```html
charset:iso-8859-1
expires:31 Dec 2008
```

> **meta标签补充**：{% post_link web/01HTML/meta  %}



### 字体图标

#### 引入到 HTML

**引入：**

```css
@font-face {
  font-family: 'icomoon';
  src:  url('fonts/icomoon.eot?7kkyc2');
  src:  url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
    url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
    url('fonts/icomoon.woff?7kkyc2') format('woff'),
    url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
}
```

**设置盒子字体：**

```css
span {
    font-family: "icomoon";
  }
```

