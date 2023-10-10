## Buffer

### 1. 概念

* Buffer是一个类似于数组的<font color=red>对象</font>,用于表示固定长度的字节序列
* Buffer本质是一段内存空间，专门用来处理<font color=red>二进制数据</font>

### 2. 特点

* Buffer大小固定且无法调整
* Buffer性能较好，可以直接对计算机内存进行操作
* 每个元素的大小为1字节（byte）

### 3. 使用

* 创建

```js
//1.alloc
let buf = Buffer.alloc(10);
//创建一个10字节的Buffer
//打印buf
console.log(buf);
//每一个二进制位都会归零

//2.allocUnsafe
let buf = Buffer.allocUnsafe(10);
//打印buf
console.log(buf);
//可能会包含旧的内存数据，即创建前不归零
//优点 速度更快

//3.from
let buf = Buffer.from("Hello");
let buf = Buffer.from([100,105,2305,453]);
//打印buf
console.log(buf)
//将一个字符串或数组转化为Buffer
```

* Buffer 与字符串的转换

```js
//Buffer 与字符串的转换
let buf = Buffer.from([105,108,111,118,101,121,111,117]);
console.log(buf,toString());
```

* Buffer的读写

```js
//读取
console.log(buf[1]);
//读取Buffer中位置为1的元素

//修改
buf[1] = 97;
//如果修改的数值超过255，则超过8位的数据会被舍弃

//查看字符输出结果
console.log(buf[0].toString());
//[]中可以省略，[]中的数字表示当中位置的元素
```

## fs模块

fs全称为==file system==，称之为==文件系统==，是Node.js中的==内置模块==，可以对计算机中的磁盘进行操作

功能

实现与硬盘的交互，文件内容的写入、读取以及文件夹的相关操作

### 1. 文件写入

| 方法                      | 说明     |
| ------------------------- | -------- |
| writeFile                 | 同步写入 |
| writeFileSync             | 异步写入 |
| appendFile/appendFileSync | 追加写入 |
| createwriteStream         | 流式写入 |

#### writeFile异步写入

语法：==fs.writeFile(filedata[,options],callback);==

参数说明：

* file 文件名
* data 待写入的数据
* options 选项设置（可选）
* callback 写入回调

返回值：==undefined==

```js
//1.导入fs模块
const fs = require('fs');

//2.写入文件
fs.writeFile('./文件名.txt','写入文本'，err =>{
             //err 写入失败：错误对象 写入成功：null
             if(err){
  							console.log('写入失败');
  							return;
							}
							console.log('写入成功')
             });
console.log(1+1);
```

#### writeFileSync同步写入

语法：`fs.writeFileSync(file,data[,options]);`

参数说明：

* file 文件名
* data 待写入的数据
* options 选项设置（可选）

```js
//1.导入fs模块
const fs = require('fs');

//2.写入文件
fs.writeFileSync('./文件名.txt','写入文本'，err =>{
             //err 写入失败：错误对象 写入成功：null
             if(err){
  							console.log('写入失败');
  							return;
							}
							console.log('写入成功')
             });
```

> Node.js 中的磁盘操作是由其他 线程 完成的，结果的处理有两种模式:
>
> 同步处理 JavaScript 主线程 会等待 其他线程的执行结果，然后再继续执行主线程的代码， 效率较低
>
> 异步处理 JavaScript 主线程 不会等待 其他线程的执行结果，直接执行后续的主线程代码， 效率较好

#### appendFile/appendFileSync追加写入

appendFile作用是在文件尾部追加内容，appendFile语法与writeFile语法完全相同

语法：

`fs.appendFile(file,data[,options],callback);`

`fs.appendFileSync(file,data[,options],callback);`

参数说明：

参数说明：

* file 文件名
* data 待写入的数据
* options 选项设置（可选）
* callback 写入回调

返回值：==undefined==

```js
//1.引入fs模块
const fs = require('fs');

//2.调用appendFile
fs.appendFile('./文件名.txt','/r/n追加文本'，err=>{
              // \r\n 换行
              //判断
              if(err){
  							console.log('写入失败')；
                return；
							}
							console.log('追加写入成功');
              }); 
```

#### createWriteSteam流式写入

语法：`fs.createWtireSteam(path[,options]);`

参数说明：

