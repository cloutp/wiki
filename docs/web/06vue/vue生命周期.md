---
title: vue生命周期
date: 2022-01-27 14:32:17
tags:
 - vue
categories:
 - vue
---

# vue生命周期

> 生命周期，又名：生命周期回调函数、生命周期函数、生命周期钩子。是Vue 在关键时刻帮我们调用的一些特殊名称的函数，生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。 生命周期函数中的 this 指向是 vm 或 组件实例对象。 

常见的生命周期使用：

1. mounted: 发送 ajax 请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。
2. beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

## vue2

> 在vue2中的生命周期函数书写在vue实例身上的配置项中

```js
beforeCreate() {
    console.log('beforeCreate')
},
created() {
    console.log('created')
},
beforeMount() {
    console.log('beforeMount')
},
mounted() {
    console.log('mounted')
},
beforeUpdate() {
    console.log('beforeUpdate')
},
updated() {
    console.log('updated')
},
beforeDestroy() {
    console.log('beforeDestroy')
},
destroyed() {
    console.log('destroyed')
},
```

### vue2图示![image-20220127133926963](https://raw.githubusercontent.com/cloutp/blog_img/main/202201271339125.png)



## vue3

> vue3中有些许变动，书写时可以和vue2一样书写在配置项中，也可以在setup中书写，在setup中书写需要进行变化

