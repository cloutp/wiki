---
title: CSS
date: 2022-01-26 13:30:37
tags:
 - web
categories:
 - web
---

## CSS

>  CSS(Cascading Style Sheets)  ，通常称为 CSS 样式表或层叠样式表（级联样式表）

**作用：**

1. 主要用于设置 HTML 页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及版面的布局和外观显示样式。
2. CSS 以 HTML 为基础，提供了丰富的功能，如字体、颜色、背景的控制及整体排版等，而且还可以针对不同的浏览器设置不同的样式。

### 引入方式

1. 行间样式

   ```html
   <标签名 style="属性1:属性值1; 属性2:属性值2; 属性3:属性值3;"> 内容 </标签名>内部样式表
   ```

2. style标签

   ```html
   
   ```

3. 外部样式

   ```html
   <head>
     <link rel="stylesheet" type="text/css" href="css文件路径">
   </head>
   link 是个单标签
   link 标签需要放在 head 头部标签中，并且指定 link 标签的三个属性
   ```

   | **属性** | **作用**                                                     |
   | -------- | ------------------------------------------------------------ |
   | **rel**  | **定义当前文档与被链接文档之间的关系，在这里需要指定为“stylesheet”，表示被链接的文档是一个样式表文件。** |
   | **type** | **定义所链接文档的类型，在这里需要指定为“text/CSS”，表示链接的外部文件为 CSS 样式表。我们都可以省略** |
   | **href** | **定义所链接外部样式表文件的 URL，可以是相对路径，也可以是绝对路径。** |

4. **三种样式表总结（位置）**

   | **样式表**     | **优点**                     | **缺点**                     | **使用情况**       | **控制范围**           |
   | -------------- | ---------------------------- | ---------------------------- | ------------------ | ---------------------- |
   | **行内样式表** | **书写方便，权重高**         | **没有实现样式和结构相分离** | **较少**           | **控制一个标签（少）** |
   | **内部样式表** | **部分结构和样式相分离**     | **没有彻底分离**             | **较多**           | **控制一个页面（中）** |
   | **外部样式表** | **完全实现结构和样式相分离** | **需要引入**                 | **最多，强烈推荐** | **控制整个站点（多）** |



### 注释

#### 单行注释

```css
//
```

#### 多行注释

```css
/*
*/
```

## CSS后续

- {% post_link web/02CSS/01选择器 %}

- {% post_link web/02CSS/02css属性 %}

- {% post_link web/02CSS/03盒子模型 %}

- {% post_link web/02CSS/04css布局 %}

- {% post_link web/02CSS/05两个bug %}

- {% post_link web/02CSS/06css技巧 %}

- {% post_link web/02CSS/07css3 %}

  