* path 文件路径
* options 选项配置（可选）

返回值：==Object==

> * 优点：==程序打开一个文件时需要消耗资源==，流式写入可以减少打开关闭文件的次数
>
> * 使用场景：==大文件写入==或者==频繁写入==的场景
>

```js
//1.导入fs
const fs = require('fs');

//2.创建写入流对象
const ws = fs.createWriteStream('./观书有感.txt');

//3.write
ws.write('半亩方塘一鉴开\r\n');
ws.write('天光云影共徘徊\r\n');
ws.write('问渠哪得清如许\r\n');
ws.write('为有源头活水来\r\n');

//4.关闭通道
ws.close();
```

文件写入场景

* 下载文件
* 安装软件
* 保存系统日志，e.g.Git
* IDE保存文件
* 视频录制

> 当==需要持久化保存数据==的时候，应该想到==文件写入==

### 2.文件读取

通过程序从文件中取出其中的数据

| 方法             | 说明     |
| ---------------- | -------- |
| readFile         | 异步读取 |
| readFileSync     | 同步读取 |
| createReadStream | 流式读取 |

#### readFile 异步读取

语法：`fs.readFile(path[,options],calback);`

参数说明：

* path 文件路径
* options 选项配置
* callback 回调函数

返回值：`undefined`

```js
//导入 fs 模块
const fs = require('fs');

fs.readFile('./需要读取的文件文件名.txt'，{err,date} >> {
  if(err) {
    console.log('读取失败')；
    return；
  }
  console.log(date.toString());
});
//err负责接收错误信息
//date负责接收读取到的文件信息
```

#### readFileSync 同步读取

语法: `fs.readFileSync(path[, options]);` 

参数说明:

* path 文件路径 

* options 选项配置

返回值: ==string | Buffer==

```js
//1.引入fs模块
const fs = require('fs');

let date = fs.readFileSync('需要读取的文件文件名.txt');
console.log(date.toString());
```

#### createReadFile 流式读取

语法: `fs.createReadStream(path[, options]);` 

参数说明:

* path 文件路径
* options 选项配置( 可选 )

 返回值: ==Object==

```js
//1.引入 fs 模块
const fs = require('fs');

//2.创建读取流对象
const rs = fs.createReadStream('。/文件路径')；

//3.绑定data时间 chunk 块
rs.on('date',chunk => {
	console.log(chunk);
	//length读取长度
})

//4.end
rs.on('end',() => {
	console.log('读取完成')；
})；
```

文件写入应用场景

* 电脑开机
* 程序运行
* IDE打开文件
* 查看图片
* 播放视频
* 播放音乐
* Git查看日志
* 上传文件
* 查看聊天记录

### 3.文件移动与重命名

语法：

```js
fs.rename(oldPath,newPath,callback);
fs,renameSync(oldPath,newPath);
```

参数说明：

* oldPath 文件当前路径
* newPath 文件新的路径
* callback 操作后的回调

```js
const fs = require('fs');

fs.rename('./要移动的文件名.txt','./文件的新路径/要移动的文件名.txt'，（err => {
          if(err) throw err;
					console.log('移动完成')；
          })；
fs.renameSync('./要移动的文件名.txt','./文件的新路径/要移动的文件名.txt');
```

### 4.文件删除

| 方法       |
| ---------- |
| unlink     |
| unlinkSycn |
| rm         |
| rmSycn     |

Node.js中，可以使用unlink或unlinkSync来删除文件

语法：

```js
fs.unlink(path,callback);
fs.umlinkSync(path);
fs.rm(path);
fs.rmSync(path);
```

参数说明：

* path 文件路径
* callback 操作后的回调

### 5.文件夹操作

| 方法                | 说明       |
| ------------------- | ---------- |
| mkdir/mkdirSync     | 创建文件夹 |
| readdir/readdirSync | 读取文件夹 |
| rmdir/rmdirSync     | 删除文件夹 |

#### mkdir 创建文件夹

语法：

```js
fs.mkdir(path[,options],callback);
fs.mkdir(path[,options]);
```

参数说明:

* path 文件夹路径
* options 选项配置（可选）
* callback 操作后的回调

