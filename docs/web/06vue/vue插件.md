---
title: vue插件
date: 2012-01-27 17:32:17
tags:
 - vue
categories:
 - vue
---

# vue插件

> 用于增强 Vue,包含 install 方法的一个对象，install 的第一个参数是 Vue，第二个以后的参数是插件使用者传递的数据

### 定义插件

```js
// plugins.js
export default {
	install(Vue,x,y,z){
            console.log(x,y,z)
            //全局过滤器
            Vue.filter('mySlice',function(value){
                return value.slice(0,4)
            })
            //定义全局指令
            Vue.directive('fbind',{
                //指令与元素成功绑定时（一上来）
                bind(element,binding){
                element.value = binding.value
                },
                //指令所在元素被插入页面时
                inserted(element,binding){
                    element.focus()
                },
                //指令所在的模板被重新解析时
                update(element,binding){
                    element.value = binding.value
                }
            })

		//定义混入
		Vue.mixin({
			data() {
				return {
					x:100,
					y:200
				}
			},
		})

		//给Vue原型上添加一个方法（vm和vc就都能用了）
		Vue.prototype.hello = ()=>{alert('你好啊')}
	}
}
```

### 使用插件

```js

// main.js
//引入插件
import plugins from './plugins'
//应用（使用）插件
Vue.use(plugins,1,2,3)

```

