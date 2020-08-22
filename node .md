# 1.Node介绍

## 为什么要学习Node.js

企业需求

- 具有服务端开发经验更改
- front-end
- back-end
- 全栈开发工程师
- 基本的网站开发能力
  - 服务端
  - 前端
  - 运维部署
- 多人社区

## Node.js是什么

- Node.js是JavaScript 运行时的一个环境
- 通俗易懂的讲，Node.js是JavaScript的运行平台
- Node.js既不是语言，也不是框架，它是一个平台
- 浏览器中的JavaScript
  - EcmaScript
    - 基本语法
    - if
    - var
    - function
    - Object
    - Array
  - Bom
  - Dom
- Node.js中的JavaScript
  - 没有Bom，Dom
  - EcmaScript
  - 在Node中这个JavaScript执行环境为JavaScript提供了一些服务器级别的API
    - 例如文件的读写
    - 网络服务的构建
    - 网络通信
    - http服务器
- 构建与Chrome的V8引擎之上
  - 代码只是具有特定格式的字符串
  - 引擎可以认识它，帮你解析和执行
  - Google Chrome的V8引擎是目前公认的解析执行JavaScript代码最快的
  - Node.js的作者把Google Chrome中的V8引擎移植出来，开发了一个独立的JavaScript运行时环境
- Node.js uses an envent-driven,non-blocking I/O mode that makes it lightweight and efficent.
  - envent-driven 事件驱动
  - non-blocking I/O mode 非阻塞I/O模型（异步）
  - ightweight and efficent. 轻量和高效
- Node.js package ecosystem,npm,is the larget scosystem of open sourcr libraries in the world
  - npm 是世界上最大的开源生态系统
  - 绝大多数JavaScript相关的包都存放在npm上，这样做的目的是为了让开发人员更方便的去下载使用
  - npm install jquery

## Node能做什么

- web服务器后台
- 命令行工具
  - npm(node)
  - git(c语言)
  - hexo（node）
  - ...
- 对于前端工程师来讲，接触最多的是它的命令行工具
  - 自己写的很少，主要是用别人第三方的
  - webpack
  - gulp
  - npm

# 2.起步

## 安装Node环境

- 查看Node环境的版本号
- 下载：https://nodejs.org/en/
- 安装：
  - 傻瓜式安装，一路`next`
  - 安装过再次安装会升级
- 确认Node环境是否安装成功
  - 查看node的版本号：`node --version`
  - 或者`node -v`
- 配置环境变量



## 解析执行JavaScript

1. 创建编写JavaScript脚本文件
2. 打开终端，定位脚本文件的所属目录
3. 输入`node 文件名`执行对应的文件

注意：文件名不要用`node.js`来命名，也就是说除了`node`这个名字随便起，最好不要使用中文。

## 文件的读写

文件读取:

```
//浏览器中的JavaScript是没有文件操作能力的
//但是Node中的JavaScript具有文件操作能力
//fs是file-system的简写，就是文件系统的意思
//在Node中如果想要进行文件的操作就必须引用fs这个核心模块
//在fs这个和兴模块中，就提供了人所有文件操作相关的API
//例如 fs.readFile就是用来读取文件的

//  1.使用fs核心模块
var fs = require('fs');

// 2.读取文件
fs.readFile('./data/a.txt',function(err,data){
   if(err){
        console.log('文件读取失败');
   }
    else{
         console.log(data.toString());
    }
})
```

文件写入：

```
//  1.使用fs核心模块
var fs = require('fs');

// 2.将数据写入文件
fs.writeFile('./data/a.txt','我是文件写入的信息',function(err,data){
   if(err){
        console.log('文件写入失败');
   }
    else{
         console.log(data.toString());
    }
})
```

### http

服务器：

```
// 1.加载http核心模块
var http = require('http');

// 2.使用http.createServer()创建一个web服务器
var server = http.createServer();

// 3.服务器要做的事儿
// 提供服务：对数据服务
// 发请求
//	接收请求
//	处理请求
//	反馈（发送响应）
//	当客户端请求过来，就会自动触发服务器的request请求事件，然后执行第二个参数：回调处理函数
server.on('request',function(){
    console.log('收到客户的请求了')
})

// 4.绑定端口号，启动服务
server.listen(3000,function(){
    console.log('runing...')
})
```

# 3.Node中的JavaScript

### 3.1.EcmaSccript

- EcmaScript语言
  - 和浏览器一样，在Node中没有Bom和Dom
- 核心模块
  - 文件操作的fs
  - http服务操作的http
  - url路径操作模块
  - path路径处理模块
  - os操作系统信息
- 第三方模块
  - art-template
  - 必须通过npm来下载才可以使用