```js
//1.导入 fs 模块
const fs = require('fs');

//2.创建文件夹
//mk make 制作
//dir directory 文件夹
fs.mkdir('./html',err => {
  if(err) {
    console.log('创建失败')；
    return;
  }
  console.log('创建成功')；
})；
```

递归创建

```js
fs.mkdir('./a/b/c',{recusive:ture},err => {
  if(err) {
    console.log('创建失败')；
    return；
  }
  console.log('创建成果');
}); 
```

#### readdir **读取文件夹**

语法:

`fs.readdir(path[, options], callback)`

`fs.readdirSync(path[, options])`

参数说明:

* path 文件夹路径
*  options 选项配置( 可选 )
*  callback 操作后的回调

```js
//1.导入 fs 模块
const fs = require('fs');

//2.读取文件夹
//异步
fs.readdir('./要读取的文件夹',(err,data) => {
  if(err) {
    console.log('读取失败');
    return;
  }
  console.log(data);
});
//同步
let data = fs.readdirSync('./要读取的文件夹');
console.log(data);
```

#### rmdir 删除文件夹

语法:

`fs.rmdir(path[, options], callback);`

`fs.rmdirSync(path[, options]);`

参数说明:

* path 文件夹路径
* options 选项配置( 可选 )
*  callback 操作后的回调

```js
//1.导入 fs 模块
const fs = require('fs');

//2.删除文件夹
fs.rmdir('./要删除的文件夹',err => {
  if(err) {
    console.log('删除失败');
    return；
  }
  console.log('删除成功')；
})；

//3.异步递归
fs.rmdir('./要删除的文件夹'，{recursive:ture},err => {
  if(err) {
    console.log(err);
    return;
  }
  console.log('递归成功');
});
//4.同步递归
fs.rmdirSync('./要删除的文件夹',{recursive:ture});
```

#### 查看资源状态

语法:

`fs.stat(path[, options], callback)`

`fs.statSync(path[, options])`

参数说明:

* path 文件夹路径
* options 选项配置( 可选 ) 
* callback 操作后的回调

结果值对象结构:

* size 文件体积
* birthtime 创建时间
* mtime 最后修改时间 
* isFile 检测是否为文件
* isDirectory 检测是否为文件夹

```js
//1.导入 fs 模块
const fs = require('fs');

//2.异步获取
fs.state('.要获取的文件.txt',(err,data) => {
  if(err) {
    console.log(err);
    return;
  }
  console.log(data);
})
//3.同步获取
let date = fs.stateSync('./文件名称.txt');
```

## path 模块

path 模块提供 ==操作路径==的功能

| API           | 说明                        |
| ------------- | --------------------------- |
| path.resolve  | 拼接规范的绝对路径 ==常用== |
| path.sep      | 获取操作系统的路径分隔符    |
| path.parse    | 解析路径并返回对象          |
| path.basename | 获取路径的急促名称          |
| path.dirname  | 获取路径的基础名称          |
| path.extname  | 获取路径扩展名              |

```js
//1.导入 path 模块
const path = require('path');

//获取路径分隔符
console.log(path.sep);

//拼接绝对路径
console.log(path。resolve(__dirname,'test'))；

//解析路径
let pathname = 'D:/program file/nodejs/node.exe';
console.log(path.parse(pathname));

//获取路径基础名称
console.log(path.basename(pathname));

//获取路径目录名
console.log(path.dirname(pathname));

//获取路径的扩展名
console.log(path.exname(pathname));
```

## HTTP 协议

### 概念

HTTP(hypertext transport protocol)协议;

中文叫**超文本传输协议** 是一种基于TCP/IP的应用层通信协议

这个协议详细规定了==浏览器==和万维网==服务器==之间互相通信的规则。

协议中主要规定了两个方面的内容：

* 客户端:用来向服务器发送数据，可以被称之为 **请求报文** 
* 服务端:向客户端返回数据，可以被称之为 **响应报文**

>  报文:可以简单理解为就是一堆字符串

### 1.请求报文

* 请求行

  * 请求方法(get、post、put、delete等)

  * 请求 URL(统一资源定位器)

    >  e.g. http://www.baidu.com:80/index.html?a=100&b=200#logo
    >
    > * http:                        协议(https、ftp、ssh等)
    > * www.baidu.com   域名
    > * 80                            端口号
    > * /index.html            路径
    > * a=100&b=200       查询字符串
    > * #logo                      哈希(锚点链接)

  * HTTP协议版本号

