## 实验介绍

嗨！欢迎来到本章节～

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/deac8f2800a54855dbcb80b35d932fbd-0)

HTTP 协议（Hyper Text Transfer Protocol）是超文本传输协议，它是基于请求-响应的一个协议，即客户端浏览器给服务器发送一个 HTTP 请求，然后服务器对客户端的请求作出响应。我们开发的基于浏览器的 B/S 架构的程序都是基于 HTTP 协议（也有 HTTPS）的，例如登录、注册、查询商品等。

当用户在 URL 中输入一个网址到看到页面，大体经过如下几步：

- DNS 解析，建立 TCP 连接，发送 HTTP 请求。
- Server 端接收 HTTP 请求，处理，返回结果。
- 客户端接收到返回数据，进行页面渲染显示内容。

本节实验要给同学介绍的就是发送请求最常用的两种方式，GET 和 POST。

我们快一起去学习吧！

#### 知识点

- GET 请求
- POST 请求

## 处理 GET 请求

通过浏览器向服务器发送请求的常用方式分为两种，一种是 `GET` 方式，另一种是 `POST` 方式，前者请求的安全性不高，常用于查询的操作，如查询用户信息、查询博客信息等。

GET 请求传递参数是在 URL 后面加入一个 "?" ，然后在 "?" 后面加入想要传递的参数，多个参数之间用 "&" 隔开。格式如下：

```bash
http://localhost:8000/index?id=1001&name=abc
```

首先在右侧控制台中输入以下命令来初始化 npm 环境，初始化完成后会生成一个 package.json 文件。

```bash
npm init -y
```

在 `project` 文件夹下，新建 `index.js` 文件，并加入下列代码：

```js
const http = require("http");
const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/html;charset=utf-8" });
  // 通过请求对象获取完整的请求地址并保存在变量 url 中
  let url = req.headers["x-scheme"] + "://" + req.headers.host + req.url;
  // 将变量传入实例化方法中，并实例化一个 URL 对象
  const myURL = new URL(url);
  let params = myURL.searchParams.toString();
  res.write(params);
  res.end();
});
// 服务侦听 8080 端口
server.listen(8080, () => {
  console.log("服务器运行在 8080 端口...");
});
```

在本示例中代码解析如下：

- 定义一个变量 `url` 用于保存 `req` 对象请求的完整地址，其中 `req.headers['x-scheme']` 返回请求协议名称，如 `http` 或 `https` ，而 `req.headers.host` 返回请求的域名和端口，`req.url` 返回请求的详细路径，包含查询字符串。

- 获取并保存完整的请求地址后，实例化一个 `URL` 对象，在实例化对象的方法中，可以传递两个参数，第一个参数是必选项，表示要解析的绝对或相对的网址，第二个参数是可选项，表示要解析的基础网址，如果第一个参数是绝对地址，则第二个可以省略，如本示例中的代码；如果第一个对数是相对地址，则第二个参数必须添加请求地址的协议名称、域名和端口。

- 如果将示例中绝对的请求地址修改成相对地址，那么在实例化 `URL` 对象时，代码修改如下所示：

  ```js
  // 通过请求对象获取相对请求路径并保存在变量 url 中
  let url = req.url;
  // 在实例化过程中，通过第二个参数添加请求协议的名称、域名和端口
  const myURL = new URL(
    url,
    req.headers["x-scheme"] + "://" + req.headers.host
  );
  ```

  这两种代码实现的方式在使用时，结果都是一样的，但在实际运用时，传入完整的请求地址，使用会更多些。

在控制台中输入以下命令运行该程序。

```bash
node index.js
```

然后点击右侧的 “Web 服务”，并在 `simplelab.cn` 地址后加入 `?id=1001&name=abc`，刷新页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1761387/42e8e6d865da5f007e0c680f28d64164-0)

页面中显示的内容就是以字符串形式输出的 GET 请求参数，如果需要使用，也可以通过指定参数名称获取对应的值。

## 处理 POST 请求

相对于 `GET` 方式请求，`POST` 请求在传输数据时，要安全很多，因此，常用用于数据的添加、删除、修改操作，例如新建博客、删除博客、修改博客等就会使用到 `POST` 请求。

在 `URL` 中输入地址直接访问属于 `GET` 请求，而 `POST` 请求则常用于表单数据的提交，先在 `form` 中设置 `method=post`，当用户点击提交表单按钮时就会发送一个 `POST` 请求，并把表单中用户填入的数据传递给服务器。但是手工编写表单的代码显然比较麻烦，有没有一种更加简单的方式发送 `POST` 请求呢？

答案是有的。可以使用 `Postman` 这个工具来帮助我们发送 `POST` 请求。

## Postman 下载安装

