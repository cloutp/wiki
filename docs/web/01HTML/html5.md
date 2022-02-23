---
title: HTML5新增
date: 2022-01-08 13:30:39
tags:
 - web
categories:
 - web
---

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