* 请求头

  格式:『头名:头值』

  常见的请求头有:

  | 请求头                                | 解释                                                         |
  | ------------------------------------- | ------------------------------------------------------------ |
  | Host                                  | 主机名                                                       |
  | Connection                            | 连接的设置 keep-alive(保持连接)/close（关闭连接）            |
  | Cache-Control                         | 缓存控制max-age=0(没有缓存)                                  |
  | Upgrade-<br />Insecure-<br />Requests | 将网页中的http请求转化为https请求                            |
  | User-Agent                            | 用户代理，客户端字符串标识，服务器可以通过这个标识来识别哪个客户端，一般在PC端和手机端区分 |
  | Accept                                | 设置浏览器接受的数据类型                                     |
  | Accept-Encoding                       | 设置接受的压缩方式                                           |
  | Accept- Language                      | 设置接受的语言 q=0.7 的喜好系数，满分为1                     |
  | Cookie                                |                                                              |

* 空行

* 请求体

  请求体的内容是非常灵活的

  （可以是空） ===>GET请求

  （可以是字符串/JSON） ===>POST请求

  e.g.

  > 字符串：`keyword=手机&price=2000`
  >
  > JSON：`{"keywords":"手机","price":2000}`

### 2.响应报文

* 响应行

  `HTTP/1.1 200 OK`

  * HTTP/1.1 : HTTP协议版本号

  * 200 : 响应状态码

    | 响应状态码 | 含义                  |
    | ---------- | --------------------- |
    | 200        | 请求成功              |
    | 404        | Not Found             |
    | 500        | Internal Server Error |

  * OK ： 响应状态描述

    | 响应状态描述  | 含义                             |
    | ------------- | -------------------------------- |
    | OK            | 成功                             |
    | GET           | :资源已被提取并在消息正文中传输  |
    | HEAD          | 实体标头位于消息正文             |
    | PUT` or `POST | 描述动作结果的资源在消息体中传输 |
    | TRACE         | 消息正文包含服务器收到的请求消息 |

    > 响应状态码和响应字符串关系是一一对应的。

* 响应头

```
Cache-Control:缓存控制 private 私有的，只允许客户端缓存数据
Connection 链接设置
Content-Type:text/html;charset=utf-8 设置响应体的数据类型以及字符集,响应体为html，字符集 utf-8
Content-Length:响应体的长度，单位为字节
```

* 空行

* 响应体

  响应体内容的类型是非常灵活的，常见的类型有 HTML、CSS、JS、图片、JSON

### 3.创建HTTP服务

**操作步骤**

```js
//1. 导入 http 模块
const http = require('http');

//2. 创建服务对象 create 创建 server 服务
// request 意为请求. 是对请求报文的封装对象, 通过 request 对象可以获得请求报文的数据
// response 意为响应. 是对响应报文的封装对象, 通过 response 对象可以设置响应报文 
const server = http.createServer((request, response) => {
    response.end('Hello HTTP server');
});

//3. 监听端口, 启动服务 
server.listen(9000, () => {
console.log('服务已经启动, 端口 9000 监听中...'); 
});
```

> http.createServer里的回调函数的执行时机: 当接收到 HTTP 请求的时候，就会执行

**测试**

 浏览器请求对应端口

> http://127.0.0.1:9000 

**注意事项**

1. 命令行 ctrl + c 停止服务
2. 当服务启动后，更新代码必须重启服务才能生效 
3. 响应内容中文乱码的解决办法

```
response.setHeader('content-type','text/html;charset=utf-8');
```

4. 端口号被占用

```
Error: listen EADDRINUSE: address already in use :::9000
```

​	1)关闭当前正在运行监听端口的服务 ( 使用较多 ) 

​	2)修改其他端口号

5. HTTP协议默认端口是80。HTTPS协议的默认端口是443,HTTP服务开发常用端口有3000， 8080，8090，9000 等

> 如果端口被其他程序占用，可以使用==资源监视器==找到占用端口的程序，然后使用==任务管理器==关闭对应的程序

### 4.获取 HTTP请求报文

想要获取请求的数据，需要通过==request==对象

