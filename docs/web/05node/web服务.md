---
title: web服务
date: 2022-01-18 12:17:41
tags:
 - web
 - NodeJs
categories:
 - web
 - NodeJs

---

# NodeJs提供网络服务

## HTTP模块

### 创建web服务器

```js
  // 引用系统模块
 const http = require('http');
  // 创建web服务器
 const app = http.createServer();
  // 当客户端发送请求的时候
 app.on('request', (req, res) => {
        //  响应
       res.end('<h1>hi, user</h1>');
 });
  // 监听3000端口
 app.listen(3000);
 console.log('服务器已启动，监听3000端口，请访问 localhost:3000')
```

### 请求与响应处理

#### 请求报文处理

```js
 app.on('request', (req, res) => {
     req.headers  // 获取请求报文
     req.url      // 获取请求地址
     req.method   // 获取请求方法
 });
```

#### 设置响应报头

**HTTP状态码**

1. 200 请求成功

2. 404 请求的资源没有被找到

3. 500 服务器端错误

4. 400 客户端请求有语法错误

**内容类型**

1. text/html

2. text/css

3. application/javascript

4. image/jpeg

5. application/json

```js
 app.on('request', (req, res) => {
     // 设置响应报文
     res.writeHead(200, {
         'Content-Type': 'text/html;charset=utf8‘
     });
 });

```

#### GET请求参数

> 参数被放置在浏览器地址栏中，例如：http://localhost:3000/**?name=zhangsan&age=20**

**参数获取需要借助系统模块url，url模块用来处理url地址**

```js
 const http = require('http');
 // 导入url系统模块 用于处理url地址
 const url = require('url');
 const app = http.createServer();
 app.on('request', (req, res) => {
     // 将url路径的各个部分解析出来并返回对象
         // true 代表将参数解析为对象格式
     let {query} = url.parse(req.url, true);
     console.log(query);
 });
 app.listen(3000);
```

#### POST请求参数

>  参数被放置在请求体中进行传输

**获取POST参数需要使用data事件和end事件**

**使用querystring系统模块将参数转换为对象格式**

```js
 // 导入系统模块querystring 用于将HTTP参数转换为对象格式
 const querystring = require('querystring');
 app.on('request', (req, res) => {
     let postData = '';
     // 监听参数传输事件
     req.on('data', (chunk) => postData += chunk;);
     // 监听参数传输完毕事件
     req.on('end', () => { 
         console.log(querystring.parse(postData)); 
     }); 
 });
```



### 路由

> 路由是指客户端请求地址与服务器端程序代码的对应关系。