- 自己写的模块
  - 自己创建的文件

### 3.2核心模块

Node为JavaScript提供了很多服务器级别的API，这些API绝大多数都被包装到了一个具名的核心模块中了。例如文件操作的`fs ` 核心模块，http服务构建的`http` 模块，`path` 路径操作模块、`os ` 操作系统信息模块。。。



核心模块：

```javascript
var fs = require('fs')
var http = require('http')
```

### 3.3.用户自定义模块

- require
- exports

### 3.4. 第三方模块

# 4.Web服务器

### 4.1. ip地址和端口号

- ip地址用来定位计算机
- 端口号用来定位具体的应用程序
- 一切需要联网通信的软件都会占用一个端口号
- 端口号的范围从0-65536之间
- 在计算机中有一些默认的端口号，最好不要去使用
  - 例如http服务的80
- 我们在开发过程中使用一些简单好记的就可以了，例如3000、5000等没有什么含义。
- 可以同时开启多个服务，但一定要确保不同服务占用的端口号不一致才可以。

### 4.2. Content-Type

###  http://tool.oschina.net/

### 4.3.  请求对象Request

### 4.4. 响应对象 Response

### 4.5. 在Node中使用模板引擎

### 4.6. 统一处理静态资源

### 4.8. 服务端渲染

# 5.留言板

# 6.Node 中的模块系统

使用Node 编写应用程序主要就是在使用：

- EcmaScript语言
  - 和浏览器不一样，在Node中没有BOM、DOM
- 核心模块
  - 文件操作的fs
  - http服务的http
  - url路径操作模块
  - path路径处理模块
  - os操作系统信息
- 第三方模块
  - art-template
- 自己写的模块
  - 自己创建的文件

## 6.1. 模块化

### 6.1.1. 什么是模块化

- 文件作用域
- 通信规则
  - 加载require
  - 导出



### 6.1.2 CommonJS模块规范

在Node中的JavaScript还有一个很重要的概念： 模块系统

- 模块作用域
- 使用require方法用来加载模块
- 使用exports接口对象用来导出模块中的成员

## 6.2. require

### 6.2.1. 加载require

语法：

```javascript
var 自定义变量名称 = require('模块')
```

两个作用：

- 执行被加载模块中的代码
- 得到被加载模块中的`exports ` 导出接口对象



- Node 中是模块作用域，默认文件中所有的成员只在当前文件模块有效
- 对于希望可以被其它模块访问的成员，我们就需要把这些公开的成员都挂载到  `exports` 接口对象中就可以了

导出多个成员（必须在对象中）：

```javascript
exports.a = 123
exports.b = 'hello'
exports.c = function () {
    console.log('ccc')
}
exports.d = {
	foo: 'bar'
}
```

导出单个成员（拿到的就是：函数、字符串）：

```javascript
module.exports = 'hello'
```

以下情况会覆盖：

```javascript
module.exports = 'hello'

// 以这个为准，后者会覆盖前者
module.exports = function (x, y) {
    return x + y
}
```

也可以这样来导出多个成员：

```javascript
module.exports = {
    add: function () {
        return x + y
    },
    str: 'hello'
}
```

### 6.2.3. 原理解析

exports 和 ` module.exports` 的一个引用：

```javascript
console.log(exports === module.exports)  // = > true

exports.foo = 'bar'

//等价于
module.exports.foo = 'bar'
//reture module.exports
```



### 6.2.4. exports 和module.exports 的区别：

![image-20200616181156739](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200616181156739.png)



### 6.2.5. require 加载规则

```html
<a href = '#'>深入浅出Node.js(三): 深入Node.js的模块机制</a>
```

如果想要了解更多底层细节，可以自行参考：《深入浅出Node.js》中的模块系统章节

- 核心模块
  - 模块名
- 第三方模块
  - 模块名
- 用户自己写的
  - 路径

```JavaScript
blog
	a
    	node_modules
        	art-template
	b
    	../a/foo.js
		a 中的第三方包是不能通过 require('art-template') 方式来加载
        require('../a/node_modules/art-template/index.js')
```



- 优先从缓存加载
- 判断模块标识
  - 核心模块
  - 第三方模块
  - 自己写的模块

