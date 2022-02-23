---
title: vue插槽
date: 2014-01-27 17:32:17
tags:
 - vue
categories:
 - vue
---

# vue插槽

> 让父组件可以向子组件指定位置插入 html 结构，也是一种组件间通信的方式，适用于 **父组件 ===> 子组件** 。

### 默认插槽

#### 父组件

```vue
<子组件>
   <div>html结构1</div>
</子组件>
```

#### 子组件

```vue
<template>
    <div>
       <!-- 定义插槽 -->
       <slot>插槽默认内容...</slot>
    </div>
</template>
```



### 具名插槽

#### 父组件

```vue
<子组件>
    <template slot="center">
      <div>html结构1</div>
    </template>

    <template v-slot:footer>
       <div>html结构2</div>
    </template>
</子组件>
```

#### 子组件

```vue
<template>
    <div>
       <!-- 定义插槽 -->
       <slot name="center">插槽默认内容...</slot>
       <slot name="footer">插槽默认内容...</slot>
    </div>
</template>
```



### 作用域插槽

> 数据在组件的自身，但根据数据生成的结构需要组件的使用者来决定。（games 数据在 子组件中，但使用数据所遍历出来的结构由 App 组件决定）

#### 父组件

```vue
<子组件>
    // scope接受一个对象，里面包含了传入的数据
    <template scope="scopeData">
        <!-- 生成的是ul列表 -->
        <ul>
             <li v-for="g in scopeData.games" :key="g">{{g}}</li>
        </ul>
    </template>
</子组件>
<子组件>
    <template slot-scope="scopeData">
        <!-- 生成的是h4标题 -->
        <h4 v-for="g in scopeData.games" :key="g">{{g}}</h4>
    </template>
</子组件>
```

#### 子组件

```vue
<template>
    <div>
        // 将数据绑定到插槽
        <slot :games="games"></slot>
    </div>
</template>

<script>
    export default {
        name:'Category',
        props:['title'],
        //数据在子组件自身
        data() {
            return {
                games:['红色警戒','穿越火线','劲舞团','超级玛丽']
            }
        },
    }
</script>
```