| 含义          | 语法                                                         |
| ------------- | ------------------------------------------------------------ |
| 请求方法      | request.method                                               |
| 请求版本      | request.httpVersion                                          |
| 请求路径      | request.url                                                  |
| URL路径       | require("url").parse(request.url).pathname                   |
| URL查询字符串 | require("url").parse(request.url,true).query                 |
| 请求头        | request.headers                                              |
| 请求体        | request.on('data',function(chunk)[]);<br />request.on('end',function(){}); |

注意事项：

1. request.url只能获取路径以及查询字符串，无法获取URL中的域名以及协议的内容
2. request.headers将请求信息转化成一个对象，并将属性名都转化成了『小写』
3. 关于路径:如果访问网站的时候，只填写了IP地址或者是域名信息，此时请求的路径为『/』 
4. 关于favicon.ico:这个请求是属于浏览器自动发送的请求

### 5.设置 HTTP 响应报文

| 作用             | 语法                                          |
| ---------------- | --------------------------------------------- |
| 设置响应状态码   | response.statusCode                           |
| 设置响应状态描述 | response.statusMessage                        |
| 设置响应头信息   | response.serHeader('头名','头值')             |
| 设置响应体       | response.write('xx')<br />response.end('xxx') |

```js
write 和 end 的两种使用情况:
//1. write 和 end 的结合使用 响应体相对分散 response.write('xx');
response.write('xx');
response.write('xx');
response.end(); //每一个请求，在处理的时候必须要执行 end 方法的
//2. 单独使用 end 方法 响应体相对集中 response.end('xxx');
```

### 6.静态资源服务

静态资源是指==内容长时间不发生改变的资源==，例如图片，视频，CSS 文件，JS文件，HTML文件，字体文 件等

动态资源是指==内容经常更新的资源==，例如百度首页，网易首页，京东搜索列表页面等

* 网站根目录或静态资源目录
  HTTP 服务在哪个文件夹中寻找静态资源，那个文件夹就是==静态资源目录==，也称之为==网站根目录==

* 网页中的URL
   网页中的 URL 主要分为两大类:相对路径与绝对路径 

  * 绝对路径：绝对路径可靠性强，而且相对容易理解，在项目中运用较多

  | 形式                   | 特点                                                         |
  | ---------------------- | ------------------------------------------------------------ |
  | http://atguigu.com/web | 直接向目标资源发送请求，容易理解。网站的外链会用到此形式     |
  | //atguigu.com/web      | 与页面 URL 的协议拼接形成完整 URL 再发送请求。大型网站用的比较多 |
  | /web                   | 与页面 URL 的协议、主机名、端口拼接形成完整 URL 再发送请求。适用于中小型网站 |

  * 相对路径：相对路径在发送请求时，需要与当前页面 URL 路径进行==计算==，得到完整 URL 后，再发送请求，学习阶段用的较多
    e.g.当前网页 url 为 http://www.atguigu.com/course/h5.html

| 形式               | 最终的URL                                 |
| ------------------ | ----------------------------------------- |
| ./css/app.css      | http://www.atguigu.com/course/css/app.css |
| js/app.js          | http://www.atguigu.com/course/js/app.js   |
| ../img/logo.png    | http://www.atguigu.com/img/logo.png       |
| ../../mp4/show.mp4 | http://www.atguigu.com/mp4/show.mp4       |

* 网页中使用URL的场景小结

  包括但不限于如下场景:

  * a 标签
  * href link 标签
  * href script 标签 src
  * img 标签 src
  * video audio 标签 src
  * form 中的 action
  * AJAX 请求中的 URL

* 设置资源类型(mime类型)

  媒体类型(通常称为 Multipurpose Internet Mail Extensions 或 MIME 类型 )是一种标准，用来表示文档、文件或字节流的性质和格式。

HTTP 服务可以设置响应头 Content-Type 来表明响应体的 MIME 类型，浏览器会根据该类型决定如何处理 资源

```
mime 类型结构: [type]/[subType]
e.g.text/html text/css image/jpeg image/png application/json
```

下面是常见文件对应的 mime 类型

```
html: 'text/html',
css: 'text/css',
js: 'text/javascript',
png: 'image/png',
jpg: 'image/jpeg',
gif: 'image/gif',
mp4: 'video/mp4',
mp3: 'audio/mpeg',
json: 'application/json'
```