![image-20220127183119090](https://raw.githubusercontent.com/cloutp/blog_img/main/202201271831296.png)

**处理：**

```js
 // 当客户端发来请求的时候
 app.on('request', (req, res) => {
     // 获取客户端的请求路径
     let { pathname } = url.parse(req.url);
     if (pathname == '/' || pathname == '/index') {
         res.end('欢迎来到首页');
     } else if (pathname == '/list') {
         res.end('欢迎来到列表页页');
     } else {
        res.end('抱歉, 您访问的页面出游了');
     }
 });
```

### 静态资源

> 服务器端不需要处理，可以直接响应给客户端的资源就是静态资源，例如CSS、JavaScript、image文件。

### 动态资源

> 相同的请求地址不同的响应资源，这种资源就是动态资源。



## 数据库处理（mongoDB）

> 数据库即存储数据的仓库，可以将数据进行有序的分门别类的存储。它是独立于语言之外的软件，可以通过API去操作它。



### Node中的数据库概念

| **术语**   | **解释说明**                                             |
| ---------- | -------------------------------------------------------- |
| database   | 数据库，mongoDB数据库软件中可以建立多个数据库            |
| collection | 集合，一组数据的集合，可以理解为JavaScript中的数组       |
| document   | 文档，一条具体的数据，可以理解为JavaScript中的对象       |
| field      | 字段，文档中的属性名称，可以理解为JavaScript中的对象属性 |

### 数据库连接

> 使用mongoose提供的**connect**方法即可连接数据库。

```js
// mongoose.connect('mongodb://user:pass@localhost:port/database') 
mongoose.connect('mongodb://localhost/playground')
     .then(() => console.log('数据库连接成功'))
     .catch(err => console.log('数据库连接失败', err));
```



### 数据库创建

> 在MongoDB中**不需要显式创建数据库**，如果正在使用的数据库不存在，MongoDB会自动创建。

### 创建集合(表)

>  创建集合分为两步，一是对**对集合设定规则**，二是**创建集合**，创建mongoose.Schema构造函数的实例即可创建集合。

```js
// 设定集合规则
const courseSchema = new mongoose.Schema({
 name: String,
 author: String,
 isPublished: Boolean
});
// 创建集合并应用规则
const Course = mongoose.model('Course', courseSchema); // courses
```



### 创建文档

> 创建文档实际上就是向集合中插入数据。

```js
  // 创建集合实例
 const course = new Course({
     name: 'Node.js course',
     author: '黑马讲师',
     tags: ['node', 'backend'],
     isPublished: true
 });
// 将数据保存到数据库中
course.save();


Course.create({name: 'JavaScript基础', author: '黑马讲师', isPublish: true}, (err, doc) => { 
     //  错误对象
    console.log(err)
     //  当前插入的文档
    console.log(doc)
});
Course.create({name: 'JavaScript基础', author: '黑马讲师', isPublish: true})
      .then(doc => console.log(doc))
      .catch(err => console.log(err))

```

### 查询文档

```js
//  根据条件查找文档（条件为空则查找所有文档）
Course.find().then(result => console.log(result))
//  根据条件查找文档
Course.findOne({name: 'node.js基础'}).then(result => console.log(result))

```

```json
// 返回文档集合
[{
    _id: 5c0917ed37ec9b03c07cf95f,
    name: 'node.js基础',
    author: '黑马讲师‘
},{
     _id: 5c09dea28acfb814980ff827,
     name: 'Javascript',
     author: '黑马讲师‘
}]
```

```js
 //  匹配大于 小于
 User.find({age: {$gt: 20, $lt: 50}}).then(result => console.log(result))
 //  匹配包含
 User.find({hobbies: {$in: ['敲代码']}}).then(result => console.log(result))
 //  选择要查询的字段  
 User.find().select('name email').then(result => console.log(result))
 // 将数据按照年龄进行排序
 User.find().sort('age').then(result => console.log(result))
 //  skip 跳过多少条数据  limit 限制查询数量
 User.find().skip(2).limit(2).then(result => console.log(result))
 // 删除单个
Course.findOneAndDelete({}).then(result => console.log(result))
 // 删除多个
User.deleteMany({}).then(result => console.log(result))
```

### MongoDB验证

> 在创建集合规则时，可以设置当前字段的验证规则，验证失败就则输入插入失败。

1. required: true 必传字段
2. minlength：3 字符串最小长度
3. maxlength: 20 字符串最大长度
4. min: 2 数值最小为2
5. max: 100 数值最大为100
6. enum: ['html'**,** 'css'**,** 'javascript'**,** 'node.js']
7. trim: true 去除字符串两边的空格
8. validate: 自定义验证器
9. default: 默认值

> 获取错误信息：error.errors['字段名称'].message

### 集合关联

> 通常**不同集合的数据之间是有关系的**，例如文章信息和用户信息存储在不同集合中，但文章是某个用户发表的，要查询文章的所有信息包括发表用户，就需要用到集合关联。

- 使用id对集合进行关联

- 使用populate方法进行关联集合查询

```js
// 用户集合
const User = mongoose.model('User', new mongoose.Schema({ name: { type: String } })); 
// 文章集合
const Post = mongoose.model('Post', new mongoose.Schema({
    title: { type: String },
    // 使用ID将文章集合和作者集合进行关联
    author: { type: mongoose.Schema.Types.ObjectId, ref: 'User' }
}));
//联合查询
Post.find()
      .populate('author')
      .then((err, result) => console.log(result));

```













