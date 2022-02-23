---
title: vue简单使用
date: 2022-01-27 15:32:17
tags:
 - vue
categories:
 - vue

---

## Vue简单使用

### 简单介绍

1. 想让 Vue 工作，就必须创建一个 Vue 实例，且要传入一个配置对象；

2. root 容器里的代码依然符合 html 规范，只不过混入了一些特殊的 Vue 语法；

3. root 容器里的代码被称为【Vue 模板】；

4. Vue 实例和容器是一一对应的；

5. 真实开发中只有一个 Vue 实例，并且会配合着组件一起使用；

6. {{xxx}}中的 xxx 要写 js 表达式，且 xxx 可以自动读取到 data 中的所有属性；

7. 一旦 data 中的数据发生改变，那么页面中用到该数据的地方也会自动更新；

### 常用命令（webpack）

#### 安装vue命令行工具

```shell
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

#### 创建项目

```shell
vue create 项目名称
# OR
vue ui
```

> 第一种会在命令行选择版本信息配置，第二种在浏览器图形化界面配置项目

#### 启动项目

```shell
vue serve
```

#### 生成静态文件

```shell
vue build
```



#### 升级

```shell
npm update -g @vue/cli
# 或者
yarn global upgrade --latest @vue/cli
# -----------------------------------
用法： upgrade [options] [plugin-name]
选项：
  -t, --to <version>    升级 <plugin-name> 到指定的版本
  -f, --from <version>  跳过本地版本检测，默认插件是从此处指定的版本升级上来
  -r, --registry <url>  使用指定的 registry 地址安装依赖
  --all                 升级所有的插件
  --next                检查插件新版本时，包括 alpha/beta/rc 版本在内
  -h, --help            输出帮助内容
```

### 常用命令（vite）

> 开发环境中，无需打包操作，可快速的冷启动。按需编译，不再等待整个应用编译完成。

<img src="https://raw.githubusercontent.com/cloutp/blog_img/main/202201271651988.png" alt="image-20220127165038215" style="zoom: 33%;" />



```shell
## 创建工程
npm init vite-app <project-name>
## 进入工程目录
cd <project-name>
## 安装依赖
npm install
## 运行
npm run dev
```

### vue的目录规范

```shell
├── node_modules 
├── public
│   ├── favicon.ico: 页签图标
│   └── index.html: 主页面
├── src
│   ├── hooks: 存放钩子资源/vue3
│   ├── assets: 存放静态资源
│   │   └── logo.png
│   │── component: 存放组件
│   │   └── HelloWorld.vue
│   │── App.vue: 汇总所有组件
│   │── main.js: 入口文件
├── .gitignore: git版本管制忽略的配置
├── babel.config.js: babel的配置文件
├── package.json: 应用包配置文件 
├── README.md: 应用描述文件
├── package-lock.json：包版本控制文件
```