首先在右侧桌面环境打开 Firefox 浏览器，然后在 URL 地址栏中输入 `http://postman.com/downloads` 进入到下载页面。系统自动识别下载 linux 版本的 `postman`。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/2bb9076d5fb39c48fc18f23627160649-0)

然后单击 `Download the App` 按钮进行下载，在弹出的界面中选择 Linux 64-bit 下载（如下图）。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/865e3b15646ea2c1bfe2cc46f52ac1cb-0)

单击”保存文件”按钮进行保存，如下图。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/71a0e239c70da19c9e59550e2141faa3-0)

下载完毕后右上角会提示“已完成”。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/0a8e1d02c320b8dedae44644be98602b-0)

然后点击“显示全部下载”会弹出以下界面。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/c4e9808521a7709cb7b0a97d6f4a0b52-0)

点击“打开所在文件夹”，然后右键点击 `Postman-linux-x86_64-8.11.1.tar.gz` 文件重命名为 `postman.tar.gz`，然后使用鼠标把该文件拖拽到左侧 `shiyanlou` 目录下。然后在实验楼路径中点击右键，选择“在此打开终端”（如下图）。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/612ad1583c41427a467bb594756e523c-0)

然后在终端中输入如下命令进行解压。

```bash
sudo tar -zxvf postman.tar.gz
```

使用如下命令启动 postman

```bash
./Postman/Postman
```

启动后点击左上角的 "File"---"new" 新建一个窗口，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/19f61bbab1f7bc199d7563217cd51708-0)

然后申请一个 `Postman` 账号并点击 `Sign in` 登录（此过程不再截图，同学们自行完成）。登录成功后如下图,然后点击 `Create new`。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/97ea40097245166e993eafa288dd2b9b-0)

在弹出的界面中点击 `HTTP Request`，如下图：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/c8be10806c583fbb66778200bbfaa88d-0)

如果想发送 `HTTP` 请求还需要装一个 `Postman` 客户端才能正常发送请求。使用下列命令下载 `Postman` 客户端。

```bash
cd /home/shiyanlou
wget https://labfile.oss.aliyuncs.com/courses/4380/postmanAgent.tar.gz
```

注意：如果想复制如上命令到云课桌面环境进行粘贴的话，可以借助右侧“剪切板”功能。先复制好想要粘贴的命令，然后点击右侧“剪切板”，把复制的内容粘贴到剪切板中，然后点击保存即可（如下图），然后就可以在云课桌面环境中进行粘贴了。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/1407c7dfe5be62ba083057829652092b-0)

下载完毕后截图如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/4de743d34fb862db3622ed56a33c6289-0)

然后使用如下命令进行解压安装。

```bash
cd /home/shiyanlou
sudo tar -zxvf postmanAgent.tar.gz
```

## 编写代码处理 POST 请求

然后在 `/home/shiyanlou/` 路径下新建 `index.js` 文件，然后编写代码如下：

```js
const http = require("http");

const server = http.createServer((req, res) => {
  if (req.method === "POST") {
    console.log("content-type:", req.headers["content-type"]); // 获取请求类型 application/json

    //读post数据
    let postData = ""; // postData 用来存储传递给服务器的全部数据
    // 分段循环传输数据，每次传递数据都会执行后面的回调函数
    req.on("data", (chunk) => {
      postData += chunk.toString(); // chunk是二进制数据 所以要把它转换成字符串
    });

    // 当数据传输完毕会执行 end 事件后的回调函数
    req.on("end", () => {
      console.log("postData:", postData);
      res.end("Hello"); //在这里返回因为是异步
    });
    console.log("test"); //这里先被打印 因为上面的代码是异步的
  }
});

server.listen(8080, () => {
  console.log("服务器运行在 8080 端口...");
});
```

在终端中输入以下命令运行该程序。

```bash
cd /home/shiyanlou
node index.js
```

最终效果如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/4380/1761387/e5010bd3f5d8f613a9fb766e9e6e1ba4-0)

#### 使用 Postman 发送 POST 请求

然后打开刚才的 `Postman` 界面，根据下图依次选择 `POST` 请求，输入请求地址 `http://localhost:8080`。然后点击 `Body`，选择 `raw `和 `JSON`，输入发送的内容后点击 `Send` 按钮。

![图片描述](https://doc.shiyanlou.com/courses/4380/1761387/446725aa20417676eb862c0ed1b2156e-0)

当看到上图中的返回内容 `Hello` 时，说明程序已经调试成功了，控制台输出如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1761387/35d7d4d9f4372fc434e48ef740f76b24-0)

## 实验总结

本节实验给大家介绍了两种最常用的 Web 请求，分别是 GET 和 POST。这里我们来总结一下：前者的链接中包含请求参数，安全系数低于 POST 请求。但 GET 请求也有自己的用处，比如查询操作时，显然 GET 请求是不错的选择。