```JavaScript
// 如果是非路径形式的模块标识
// 路径形式的模块：
//  ./ 当前目录，不可省略
//  ../ 上一级目录，不可省略
//  /xxx 几乎不用
//  d:/a/foo.js 几乎不用
//  首位的 / 在这里表示的是当前文件模块所属磁盘根路径
//  .js 后缀名可以省略
// require('./foo.js')

// 核心模块的本质也是文件
// 核心模块文件已经被编译到了二进制文件中了，我们只需要按照名字来加载就可以了
// require('fs')
// require('http')

// 第三方模块
// 凡是第三方模块都必须通过 npm 来下载
// 使用的时候就可以通过 require('包名') 的方式来进行加载才可以使用
// 不可能有任何一个第三方包和核心模块的名字是一样的
// 既不是核心模块、也不是路径形式的模块
//    先找到当前文件所处目录中的 node_modules 目录
//    node_modules/art-template
//    node_modules/art-template/package.json 文件
//    node_modules/art-template/package.json 文件中的 main 属性
//    main 属性中就记录了 art-template 的入口模块
//    然后加载使用这个第三方包
//    实际上最终加载的还是文件

//    如果 package.json 文件不存在或者 main 指定的入口模块是也没有
//    则 node 会自动找该目录下的 index.js
//    也就是说 index.js 会作为一个默认备选项
//    
//    如果以上所有任何一个条件都不成立，则会进入上一级目录中的 node_modules 目录查找
//    如果上一级还没有，则继续往上上一级查找
//    。。。
//    如果直到当前磁盘根目录还找不到，最后报错：
//      can not find module xxx
// var template = require('art-template')
// 
// 注意：我们一个项目有且只有一个 node_modules，放在项目根目录中，这样的话项目中所有的子目录中的代码都可以加载到第三方包
// 不会出现有多个 node_modules
// 模块查找机制
//    优先从缓存加载
//    核心模块
//    路径形式的文件模块
//    第三方模块
//      node_modules/art-template/
//      node_modules/art-template/package.json
//      node_modules/art-template/package.json main
//      index.js 备选项
//      进入上一级目录找 node_modules
//      按照这个规则依次往上找，直到磁盘根目录还找不到，最后报错：Can not find moudle xxx
//    一个项目有且仅有一个 node_modules 而且是存放到项目的根目录

require('a')
```



## 6.3. npm

- node package manager：  node 包 管理

### 6.3.1. npm 网站

```html
npmjs.com
```

### 6.3.2. npm 命令行工具

npm的第二层含义就是一个命令行工具，只要你安装了node就已经安装了npm。

npm 也有版本这个概念。

可以通过在命令行中输入：

```javacript
npm --version
```

升级 npm：

```javascript
npm install --global npm
```

### 6.3.3. 常用命令

- npm init
  - npm init --yes 可以跳过向导，快速生成
- npm install 
  - 一次性把dependencies 选项中的依赖项全部安装
  - npm i
- npm install 包名
  - 只下载
  - npm i 包名
- npm install --save 包名
  - 下载并保存依赖项（package.json 文件中的 dependencies 选项）
  - npm i -S 包名
- npm uninstall 包名
  - 只删除，如果有依赖项会依然保存
  - npm un
- npm uninstall --save 包名
  - 删除的同时也会把依赖项信息也去除
  - npm un --S 包名
- npm help
  - 查看使用帮助
- npm 命令 -- help
  - 查看指定命令的使用帮助
  - 例如我忘记了 uninstall 命令的简写了，这个时候，可以输入 `npm uninstall --help` 来查看使用帮助

### 6.3.4. 解决 npm 被墙问题

npm 存储包文件的服务器在国外，有时候会被墙，速度很慢，所以我们需要解决这个问题。

https://developer.aliyun.com/mirror/NPM?from=tnpm淘宝的开发团队把 npm 在国内做了一个备份。

安装淘宝的 cnpm:

```shell
# 在任意目录执行都可以
# --global 表示安装到全局，而非当前目录
# --global 不能省略，否则不管用
npm install --global cnpm
```

在接下来你安装包的时候把之前的` npm` 替换成 `cnpm`

举个例子：

```shell
# 这里还是走国外的 npm 服务器，速度比较慢
npm install jquery

# 使用 cnpm 就会通过淘宝的服务器来下载 jquery
cnpm install jquery
```

如果不想安装 `cnpm` 又想使用淘宝的服务器来下载：

```shell
npm install jquery --registry=https://registry.npm.taobao.org
```

但是每一次手动这样加参数很麻烦，所以我们可以把这个选项加入配置文件中：

```shell
npm config set registry https://registry.npm.taobao.org

# 查看 npm 配置信息
npm config list
```



## 6.4. package.json

我们建议每一个项目都要有一个` package.json `  文件（包描述文件，就像产品的说明书一样），给人踏实个感觉。

这个文件可以通过 ` npm init`  的方式来自动初始化出来。

```javascript
{
  "name": "npm-demo",
  "version": "0.0.1",
  "description": "这是一个测试项目",
  "main": "main.js",
  "dependencies": {
    "jQuery": "^1.8.4"
  },
  "devDependencies": {},
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "lipengzhou",
  "license": "ISC"
}
```