> 对于未知的资源类型，可以选择==application/octet-stream==类型，浏览器在遇到该类型的响应 时，会对响应体内容进行独立存储，也就是我们常见的==下载==效果

```nodejs
require('http').createServer((request,response)=>{ //获取请求的方法已经路径
 let {url,method} = request; //判断请求方式以及请求路径

if(method == "GET" && url == "/index.html"){
 //需要响应文件中的内容
 let data = require('fs').readFileSync(__dirname + '/index.html'); response.end(data);

}else if(method == "GET" && url == "/css/app.css"){
 //需要响应文件中的内容
 let data = require('fs').readFileSync(__dirname + '/public/css/app.css'); response.end(data);

}else if(method == "GET" && url == "/js/app.js"){
 //需要响应文件中的内容
 let data = require('fs').readFileSync(__dirname + '/public/js/app.js'); response.end(data);

} else{

//404响应
 response.statusCode = 404; response.end("<h1>404 Not Found</h1>");
     }
}).listen(80,()=>{
console.log('80端口正在启动中....'); })
```

很明显上面的代码，当只要有一个请求路径就需要进行判断，显然这种方式不够完美，那么我们需要封装

```nodejs
require('http').createServer((request,response)=>{ //获取请求的方法已经路径
let {url,method} = request;
//文件夹路径
let rootDir = __dirname + '/public'; //拼接文件路径
let filePath = rootDir + url; //读取文件内容 fs.readFile(filePath,(err,data)=>{
//判断 if(err){
//如果出现错误，响应404状态码 response.statusCode = 404; response.end('<h1>404 Not Found</h1>');
}else{ //响应文件内容
            response.end(data);
        }
    })
}).listen(80,()=>{
console.log('80端口正在启动中....'); })
```

* GET 和 POST 请求场景小结 

  GET 请求的情况:

  * 在地址栏直接输入 url 访问
  * 点击a链接
  * link 标签引入 css
  * script 标签引入 js
  * img 标签引入图片
  * form 标签中的 method 为 get (不区分大小写)
  * ajax 中的 get 请求

  POST 请求的情况:

  * form 标签中的 method 为 post(不区分大小写)
  * AJAX 的 post 请求

> GET 和 POST 请求的区别
>
> GET 和 POST 是 HTTP 协议请求的两种方式。
>
> * GET 主要用来获取数据，POST 主要用来提交数据
> * GET 带参数请求是将参数缀到 URL 之后，在地址栏中输入 url 访问网站就是
> * GET 请求， POST 带参数请求是将参数放到请求体中
> * POST 请求相对 GET 安全一些，因为在浏览器中参数会暴露在地址栏
> * GET 请求大小有限制，一般为 2K，而 POST 请求则没有大小限制

## 模块化

将一个复杂的程序文件依据一定规则(规范)拆分成多个文件的过程称之为==模块化== 

其中拆分出的==每个文件==就是一个模块 ，模块的内部数据是私有的，不过模块可以暴露内部数据以便其他模块使用

* 好处：
  1. 防止命名冲突
  2. 高复用性
  3. 高维护性

#### 1.暴露数据

* `module.exports = value`

* `exports.name = value`

> * module.export 可以暴露==任意==数据
> * 不能使用 export = value 的形式暴露数据，模块内部 module 与 exports 的隐式关系exports = module.exports = {} ,require返回的是目标模块中 ==module.exports== 的值

#### 2.导入(引入)模块

在模块中使用 require 传入文件路径即可引入文件

```nodejs
const test = require('./me.js');
```

require 使用的一些注意事项:

1. 对于自己创建的模块，导入时路径建议写==相对路径==，且不能省略 ==./== 和 ==../==

2. ==js==和==json==文件导入时可以不用写后缀，c/c++编写的 node 扩展文件也可以不写后缀，但是一般用不到

3. 如果导入其他类型的文件，会以 ==js== 文件进行处理

4. 如果导入的路径是个文件夹，则会==首先==检测该文件夹下 package.json 文件中 main 属性对应的文件，

   如果存在则导入，反之如果文件不存在会报错。

   如果main属性不存在，或者package.json不存在，则会尝试导入文件夹下的 ==index.js== 和 ==index.json== ，

   如果还是没找到，就会报错

