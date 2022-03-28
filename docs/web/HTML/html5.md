# HTML5

> HTML5是HTML最新的修订版本，2014年10月由万维网联盟（W3C）完成标准制定。设计目的是为了在移动设备上支持多媒体。

HTML5 中的一些有趣的新特性：

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

###  最小的HTML5文档

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>文档标题</title>
</head>
 
<body>
文档内容......
</body>
 
</html>
```

## 语义标签

| 标签           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| `<article>`    | 定义页面独立的内容区域。                                     |
| `<aside>`      | 定义页面的侧边栏内容。                                       |
| `<bdi>`        | 允许您设置一段文本，使其脱离其父元素的文本方向设置。         |
| `<command>`    | 定义命令按钮，比如单选按钮、复选框或按钮                     |
| `<details>`    | 用于描述文档或文档某个部分的细节                             |
| `<dialog>`     | 定义对话框，比如提示框                                       |
| `<summary>`    | 标签包含 details 元素的标题                                  |
| `<figure>`     | 规定独立的流内容（图像、图表、照片、代码等等）。             |
| `<figcaption>` | 定义 <figure> 元素的标题                                     |
| `<footer>`     | 定义 section 或 document 的页脚。                            |
| `<header>`     | 定义了文档的头部区域                                         |
| `<mark>`       | 定义带有记号的文本。                                         |
| `<meter>`      | 定义度量衡。仅用于已知最大和最小值的度量。                   |
| `<nav>`        | 定义导航链接的部分。                                         |
| `<progress>`   | 定义任何类型的任务的进度。                                   |
| `<ruby>`       | 定义 ruby 注释（中文注音或字符）。                           |
| `<rt>`         | 定义字符（中文注音或字符）的解释或发音。                     |
| `<rp>`         | 在 ruby 注释中使用，定义不支持 ruby 元素的浏览器所显示的内容。 |
| `<section>`    | 定义文档中的节（section、区段）。                            |
| `<time>`       | 定义日期或时间。                                             |
| `<wbr>`        | 规定在文本中的何处适合添加换行符。                           |

## HTML5 多媒体

### Video

> `<video>` 元素支持多个 `<source>` 元素. `<source>` 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式：

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
您的浏览器不支持Video标签。
</video>
```

> control 属性供添加播放、暂停和音量控件

#### 视频格式

当前， <video> 元素支持三种视频格式： MP4, WebM, 和 Ogg:

- MP4 = 带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
- WebM = 带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件
- Ogg = 带有 Theora 视频编码和 Vorbis 音频编码的 Ogg 文件

| 格式 | MIME-type  |
| ---- | ---------- |
| MP4  | video/mp4  |
| WebM | video/webm |
| Ogg  | video/ogg  |

### Audio

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
您的浏览器不支持 audio 元素。
</audio>
```

> 在<audio> 与 </audio> 之间你需要插入浏览器不支持的<audio>元素的提示文本 。

#### 音频格式及浏览器支持

目前, <audio>元素支持三种音频格式文件: MP3, Wav, 和 Ogg:

## HTML5 input

> HTML5 拥有多个新的表单输入类型。这些新特性提供了更好的输入控制和验证。

|   input类型    |                   说明                   | 代码                                                  |
| :------------: | :--------------------------------------: | ----------------------------------------------------- |
|     color      |               用于选取颜色               | <input type="color" name="favcolor">                  |
|      date      |   允许你从一个日期选择器选择一个日期。   | <input type="date" name="bday">                       |
|    datetime    |        选择一个日期（UTC 时间）。        | <input type="datetime" name="bdaytime">               |
| datetime-local |    允许你选择一个日期和时间 (无时区).    | <input type="datetime-local" name="bdaytime">         |
|     email      |   会自动验证 email 域的值是否合法有效:   | <input type="email" name="email">                     |
|     month      |              选择一个月份。              | <input type="month" name="bdaymonth">                 |
|     number     |              数值的输入域。              | <input type="number" name="quantity" min="1" max="5"> |
|     range      |        一定范围内数字值的输入域。        | <input type="range" name="points" min="1" max="10">   |
|     search     | 用于搜索域，比如站点搜索或 Google 搜索。 | <input type="search" name="googlesearch">             |
|      tel       |                 电话号码                 | <input type="tel" name="usrtel">                      |
|      time      |          时间控制器（无时区）：          | <input type="time" name="usr_time">                   |
|      url       |            URL 地址的输入域。            | <input type="url" name="homepage">                    |
|      week      |             周和年 (无时区):             | <input type="week" name="week_year">                  |
|                |                                          |                                                       |

### number限定

| 属性      | 描述                       |
| --------- | -------------------------- |
| disabled  | 规定输入字段是禁用的       |
| max       | 规定允许的最大值           |
| maxlength | 规定输入字段的最大字符长度 |
| min       | 规定允许的最小值           |
| pattern   | 规定用于验证输入字段的模式 |
| readonly  | 规定输入字段的值无法修改   |
| required  | 规定输入字段的值是必需的   |
| size      | 规定输入字段中的可见字符数 |
| step      | 规定输入字段的合法数字间隔 |
| value     | 规定输入字段的默认值       |



## HTML5 表单元素

### `<datalist>` 元素

> 规定输入域的选项列表。规定 form 或 input 域应该拥有自动完成功能。当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项：

使用 <input> 元素的列表属性与 <datalist> 元素绑定.

```html
<input list="browsers">
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```



###  `<keygen>` 元素

> 提供一种验证用户的可靠方法,用于表单的密钥对生成器字段。

当提交表单时，会生成两个键，一个是私钥，一个公钥。

私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。

```html
<form action="demo_keygen.asp" method="get">
用户名: <input type="text" name="usr_name">
加密: <keygen name="security">
<input type="submit">
</form>
```

### `<output> `元素

用于不同类型的输出，比如计算或脚本输出：

```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100 +
<input type="number" id="b" value="50">=
<output name="x" for="a b"></output>
</form>
```















## HTML5 Web存储

### 客户端存储

- localStorage - 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。
- sessionStorage - 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

**检查浏览器是否支持：**

```js
if(typeof(Storage)!=="undefined")
{
    // 是的! 支持 localStorage  sessionStorage 对象!
    // 一些代码.....
} else {
    // 抱歉! 不支持 web 存储。
}
```

#### localStorage 对象

```js
// 存储
localStorage.setItem("sitename", "菜鸟教程");
 
