---
title: Node
date: 2022-01-20 12:33:41
tags:
 - web
 - NodeJs
categories:
 - web
 - NodeJs
---

# NodeJs

> **Node**是一个基于Chrome V8引擎的JavaScript**代码运行环境**。

> **浏览器**是一个基于JS引擎的JavaScript**代码运行环境**。

## Node组成

> lNode.js是由**ECMAScript**及**Node 环境**提供的一些**附加API**组成的，包括文件、网络、路径等等一些更加强大的 API。

<img src="C:\Users\HS_HG\AppData\Roaming\Typora\typora-user-images\image-20220127173628817.png" alt="image-20220127173628817" style="zoom:80%;" />



## Node.js全局对象global

> 在**浏览器**中全局对象是**window**，在**Node**中全局对象是**global**。

> Node中全局对象下方法，可以在任何地方使用，global可以省略。

- lconsole.log()   在控制台中输出

- lsetTimeout()   设置超时定时器

- lclearTimeout() 清除超时时定时器

- lsetInterval()   设置间歇定时器

- lclearInterval()  清除间歇定时器

## Node.js中模块化开发

> Node.js规定一个JavaScript文件就是一个模块，模块内部定义的变量和函数默认情况下在外部无法得到

> 模块内部可以使用exports对象进行成员导出，使用require方法导入其他模块。

#### 模块成员导出

```js
  // a.js
  // 在模块内部定义变量
 let version = 1.0;
 // 在模块内部定义方法
 const sayHi = name => `您好, ${name}`;
 // 向模块外部导出数据 
 exports.version = version;
 exports.sayHi = sayHi;

```

> **exports**是**module.exports**的别名**(地址引用关系)**，导出对象最终以module.exports为准

```js
module.exports.version = version;
module.exports.sayHi = sayHi;
```

#### 模块成员的导入

```js
  // b.js
  // 在b.js模块中导入模块a
 let a = require('./b.js');
  // 输出b模块中的version变量
 console.log(a.version);
  // 调用b模块中的sayHi方法 并输出其返回值
 console.log(a.sayHi('黑马讲师')); 
```

>  导入模块时后缀可以省略

{% post_link web/node/系统模块 %}

{% post_link web/node/第三方模块 %}



## package.json文件

### node_modules文件夹的问题

1. 文件夹以及文件过多过碎，当我们将项目整体拷贝给别人的时候,，传输速度会很慢很慢. 

2. 复杂的模块依赖关系需要被记录，确保模块的版本和当前保持一致，否则会导致当前项目运行报错

### package.json文件的作用

项目描述文件，记录了当前项目信息，例如项目名称、版本、作者、github地址、当前项目依赖了哪些第三方模块等。

使用`npm init -y`命令生成。

#### 项目依赖

在项目的开发阶段和线上运营阶段，都需要依赖的第三方包，称为项目依赖

使用npm install 包名命令下载的文件会默认被添加到 package.json 文件的 dependencies 字段中

```json
 {
    "dependencies": {
        "jquery": "^3.3.1“
    }
 } 
```

#### 开发依赖

在项目的开发阶段需要依赖，线上运营阶段不需要依赖的第三方包，称为开发依赖

使用`npm install` 包名 `--save-dev`命令将包添加到`package.json`文件的`devDependencies`字段中

```json
 {
    "devDependencies": {
        "gulp": "^3.9.1“
    }
 } 
```

### package-lock.json文件的作用

锁定包的版本，确保再次下载时不会因为包版本不同而产生问题

加快下载速度，因为该文件中已经记录了项目所依赖第三方包的树状结构和包的下载地址，重新安装时只需下载即可，不需要做额外的工作





## NodeJs中的模块加载机制

### 模块查找规则-当模块拥有路径但没有后缀时

```js
require('./find');
```

1. require方法根据模块路径查找模块，如果是完整路径，直接引入模块。

2. 如果模块后缀省略，先找同名JS文件再找同名JS文件夹

3. 如果找到了同名文件夹，找文件夹中的index.js

4. 如果文件夹中没有index.js就会去当前文件夹中的package.json文件中查找main选项中的入口文件

5. 如果找指定的入口文件不存在或者没有指定入口文件就会报错，模块没有被找到

### 模块查找规则-当模块没有路径且没有后缀时

```js
require('find');
```

1. Node.js会假设它是系统模块
2. Node.js会去node_modules文件夹中
3. 首先看是否有该名字的JS文件
4. 再看是否有该名字的文件夹
5. 如果是文件夹看里面是否有index.js
6. 如果没有index.js查看该文件夹中的package.json中的main选项确定模块入口文件
7. 否则找不到报错





## NodeJs异步编程

{% post_link web/node/异步编程 %}



## NodeJs网站服务器

{% post_link web/node/web服务 %}

{% post_link web/node/第三方模块 %}

