## DOM 介绍

​	文档对象模型（Document Object Model，简称DOM），是 [W3C](https://baike.baidu.com/item/W3C) 组织推荐的处理[可扩展标记语言](https://baike.baidu.com/item/%E5%8F%AF%E6%89%A9%E5%B1%95%E7%BD%AE%E6%A0%87%E8%AF%AD%E8%A8%80)（html或者xhtml）的标准[编程接口](https://baike.baidu.com/item/%E7%BC%96%E7%A8%8B%E6%8E%A5%E5%8F%A3)。

​	W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式。

> DOM是W3C组织制定的一套处理 html和xml文档的规范，所有的浏览器都遵循了这套标准。

### DOM树

![1550731974575](D:\note\【27】源码+课件+软件\07-10 JavaScript网页编程\02-WebAPI编程资料\Web APIs-day01\4-笔记\images\1550731974575.png)

DOM树 又称为文档树模型，把文档映射成树形结构，通过节点对象对其处理，处理的结果可以加入到当前的页面。

- 文档：一个页面就是一个文档，DOM中使用document表示
- 节点：网页中的所有内容，在文档树中都是节点（标签、属性、文本、注释等），使用node表示
- 标签节点：网页中的所有标签，通常称为元素节点，又简称为“元素”，使用element表示



> DOM把以上内容都看作是对象

## 获取元素

### 根据ID获取

语法：`document.getElementById(id)`
作用：根据ID获取元素对象
参数：id值，区分大小写的字符串
返回值：元素对象 或 null

### 根据标签名获取元素

语法：`document.getElementsByTagName('标签名') `或者 `element.getElementsByTagName('标签名') `
作用：根据标签名获取元素对象
参数：标签名
返回值：元素对象集合（伪数组，数组元素是元素对象）



**注意：**

1. 因为得到的是一个对象的集合，所以我们想要操作里面的元素需要遍历
2. 得到的元素是动态的

> ` getElementsByTagName()`获取到是动态集合，即：当页面增加了标签，这个集合中也就增加了元素。

### H5新增获取元素方式

1. **`getElementsByClassName('类名')` 根据类名获得某些元素集合**
2. **`querySelector('选择器')`  返回指定选择器的第一个元素对象  切记 里面的选择器需要加符号 .box  #nav**
3. **`querySelectorAll('选择器')`返回指定选择器的所有元素对象集合**

> `querySelector('选择器')` 和 `querySelectorAll('选择器')`里面的选择器需要加符号`#`与`.`

### 获取特殊元素（body，html）

- 获取body元素`document.body`
- 获取html元素`document.documentElement`



## 操作元素

JavaScript的 DOM 操作可以改变网页内容、结构和样式，我们可以利用 DOM 操作元素来改变元素里面的内容、属性等。（注意：这些操作都是通过元素对象的属性实现的）

### 改变元素内容（获取或设置）

`element.innerText`

从起始位置到终止位置的内容，但它去除html标签，同时空格和换行也会去掉

`element. innerHTML`

起始位置到终止位置的全部内容，包括html标签，同时保留空格和换行



**innerText和innerHTML的区别**

- 获取内容时的区别：

​	innerText会去除空格和换行，而innerHTML会保留空格和换行	

- 设置内容时的区别：

​	innerText不会识别html，而innerHTML会识别

### 常用元素的属性操作

1. innerText、innerHTML 改变元素内容
2. src、href
3. id、alt、title

**获取属性的值**

> 元素对象.属性名

**设置属性的值**

> 元素对象.属性名 = 值



### 表单元素的属性操作

利用DOM可以操作如下表单元素的属性：

`type、value、checked、selected、disabled `

**获取属性的值**

> 元素对象.属性名

**设置属性的值**

> 元素对象.属性名 = 值
>
> 表单元素中有一些属性如：disabled、checked、selected，元素对象的这些属性的值是布尔型。



### 样式属性操作

我们可以通过 JS 修改元素的大小、颜色、位置等样式。

**常用方式**

1. element.style               行内样式操作 
2. element.className    类名样式操作 



#### 方式1：通过操作style属性

> 元素对象的style属性也是一个对象！
>
> 元素对象.style.样式属性 = 值;

**注意：**

1. JS 里面的样式采取驼峰命名法比如 fontSize， backgroundColor
2. JS 修改style 样式操作，产生的是行内样式，cSs权重比较高



#### 方式2：通过操作className属性

> 元素对象.className = 值;
>
> 因为class是关键字，所有使用className。

**注意：**

1. 如果样式修改较多，可以采取操作类名方式更改元素样式。
2. class因为是个保留字，因此使用c1assName来操作元素类名属性
3. className 会直接更改元素的类名，会要盖原先的类名。







## 自定义属性操作

### 获取属性值

- `element.属性`获取属性值。 
- `element.getAttribute（＇属性＇）`；

 **区别：**

- `element.属性`	获取内置属性值（元素本身自带的属性）
- `element.getAttribute（＇属性＇）`；主要获得自定义的属性（标准）我们程序员自定义的属性



### 设置属性值

- `element.属性＝值 `	设置内置属性值。 
- `element.setAttribute（＇属性＇，“值＇）`； 

**区别：**

- `element.属性` 设置内置属性值

- `element.setAttribute（'属性', '值'）`；主要设置自定义的属性（标准） 



###  移除属性

- `element.removeAttribute('属性') `





### H5自定义属性

自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。

自定义属性获取是通过getAttribute(‘属性’) 获取。

但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性。

H5给我们新增了自定义属性：

1. 设置H5自定义属性

   H5规定自定义属性data—开头做为属性名并且赋值。比如 ＜div data-index＝＂1＂＞＜／div＞

   或者使用JS 设置

   `element.setAttribute( 'data-index',2) `

2. 获取H5自定义属性

   兼容性获取 `element．getAttribute（ ＇data-index＇）`；

   H5新增`element．dataset．index` 或者 `element．dataset［ ＇index＇］` ie 11才开始支持

> h5新增的获取自定义属性的方法 它只能获取data-开头的
>
> dataset 是一个集合里面存放了所有以data开头的自定义属性 
>
> 如果自定义属性里面有多个-链接的单词，我们获取的时候采取 驼峰命名法



## 节点操作

### 节点概述

​	网页中的所有内容都是节点（标签、属性、文本、注释等），在DOM 中，节点使用 node 来表示。

​	HTML DOM 树中的所有节点均可通过 JavaScript 进行访问，所有 HTML 元素（节点）均可被修改，也可以创建或删除。

![1550970944363](D:\note\【27】源码+课件+软件\07-10 JavaScript网页编程\02-WebAPI编程资料\Web APIs-day02\4-笔记\images\1550970944363.png)

​	一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。

- 元素节点nodeType为1
- 属性节点nodeType为2
- 文本节点nodeType为3（文本节点包含文字、空格、换行等）

> 在实际开发中，节点操作主要操作的是元素节点



### 节点层级

​	利用 DOM 树可以把节点划分为不同的层级关系，常见的是**父子兄层级关系**。

​    ![1550971058781](D:\note\【27】源码+课件+软件\07-10 JavaScript网页编程\02-WebAPI编程资料\Web APIs-day02\4-笔记\images\1550971058781.png)

### 父级节点

`node.parentNode`

`parentNode`属性可返回某节点的父节点，注意是最近的一个父节点

如果指定的节点没有父节点则返回null

> 得到的是离元素最近的父级节点(亲爸爸) 如果找不到父节点就返回为 null



### 子节点

**所有子节点**

**`parentNode.childNodes`（标准）**

`parentNode.childNodes` 返回包含指定节点的子节点的集合，该集合为即时更新的集合。

**注意：**返回值里面包含了所有的子节点，包括元素节点，文本节点等。

如果只想要获得里面的元素节点，则需要专门处理。所以我们一般不提倡使用childNodes



**子元素节点**

`parentNode．children`（非标准） 

`parentNode.children`是一个只读属性，返回所有的子元素节点。它只返回子元素节点，其余节点不返回（这个是我们重点掌握的）。

虽然children是一个非标准，但是得到了各个浏览器的支持，因此我们可以放心使用

**第1个子节点**

`parentNode.firstChild`

`firstChild`返回第一个子节点，找不到则返回null。同样，也是包含所有的节点。

**最后1个子节点**

`parentNode.lastChild`

`lastChild`返回最后一个子节点，找不到则返回null。同样，也是包含所有的节点。 

**第1个子元素节点**

`parentNode.firstElementChild`

`firstElementChild` 返回第一个子元素节点，找不到则返回null。 



**最后1个子元素节点**

`parentNode.lastElementChild`

`lastElementchild`返回最后一个子元素节点，找不到则返回null。

 注意：这两个方法有兼容性问题，IE9以上才支持。



实际开发中，`firstChild` 和 `lastChild` 包含其他节点，操作不方便，而 `firstElementChild` 和 `lastElementChild` 又有兼容性问题

**解决方案：**

1. 如果想要第一个子元素节点，可以使用`PatentNode.children［0］`
2. 如果想要最后一个子元素节点，可以使用`RaEentNode.childNode[parentNode.shildten.length -1]`



### 兄弟节点

**下一个兄弟节点**

`node. nextSibling`
`nextsibling`返回当前元素的下一个兄弟元素节点，找不到则返回null。同样，也是包含所有的节点。

**上一个兄弟节点**

`node.previoussibling`
`previoussibling` 返回当前元素上一个兄弟元素节点，找不到则返回null。同样，也是包含所有的节点。

**下一个兄弟元素节点（有兼容性问题）**

`node.nextElementsibling`
`nextElementsibling`返回当前元素下一个兄弟元素节点，找不到则返回null。

**上一个兄弟元素节点（有兼容性问题）**

` node.previousElementsibling`
`previousElementsibling`返回当前元素上一个兄弟节点，找不到则返回null。

注意: nextEl.ementsibl.ina和pxewiousElementsibl.ing有兼容性问题， IE9 以上才支持。



### 创建节点

`document.createElement ( 'tagName ' )`

`document.createElement()`方法创建由tagName指定的HTML元素。因为这些元素原先不存在,是根据我们的需求动态生成的，所以我们也称为动态创建元素节点。

### 添加节点

1. `node.appendchild(child)`

   `node.appendchild()`方法将一个节点添加到指定父节点的子节点列表末尾。类似于css里面的after 伪元素。

2. `node.insertBefore (child，指定元素)`
   `node.insertBefore()`方法将一个节点添加到父节点的指定子节点前面。类似于css里面的 before伪元素。



###  删除节点

`node.removeChild(chind) `

`node.removeChild() `方法从 node节点中删除一个子节点，返回删除的节点。



### 复制（克隆）节点

`node.cloneNode ()`
`node.cloneNode ()`方法返回调用该方法的节点的一个副本。也称为克隆节点/拷贝节点
**注意:**

1. 如果括号参数为空或者为false，则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点。
2. 如果括号参数为true，则是深度拷贝，会复制节点本身以及里面所有的子节点。

```js
    <script>
        var ul = document.querySelector('ul');
        // 1. node.cloneNode(); 括号为空或者里面是false 浅拷贝 只复制标签不复制里面的内容
        // 2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
        var lili = ul.children[0].cloneNode(true);
        ul.appendChild(lili);
    </script>
```



### 创建元素的三种方式

- document.write ( )
- element.innerHTML
- document.createElement ()

**区别**

1. document.write是直接将内容写入页面的内容流，但是文档流执行完毕，则它会**导致页面全部重绘**
2. innerHTMT。是将内容写入某个DOM节点，不会导致页面全部重绘
3. innerHTM创建多个元素效率更高(不要拼接字符串，采取数组形式拼接)，结构稍微复杂
4. createElement( )创建多个元素效率稍低一点点，但是结构更清晰

**总结:不同浏览器下， innerHTML效率要比creatElement高**



### innerTHML和createElement效率对比

**innerHTML字符串拼接方式（效率低）**

```js
<script>
    function fn() {
        var d1 = +new Date();
        var str = '';
        for (var i = 0; i < 1000; i++) {
            document.body.innerHTML += '<div style="width:100px; height:2px; border:1px solid blue;"></div>';
        }
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```

**createElement方式（效率一般）**

```js
<script>
    function fn() {
        var d1 = +new Date();

        for (var i = 0; i < 1000; i++) {
            var div = document.createElement('div');
            div.style.width = '100px';
            div.style.height = '2px';
            div.style.border = '1px solid red';
            document.body.appendChild(div);
        }
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```

**innerHTML数组方式（效率高）**

```js
<script>
    function fn() {
        var d1 = +new Date();
        var array = [];
        for (var i = 0; i < 1000; i++) {
            array.push('<div style="width:100px; height:2px; border:1px solid blue;"></div>');
        }
        document.body.innerHTML = array.join('');
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```



## classList 属性

classList属性是HTML5新增的一个属性，返回元素的类名。但是ie10以上版本支持。

该属性用于在元素中添加，移除及切换 CSS 类。有以下方法

**添加类：**

element.classList.add（’类名’）；

```javascript
focus.classList.add('current');
```

**移除类：**

element.classList.remove（’类名’）;

```javascript
focus.classList.remove('current');
```

**切换类：**

element.classList.toggle（’类名’）;

```javascript
focus.classList.toggle('current');
```

`注意:以上方法里面，所有类名都不带点`





## DOM的核心总结

关于dom操作，我们主要针对于元素的操作。主要有创建、增、删、改、查、属性操作、事件操作。



#### 创建

1. document.write

2. innerHTML

3. createElement

  

#### 增加

1. appendChild
2.  insertBefore

#### 删

1. removeChild

#### 改

主要修改dom的元素属性，dom元素的内容、属性,表单的值等

1. 修改元素属性:src、href、title等
2. 修改普通元素内容: innerHTML.innerText
3. 修改表单元素: value、type、disabled等
4. 修改元素样式: style、className



#### 查

主要获取查询dom的元素

1. DOM提供的API方法: getElementByld、getElementsByTagName古老用法不太推荐
2. H5提供的新方法: querySelector、querySelectorAll提倡
3. 利用节点操作获取元素:父(parentNode)、子(children)、兄(previousElementSibling、nextElementSibling)提倡

  

#### 属性操作

主要针对于自定义属性。

1. setAttribute:设置dom的属性值 
2. getAttribute:得到dom的属性值
3. removeAttribute移除属性