对于咱们目前来讲，最有用的是那个`dependencies` 选项，可以用来帮我们保存第三方包的依赖信息。

如果你的`node_modules` 删除了也不用担心，我们只需要：`npm install` 就会自动把`package.json` 中的`dependencies` 中所有的依赖项都下载回来。

- 建议每个项目的根目录下都有一个 `package.json` 文件
- 建议执行`npm install` 包名的时候都加上 `--save` 这个选项，母的是用来保存依赖信息。

### 6.4.1. package.json 和 package-lock.json

npm 5 以前是不会有`package-lock.json` 这个文件的。

npm 5 以后才加入了这个文件。

当你安装包的时候， npm 都会生成或者更新 `package-lock.json` 这个文件。

- npm 5 以后的版本安装包不需要加`--save` 参数，它会自动保存依赖信息
- 当你安装包的时候，会自动创建或者是更新`package-lock.json`这个文件
- `package-lock.json` 这个文件会保存`node_modules` 中所有包的信息（版本、下载地址）
  - 这样的话重新`npm install` 的时候速度就可以提升
- 从文件来看，有一个`lock` 称之为锁
  - 这个`lock` 是用来锁定版本的
  - 如果项目依赖了`1.1.1` 版本
  - 如果你重新 install 其实会下载最新版本，而不是 1.1.1
  - 我们的目的就是希望可以锁住 1.1.1 这个版本
  - 所以这个`package-lock.json` 这个文件的另外一个作用就是锁定版本号，防止自动升级新版

# 7. path 路径操作模块

文档地址：https://nodejs.org/dist/latest-v8.x/docs/api/path.html

- path.basename
  - 获取一个路径的文件名（默认包含扩展名）
  - ![image-20200702155852709](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702155852709.png)
- path.dirname
  - 获取一个路径中的目录部分
  - ![image-20200702155911479](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702155911479.png)
- path.extname
  - 获取一个路径中的扩展名部分
  - ![image-20200702155937405](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702155937405.png)
- path.parse
  - 把一个路径转换为对象
  - ![image-20200702160117356](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702160117356.png)
    - root 根目录
    - dir 目录
    - base 包含后缀名的文件名
    - name 不包含后缀名的文件
- path.join
  - ![image-20200702160203125](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702160203125.png)
  - 当你需要进行路径拼接的时候，推荐使用这个方法
- path.isAbsolute 判断一个路径是否是绝对路径
  - ![image-20200702160014227](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200702160014227.png)

# 8. Node 中其它成员

在每个模块中，出了`require` 、`exports` 等模块相关 API 之外，还有两个特殊的成员：

- `__dirname` 动态获取  可以用来获取当前文件模块所属目录的绝对路径
- `__filename` 动态获取 可以用来获取当前文件的绝对路径
- `__dirname` 和 `__filename` 是不受执行 node 命令所属路径影响的

在文件操作中，使用相对路径是不可靠的，因为在 Node 中文件操作的路径被设计为相对于执行 node 命令所处的路径（不是 bug，人家这样设计是有使用场景）。

所以为了解决这个问题，很简单，只需要把相对路径变为绝对路径就可以了

那这里我们就可以使用 `__dirname` 或者 `__filename` 来帮我们解决这个问题了。

在拼接路径的过程中，为了避免手动拼接带来的一些低级错误，所以推荐多使用：`path.join()` 来辅助拼接。

所以为了尽量避免刚才所描述的这个问题，大家以后在文件操作中使用的相对路径转换为 **动态的绝对路径。**

```
补充：模块中的路径标识和这里的路径没有关系，不受影响（相对于文件模块）
```



# 9. Express

原生的http在某些方面表现不足以应对我们的开发需求，所以我们就需要使用框架来加快我们的开发效率，框架的目的就是提高效率，让我们的代码更高度统一。

在Node中，有很多Web开发框架，我们这里以学习`express` 为主。

### 9.1.1 安装：

``` shell
npm install --save express
```

### 9.1.2 hello world

```javascript
const express = require('express')
const app = express()

app.get('/',(req,res) => res.send('hello world!'))

app.listen(3000,())
```

### 9.1.3. 基本路由：

路由器

get：

```javascript
// 当你以GET 方法请求 / 的时候，执行对应的处理函数
app.get('/',function (req, res) {
    res.send('hello world!')
})
```

post:

```javascript
// 当你以POST 方法请求 / 的时候，执行对应的处理函数
app.post('/',function (req, res) {
    res.send('Gpt a POST request')
})
```

### 9.1.4. 静态服务

