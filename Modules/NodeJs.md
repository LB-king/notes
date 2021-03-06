### NodeJs是什么

- nodeJs不是一门语言，不是库，也不是框架

- 是JavaScript的运行环境

- 解析和执行JavaScript的代码

- 特点：

  没有DOM和BOM

  在Node这个运行环境中为JavaScript提供了服务器级别的操作API：

  - 文件读写
  - 网络服务的构建
  - 网络通信

1.event-driven 事件驱动

2.non-blocking I/O model 非阻塞I/O模型

3.lightweght and efficient 轻量级和高效

### 核心模块

file-system(文件系统)

- readFile-异步读取文件

  ```javascript
  fs.readFile(url,'utf8',callback(err,data){
          //文件存储的数据是二进制
          //打印出来的是一串Buffer...16进制
          //因此需要 data.toString()转化为开发者能够识别的格式
      })
  ```

- readFileSync-同步读取文件

  ```javascript
  let res = fs.readFileSync(url);//直接返回结果
  ```

- writeFile

  ```javascript
  fs.writeFile(url,content,callback(err){
  	
  })
  ```

#### http

```javascript
const server = http.createServer();
server.on('request',callback(req,res){
 	//	req:请求对象
        req.url
    //	res:响应对象-可以给客户端发送响应信息
    //  res.writeHead(200,{'Content-Type','text/plain;charset=utf-8'}) 
	//	res.setHeader('Content-Type','text/plain;charset-utf-8')
	//	res.end(data)
  })

  server.listen(3000,function(){

  })  
```

#### os

os.cpus()

os.totalmem()

#### path

path.extname(__dirname+'test.js')  扩展名

path.join('/a','/v/x','/tt')  --->a/v/x/tt

#### url

url.parse(http://god.com:3001/admin/zhangsan?name=kobe&age=18',true);

结果：

  protocol: 'http:',
  slashes: true,
  auth: null,
  host: 'god.com:3001',
  port: '3001',
  hostname: 'god.com',
  hash: null,
  search: '?name=kobe&age=18',
  query: [Object: null prototype] { name: 'kobe', age: '18' },
  pathname: '/admin/zhangsan',
  path: '/admin/zhangsan?name=kobe&age=18',
  href: 'http://god.com:3001/admin/zhangsan?name=kobe&age=18' 

### Express

安装:

```shell
npm install express
```

使用:

```javascript
let app = require('express')()
```



art-template不仅可以在浏览器使用，也可以在node中使用

```javascript
//变量
{{ name }}
//数组
{{ each list }}
{{ $value }}
{{ /each }}
//条件  
{{if value}} ... {{/if}}
{{if v1}} ... {{else if v2}} ... {{/if}} 

```

#### express-art-template

安装：

```shell
npm install express express-art-template
```

配置：

```javascript
//注意：先配置好模板引擎
app.engine('html',require('express-art-template'))
app.use(router);

```

使用：

```javascript
res.render('index.html',{name:"hello art-teplate"})
```



### MongoDB

- 安装

- 启动

  ```powershell
  #mongodb默认执行 mongod 命令所处盘符目录下的 /data/db 作为自己的数据存储目录
  #所以需要手动新建一个
  mongod
  ```

- 连接

  ```shell
  mongo
  ```

- 如果想要修改默认的存储目录，可以

  ```shell
  mongod --dbpath=数据库存储目录
  ```

  

- 常见命令

  ```shell
  #查看本地数据库
  show dbs
  #切换到指定数据库，没有则新建
  use db1
  db.students.insertOne({name:'me'})
  db.colletions.find()
  ```

- 设计表

   id | username | password | gender | 444
   :-: | :-: | :-: | :-: | :-:
   aaa | bbb | ccc | ddd | eee
   fff | ggg| hhh | iii | 000

### JSON-SERVER

- 安装：

  ```shell
  npm install json-server -g
  ```

  