5. 导入node.js内置模块时，直接require模块的名字即可，无需加==./==和==../==

#### 3.导入模块的基本流程

1. 将相对路径转为绝对路径，定位目标文件
2. 缓存检测
3. 读取目标文件代码
4. 包裹为一个函数并执行(自执行函数)。通过 arguments.callee.toString() 查看自执行函数 5. 缓存模块的值
5. 返回 module.exports 的值

* CommonJS 规范

  ==module.exports==、==exports==以及==require==这些都是==CommonJS==模块化规范中的内容。 而 Node.js 是实现了 CommonJS 模块化规范，二者关系有点像 JavaScript 与 ECMAScript

## 包管理工具

* 包

   ==package==，代表了一组特定功能的源码集合

* 包管理工具

  管理包的应用软件，可以对包进行==下载安装==，==更新==，==删除==，==上传==等操作借助包管理工具，可以快速开发项目，提升开发效率

  包管理工具是一个通用的概念，很多编程语言都有包管理工具

#### 常用的包管理工具

* npm

  npm 全称 ==Node Package Manager== ，翻译为中文意思是「Node 的包管理工具」

  npm 是 node.js 官方内置的包管理工具

  * 安装

    node.js在安装时会==自动安装 npm==，所以如果你已经安装了node.js，可以直接使用npm 可以通过 ==npm -v== 查看版本号测试，如果显示版本号说明安装成功，反之安装失败

  * 使用

    * 初始化

      创建一个空目录，然后以此目录作为工作目录==启动命令行工具==，执行 ==npm init==

      ==npm init== 命令的作用是将文件夹初始化为一个「包」， 交互式创建 ==package.json== 文件 ==package.json== 是包的配置文件，每个包都必须要有 ==package.json==

      ```json
      {
      "name": "1-npm",		#包的名字
      "version": "1.0.0",	#包的版本
      "description": "",	#包的描述
      "main": "index.js",	#包的入口文件
      "scripts": { 				#脚本配置
        "test": "echo \"Error: no test specified\" && exit 1"
      	},
      "author": "", 			#作者
      "license": "ISC" 		#开源证书 
      }
      ```

      > 初始化的过程中还有一些注意事项:
      >
      > 1. ==package name==(包名)不能使用中文、大写，默认值是==文件夹的名称==，所以文件夹名称也不能使用中文和大写
      > 2. ==version== ( 版本号 )要求 ==x.x.x== 的形式定义， x 必须是数字，默认值是 1.0.0
      > 3. ISC证书与MIT证书功能上是相同的，关于开源证书扩展阅读http://www.ruanyifeng.com/blog/2011/05/how_to_choose_free_software_licenses.html
      > 4. ==package.json==可以手动创建与修改
      > 5. 使用 ==npm init -y== 或者 ==npm init --yes== 极速创建 ==package.json==

    * 搜索包

      * 命令行 「npm s/search 关键字」
      * ==网站搜索==（==https://www.npmjs.com/==）

    * 下载安装包

      * ==npm install== 和 ==npm i== 命令安装包

      * 运行之后文件夹下会增加两个资源：
        ==node_modules 文件夹==存放下载的包
        ==package_lock.json 包的锁文件==，用来锁定包的版本

    > 安装 uniq 之后， uniq 就是当前这个包的一个 ==依赖包== ，有时会简称为 ==依赖==
    >
    > 比如我们创建一个包名字为 A，A 中安装了包名字是 B，我们就说 ==B 是 A 的一个依赖包== ，也会说 ==A 依赖 B==

    * require导入npm包
      1. 在当前文件夹下node_modules中寻找同名的文件夹
      2. 在上级目录中下的node_modules中寻找同名的文件夹，直至找到磁盘根目录

  * 环境

    * 开发环境：程序员==专门用来写代码==的环境，一般是指程序员的电脑，开发环境的项目一般==只能由程序员自己访问==
    * 生产环境：项目==代码正式运行==的环境，一般是指正式的服务器电脑，生产环境的项目==一般所有用户都可以访问==

  * 依赖

  * 全局安装

  * 安装包依赖

  * 安装指定版本的包

  * 删除依赖

  * 配置命令别名

* yarn

* cnpm

## NVM

## express工具

## 接口

## 会话控制