```javascript
// /public资源   开放public目录，直接访问public下的资源
app.use(express.static('./public'))

// /files资源
app.use(express.static('./files'))

// /public/xxx
app.use('/public/', express.static('./public/'))

// /public/xxx
app.use('/public/', express.static('./public/'))

app.use('static', express.static(path.join(_dirname, 'public')))
```



## 9.2. 在 Express 中配置使用 `art-template` 模板引擎

- [art-template - GitHub 仓库](https://github.com/aui/art-template)
- [art-template 官方文档](https://aui.github.io/art-template/)

安装：

```
npm install --save art-templatenpm
npm install --save express-art-template
```

配置：

```java
// 配置使用 art-template 模板引擎
// 第一个参数，表示，当渲染以 .art 结尾的文件的时候，使用 art-template 模板引擎
// express-art-template 是专门用来在 Express 中把 art-template 整合到 Express 中
// 虽然外面这里不需要记载 art-template 但是也必须安装
// 原因就在于 express-art-template 依赖了 art-template
app.engine('html', require('express-art-template'));
```

使用:

```javascript
// Express 为 Response 相应对象提供了一个方法：render
// render 方法默认是不可以使用，但是如果配置了模板引擎就可以使用了
// res.render('html模板名', {模板数据})
// 第一个参数不能写路径，默认会去项目中的 views 目录查找该模板文件
// 也就是说 Express 有一个约定：开发人员把所有的视图文件都放到 views 目录中
app.get('/', function (req, res) {
    res.render('index.html', {
        title: 'hello world'
    });
});
```

如果希望修改默认的`views` 视图渲染存储目录，可以：

```javascript
// 如果想要修改默认的 views 目录，则可以
app.set('views', render函数的默认路径)
```

## 9.3. 在 Express 中获取表单 GET 请求参数

Express 内置了一个 API ,可以直接通过 `req.query` 来获取

```shell
req.query
```



## 9.4. 在 Express 获取表单 POST 请求体数据

在 Express 中没有内置获取表单 POST 请求体的 API , 这里我们需要啊使用一个第三方包：`body-parser` 。

安装：

```shell
npm install body-parser
```

配置：

```javascript
var express = require('express')
var bodyParser = require('body-parser')

var app = express()
// 配置 body-parser
// 只要加入这个配置， 则在req 请求对象上会多出来一个属性：body
// 也就是说您就可以这通过 req.body 来获取表单 POST 请求体数据了
// parse application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: false }))

// parse application/json
app.use(bodyParser.json())

app.use(function (req, res) {
  res.setHeader('Content-Type', 'text/plain')
  res.write('you posted:\n')
    // 也就是说您就可以这通过 req.body 来获取表单 POST 请求体数据了
  res.end(JSON.stringify(req.body, null, 2))
})
```

## 9.6. 在 Express 配置使用 `expresss-sessin` 插件

安装：

```shell
npm install express-session
```

配置：

```javascript
// 该插件会为 req 请求对象添加一个成员： req.session 默认是一个对象
// 这是最简单的配置方式，暂且先不关心里面参数的含义
app.use(session({
    // 配置加密字符串，它会在原有加密基础之上和这个字符串拼起来去加密
    // 目的是为了增加安全性，防止客户端恶意伪造
    secret: 'itcast',
    resave: false,
    saveUninitialized: false // 无论你是否使用 Session ，我都默认直接给你分配一把钥匙
}))
```

使用：

```javascript
// 添加 Session 数据
req.session.foo = 'bar'

//获取 Session 数据
req.session.foo
```

提示：默认 Session 数据是内存存储的，服务器一旦重启就会丢失，真正的生产环境会把 Session 进行持久化存储。

## 9.5. CRUD 案例

### 9.5.1. 模块化思想

模块如何划分：

- 模块职责要单一

### 9.5.1.  起步

- 初始化
- 安装依赖
- 模板处理

### 9.5.2. 路由设计

![image-20200622192008190](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200622192008190.png)

### 9.5.3. 提取路由模块

router.js:

```javascript
/**
 * router.js 路由模块
 * 职责：
 *   处理路由
 *   根据不同的请求方法+请求路径设置具体的请求处理函数
 * 模块职责要单一，不要乱写
 * 我们划分模块的目的就是为了增强项目代码的可维护性
 * 提升开发效率
 */
// 专门用来包装路由的
var express = require('express')

// 1. 创建一个路由容器
var router = express.Router()
    router.get('/students', function (req, res) {
        
    })
var router = express.Router()
    router.get('/students/new', function (req, res) {
        
    })
var router = express.Router()
    router.post('/students/new', function (req, res) {
        
    })
var router = express.Router()
    router.get('/students/edit', function (req, res) {
        
    })
var router = express.Router()
    router.post('/students/edit', function (req, res){
        
    })

// 3.把 router 导出
module.exports = router
```

app.js

```javascript
var router = require('./router')

// 挂载路由
app.use(router)
```

### 9.5.4. 设计操作数据的 API 文件模块

```javascript
/**
 * student.js
 * 数据操作文件模块
 * 职责：操作文件中的数据，只处理数据，不关心业务
 *
 * 这里才是我们学习 Node 的精华部分：奥义之所在
 * 封装异步 API
 */

/**
 * 获取学生列表
 */
exports.find = function() {

}

/**
 * 添加保存学生
 */
exports.save = function() {

}

/**
 * 更新学生
 */
exports.update = function() {

}

/**
 * 删除学生
 */
exports.delete = function() {

}
```

### 9.5.5. 自己编写的步骤

- 处理模板
- 配置开放静态资源
- 配置模板引擎
- 简单路由：/students 渲染静态页出来
- 路由设计
- 提取路由模块
- 由于接下来一系列的业务操作都需要处理文件数据，所以我们需要封装 student.js
- 先写好 student.js 文件结构
  - 查询所有学生列表的 API find
  - findById
  - updateById
  - deleteById
- 实现具体功能
  - 通过路由收到请求
  - 接收请求中的数据（get、post）
    - req.query
    - req.body
  - 调用数据操作 API 处理数据
  - 根据操作结果给客户端发送响应
- 业务功能顺序
  - 列表
  - 添加
  - 编辑
- find
- findIndex

# 10. MongoDB

## 10.1. 关系型数据库和非关系型数据库

表就是关系

或者说表与表之间存在关系

- 所有的关系型数据库都需要通过`sql` 语言来操作
- 所有的关系型数据库在操作之前都需要设计表结构
- 而且数据表还支持约束
  - 唯一的
  - 主键约束
  - 默认值
  - 非空
- 非空系型数据库非常灵活
- 有的非关系型数据库就是 key-value 对儿
- 但是 MongoDB 是长的最像关系型数据库的非关系型数据库
  - 数据库 - > 数据库
  - 数据表 -> 集合（数组）
  - 表记录 ->（文档对象）
- MongoDB 不需要设计表结构
- 也就是说你可以任意的往里面存数据，没有结构性这么一说

## 10.2. 安装

- 64位下载地址：
- 下载
- 安装
- 配置环境变量
- 最后输入`mongod --version` 测试是否安装成功
- ![image-20200626215400151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200626215400151.png)

## 10.3. 启动和关闭数据库

启动：

```shell
 # mongodb 默认使用执行 mongod 命令所处盘符根目录下的 /data/db 作为自己的数据库存储目录
 # 所以在第一次执行该命令之前先自己手动新建一个 /data/db
 mongod
```

如果想要修改默认的数据存储目录，可以：

```shell
mongod --dbpath=数据存储目录路径
```

停止：

```shell
在开启服务的控制台，直接 ctrl+c 即可停止
或者直接关闭开启服务的控制台也可以
```

## 10.4. 连接和退出数据库

连接：

```shell
# 该命令默认连接本机的 MongoDB 服务
mongo
```

退出：

```shell
# 在连接状态输入 exit 退出连接
exit
```

## 10.5. 基本命令

- `show dbs`
  - 查看显示所有数据库
  - ![image-20200627154238402](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200627154238402.png)
- `db`
  - 查看当前操作的数据库
- `ues 数据库名称`
  - 切换到指定的数据库（如果没有会新建）
- 插入数据
  - ![image-20200705111404385](C:\Users\陈奕山\AppData\Roaming\Typora\typora-user-images\image-20200705111404385.png)
- 查询数据
  - ![image-20200627154418885](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200627154418885.png)

## 10.6. 在 Node 中如何操作 MongoDB 数据

### 10.6.1. 使用官方的`mongodb` 包来操作

https://www.npmjs.com/package/mongodb

### 10.6.2.  使用第三方 mongoose 来操作 MongoDB 数据库

第三方包： `mongoose` 基于 MongoDB 官方的 `mongodb` 包再一次做了封装。

- 网址：https://mongoosejs.com/

## 11.mongoose

- 官网：https://mongoosejs.com/
- 官方指南：https://mongoosejs.com/docs/guide.html
- 官方 API 文档：https://mongoosejs.com/docs/api.html

### 11.1.MongoDB 数据库的基本概念

- 可以有多个数据库
- 一个数据库中可以有多个集合（表）
- 一个集合中可以哟多个文档（表记录）
- 文档结构很灵活，没有任何限制
- MongoDB 非常灵活，不需要像 MySQL 一样先创建数据库、表、设计表结构
  - 在这里只需要：当你需要插入数据的时候，只需要指定往哪个数据库的哪个集合操作就可以了
  - 一切都由 MongoDB 来帮你自动完成建库表这件事

```javascript
{
    qq:{
        users:[
            {name:'张三',age: 15},
            {name:'李四',age: 15},
            {name:'王五',age: 15},
        ]，
        products:[
            
        ],
    }
      taobao:{
	}
}
```

### 11.2.起步

安装：

```shell
npm install mongoose
```

hello world:

```javascript
var mongoose = require('mongoose');

// 连接 MongoDB 数据库
mongoose.connect('mongodb://localhost/test', { useMongoClient: true });

mongoose.Promise = global.Promise;

// 创建一个模型
// 就是在设计数据库
// MongoDB 是动态的，非常灵活，只需要在代码中设计你的数据库就可以了
// mongoose 这个包就可以让你的设计编写过程变的非常的简单
var Cat = mongoose.model('Cat', { name: String });
  // 实例化一个 Cat
  var kitty = new Cat({ name: '喵喵' + i });
  // 持久化保存 kitty 实例
  kitty.save(function (err) {
    if (err) {
      console.log(err);
    } else {
      console.log('meow');
    }
  }); 
```

### 11.3.官方指南

#### 11.3.1. 设计 Scheme 发布 Model

```javascript
var mongoose = require('mongoose')

var Schema = mongoose.Schema

// 1. 连接数据库
// 指定连接的数据库不需要存在，当你插入第一条数据之后就会自动被创建出来
mongoose.connect('mongodb://localhost/itcast')

// 2. 设计文档结构（表结构）
// 字段名称就是表结构中的属性名称
// 约束的目的是为了保证数据的完整性，不要有脏数据
var userSchema = new Schema({
    username: {
        type: String,
        required: true // 必须有
    },
    password: {
        type: String,
        required: true
    },
    email: {
        type: String
    }
})
// 3. 将文档结构发布为模型
//    mongoose.model 方法就是用来将一个架构发布为 model
//    第一个参数：传入一个大写名词单数字符串用来表示你的数据库名称
//                 mongoose 会自动将大写名词的字符串生成 小写复数 的集合名称
//                 例如这里的 User 最终会变为 users 集合名称
//    第二个参数：架构 Schema
//   
//    返回值：模型构造函数
var User = mongoose.model('User', userSchema)
// 4. 当我们有了模型构造函数之后，就可以使用这个构造函数对 users 集合中的数据为所欲为了（增删改查）
```

#### 11.3.2. 增加数据

```javascript
var admin = new User({
    username: 'zs',
    password: '123456',
    email: 'admin@admin.com'
})

admin.save(function(err, ret) {
        if (err) {
            console.log('保存失败')
        } else {
            console.log('保存成功')
            console.log(ret)
        }
    })
```

#### 11.3.3. 查询

查询所有：

```javascript
User.find(function(err, ret) {
    if (err) {
        console.log('查询失败')
    } else {
        console.log(ret)
    }
})
```

按条件查询所有：

```javascript
// User.find({条件},function(err,ret) {})
User.find({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('查询失败')
  } else {
    console.log(ret)
  }
})
```

按条件查询单个：

```javascript
User.findOne({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('查询失败')
  } else {
    console.log(ret)
  }
})
```

#### 11.3.4. 删除数据

根据条件删除所有：

```javascript
User.remove({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('删除失败')
  } else {
    console.log('删除成功')
    console.log(ret)
  }
})
```

根据条件删除一个：

```javascript
Model.findOneAndRemove(conditions, [options],[callback])
```

根据 id 删除一个：

```javascript
Model.findByIdAndRemove(id, [options], [callback])
```

根据条件更新所有：

```javascript
Model.update(conditions, doc, [options], [callback])
```

根据指定条件更新一个：

```javascript
Model.findOneAndUpdate([conditions], [update],[options],[callback])
```

根据 id 更新一个：

```javascript
User.findByIdAndUpdate('5a001b23d219eb00c8581184', {
  password: '123'
}, function (err, ret) {
  if (err) {
    console.log('更新失败')
  } else {
    console.log('更新成功')
  }
})
```





# 12. 异步编程

## 12.1. 回调函数

不成立情况：

```javascript
function add(x, y) {
  console.log(1)
  setTimeout(function () {
    console.log(2)
    var ret = x + y
    return ret
  }, 1000)
    console.log(3)
    // 到这里执行就结束了，不会等到前面的定时器，所以直接就返回了默认值 undefined
}

console.log(add(10,20)) // -> undefined

```

不成立情况：

```javascript
function add(x, y) {
  var ret
  console.log(1)
  setTimeout(function () {
    console.log(2)
    var ret = x + y
  }, 1000)
    console.log(3)
    return ret
}

console.log(add(10,20)) // -> undefined
```

回调函数：

```javascript

function add(x, y, callback) {
    // callback 就是回调函数
    // var x = 10
    // var y = 20
    // var callback = function (ret) { console.log(ret)}
  console.log(1)
  setTimeout(function () {
    var ret = x + y
    callback(ret)
  }, 1000)
}

add(10, 20, function (ret) {
  // 我现在拿到这个结果可以做任何操作
})
```

基于原生 XMLHTTPRequest 封装 get 方法

```javascript
    function get(url, callback) {
      var oReq = new XMLHttpRequest()
      // 当请求加载成功之后要调用指定的函数
      oReq.onload = function () {
        // 我现在需要得到这里的 oReq.responseText
        callback(oReq.responseText)
      }
      oReq.open("get", url, true)
      oReq.send()
    }

    get('data.json', function (data) {
      console.log(data)
    })
```

## 12.2. Promise

无法保证代码顺序：

```javascript
var fs = require('fs')

fs.readFile('./data/a.txt', 'utf8', function(err, data) {
    if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
    }
    console.log(data)
})

fs.readFile('./data/b.txt', 'utf8', function(err, data) {
    if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
    }
    console.log(data)
})

fs.readFile('./data/c.txt', 'utf8', function(err, data) {
    if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
    }
    console.log(data)
})
```



通过回调嵌套的方式来保证顺序：

```javascript
var fs = require('fs')

fs.readFile('./data/a.txt', 'utf8', function (err, data) {
  if (err) {
    // return console.log('读取失败')
    // 抛出异常
    //    1. 阻止程序的执行
    //    2. 把错误消息打印到控制台
    throw err
  }
  console.log(data)
  fs.readFile('./data/b.txt', 'utf8', function (err, data) {
    if (err) {
      // return console.log('读取失败')
      // 抛出异常
      //    1. 阻止程序的执行
      //    2. 把错误消息打印到控制台
      throw err
    }
    console.log(data)
    fs.readFile('./data/c.txt', 'utf8', function (err, data) {
      if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
      }
      console.log(data)
    })
  })
})
```

为了解决上述编码方式带来的问题（回调地狱嵌套），所以在EcmaScript 6 中新增了一个API: `promise`

- Promise 的英文就是承诺、保证的意思（I promise you）
- Promise 是一个容器，存放了一个异步任务
- Promise 本身不是异步，但是内部往往都是封装一个异步任务

# 13. 其它

## 13.1. 代码风格

- Airbnb javaScript Style
  - 更专业规范，比较严谨
- JavaScript Standard Style
  - 符合大多数人的习惯

规范只是建议，可以遵守也可以不遵守，在一些比较专业的团队中，对于代码风格会有对应的风格校验工具，如果你的代码风格有问题，例如少了一个空格或者多了一个空格，你的代码都是不允许提交的。

后面会学习如何使用工具来强制校验代码风格的问题。

### 13.1.1 代码风格无分号问题

无论你是否使用的是无分号的代码风格规范，都建议当一行代码是以：

- `(`
- `[`
- `

以上三者开头的时候，最好都在其之前补上一个分号。

例如：

```javascript
;(function(){
    //code here
})
```

## 13.2. 解决代码写完自动重启服务器问题

我们这里可以使用一个第三方命令行工具：`nodemon` 来帮我们解决频繁修改代码重启服务器问题。

`nodemon` 是一个基于 Node.js 开发的一个第三方命令行工具，我们使用的时候需要独立安装：

```shell
# 在任意目录执行该命令都可以
# 也就是说，所有需要 --global 来安装的包都可以在任意目录执行
npm install --global nodemon
```

安装完毕之后，使用：

```shell
node app.js

# 使用 nodemon
nodemon app.js
```

只要是通过 `nodemon app.js` 启动的服务，则它会监视你的文件变化，当文件发送变化的时候，会自动帮你重启服务器。

## 13.3. 文件操作路径和模块路径

文件操作路径：

```JavaScript
// 在文件操作的相对路径中
//    ./data/a.txt 相对于当前目录
//    data/a.txt   相对于当前目录
//    /data/a.txt  绝对路径，当前文件模块所处磁盘根目录
//    c:/xx/xx...  绝对路径
// fs.readFile('./data/a.txt', function (err, data) {
//   if (err) {
//     console.log(err)
//     return console.log('读取失败')
//   }
//   console.log(data.toString())
// })
```

模块操作路径：

```javascript
// 这里如果忽略了 . 则也是磁盘根目录
require('/data/foo.js')

// 相对路径
require('./data/foo.js')

// 模块加载的路径中的相对路径不能省略
```