// 查找
localStorage.getItem("sitename");
// 移除 
localStorage.removeItem("sitename");
```

#### sessionStorage 对象

```js

sessionStorage.clickcount=1;

sessionStorage.clickcount
```

### 扩展

- [webSQL]()
- [Web应用程序缓存]()



















































































### 语义化标签

**新增了那些语义化标签**

* `header`   ---  头部标签
* `nav`        ---  导航标签
* `article` ---   内容标签
* `section` ---   块级标签
* `aside`     ---   侧边栏标签
* `footer`   ---   尾部标签

### 多媒体音频标签

1. 多媒体标签有两个，分别是

* 音频  -- `audio`
* 视频  -- `video`

1. `audio` 标签说明

* 可以在不使用标签的情况下，也能够原生的支持音频格式文件的播放，
* 但是：播放格式是有限的

1. audio 支持的音频格式

   * audio 目前支持三种格式

2. audio 的参数  

5、audio 代码演示

```css
<body>
  <!-- 注意：在 chrome 浏览器中已经禁用了 autoplay 属性 -->
  <!-- <audio src="./media/snow.mp3" controls autoplay></audio> -->

  <!-- 
    因为不同浏览器支持不同的格式，所以我们采取的方案是这个音频准备多个文件
   -->
  <audio controls>
    <source src="./media/snow.mp3" type="audio/mpeg" />
  </audio>
</body>
```

### 多媒体视频标签

1. video 视频标签

   * 目前支持三种格式

2. 语法格式

```html
<video src="./media/video.mp4" controls="controls"></video>
```

1. video 参数  
2. video 代码演示

```html
<body>
  <!-- <video src="./media/video.mp4" controls="controls"></video> -->

  <!-- 谷歌浏览器禁用了自动播放功能，如果想自动播放，需要添加 muted 属性 -->
  <video controls="controls" autoplay muted loop poster="./media/pig.jpg">
    <source src="./media/video.mp4" type="video/mp4">
    <source src="./media/video.ogg" type="video/ogg">
  </video>
</body>
```

1. 多媒体标签总结

* 音频标签与视频标签使用基本一致
* 多媒体标签在不同浏览器下情况不同，存在兼容性问题
* 谷歌浏览器把音频和视频标签的自动播放都禁止了
* 谷歌浏览器中视频添加 muted 标签可以自己播放
* 注意：重点记住使用方法以及自动播放即可，其他属性可以在使用时查找对应的手册

### 新增 input 标签

- color
- date
- datetime
- datetime-local
- email
- month
- number
- range
- search
- tel
- time
- url
- week

### 新增表单属性

```html
<datalist> 选项列表。与 input 元素配合使用，定义 input 可能的值
<keygen> 用于表单的密钥对生成器字段
<output> 不同类型的输出，比如脚本的输出。
```

