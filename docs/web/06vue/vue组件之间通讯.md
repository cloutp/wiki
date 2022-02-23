---
title: vue组件间通讯
date: 2021-01-27 17:32:17
tags:
 - vue
categories:
 - vue
---

# Vue组件间通讯

### prop

> 支持父向子通讯，子 => 父 需要父传递一个函数子通过子调用

#### 传递

**父：**``` <Demo msg="hello" />```

#### 接收

**子：**{% post_link vue2配置项 %}



#### 子 = > 父

```js
<test :todo="todo"></test>
methods:{
    todo(val){
      alert(val)
    }
  }

// 子
props:['todo'],
methods:{
    alr(){
      this.todo('thesis')
    }
```



### 组件之间自定义事件

> 适用于：子组件 ===> 父组件

#### 父组件

```js
// 绑定事件
<Demo ref="demo" @atguigu="test"/> 
// or 
<Demo ref="demo" v-on:atguigu="test"/>

// 书写方法
......
mounted(){
   this.$refs.xxx.$on('atguigu',this.test)
}
```

> 若想让自定义事件只能触发一次，可以使用 once 修饰符，或 $once 方法

#### 子组件

```js
// 触发
this.$emit('atguigu',数据)
// 解绑
this.$off('atguigu')
```

> 组件上也可以绑定原生 DOM 事件，需要使用 native 修饰符。

**注意：**通过 this.refs.xxx. on('atguigu',回调)绑定自定义事件时，回调要么配置在 methods 中，要么用箭头函数，否则 this 指向会出问题！



### 全局事件总线（GlobalEventBus）

> 一种组件间通信的方式，适用于任意组件间通信。

#### 安装全局事件总线

```js
new Vue({
    ......
    beforeCreate() {
        Vue.prototype.$bus = this //安装全局事件总线，$bus就是当前应用的vm
    },
    ......
}) 
```

#### 使用

1. 绑定事件

   ```js
   methods(){
     demo(data){......}
   }
   ......
   mounted() {
     this.$bus.$on('xxxx',this.demo)
   }
   ```

2. 触发事件

   ```js
   this.$bus.$emit('xxxx',数据)
   ```

> 最好在 beforeDestroy 钩子中，用 $off 去解绑当前组件所用到的事件。



### 消息订阅与发布插件

> 使用比较少





### vue3新增后代通讯

### provide 与 inject

<img src="https://raw.githubusercontent.com/cloutp/blog_img/main/202201271719692.png" alt="image-20220127171928746" style="zoom: 50%;" />

- 作用：实现<strong style="color:#DD5145">祖与后代组件间</strong>通信

- 套路：父组件有一个 `provide` 选项来提供数据，后代组件有一个 `inject` 选项来开始使用这些数据

- 具体写法：

  1. 祖组件中：

     ```js
     setup(){
     	......
         let car = reactive({name:'奔驰',price:'40万'})
         provide('car',car)
         ......
     }
     ```

  2. 后代组件中：

     ```js
     setup(props,context){
     	......
         const car = inject('car')
         return {car}
     	......
     }
     ```

### 

