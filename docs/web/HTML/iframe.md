> 定义一个内联的iframe

### 语法

```html
<iframe src="URL"></iframe>
```

- URL：URL指向不同的网页。
- height 和 width ：用来定义iframe标签的高度与宽度。
- frameborder： 用于定义iframe表示是否显示边框，设置属性值为 "0" 移除iframe的边框:



>  iframe 可以显示一个目标链接的页面

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a" rel="noopener">RUNOOB.COM</a></p>
```
