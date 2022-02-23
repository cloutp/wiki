---
title: vue动画和过渡
date: 2013-01-27 17:32:17
tags:
 - vue
categories:
 - vue
---

# vue动画

> 在插入、更新或移除 DOM 元素时，在合适的时候给元素添加样式类名。

### 样式类名

1. 元素进入起点

   1. v-enter：进入的起点

   2. v-enter-active：进入过程中

   3. v-enter-to：进入的终点

2. ```css
   
   
   ```

   

3. 元素离开样式

   1. v-leave：离开的起点
   2. v-leave-active：离开过程中

   3. v-leave-to：离开的终点

### 使用

> 使用 `<transition>` 包裹要过度的元素，并配置 name 属性

```js
<transition name="hello">
	<h1 v-show="isShow">你好啊！</h1>
</transition>
```

> 若有多个元素需要过度，则需要使用：`<transition-group>`，且每个元素都要指定 `key` 值。

```css
h1{
  background-color: orange;
}
/* 进入的起点、离开的终点 */
.hello-enter,.hello-leave-to{
  transform: translateX(-100%);
}
.hello-enter-active,.hello-leave-active{
  transition: 0.5s linear;
}
/* 进入的终点、离开的起点 */
.hello-enter-to,.hello-leave{
  transform: translateX(0);
}
```

