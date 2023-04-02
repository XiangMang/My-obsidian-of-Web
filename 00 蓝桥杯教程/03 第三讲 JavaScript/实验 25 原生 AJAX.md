## 实验介绍

终于等到你～

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验给大家介绍原生 AJAX 技术，同学们快一起来学习吧！

#### 知识点

- XMLHttpRequest 对象
- open 和 send 方法
- onreadystatechange 函数

点击底部的 ![img](https://labfile.oss.aliyuncs.com/courses/4421/btn.png)，开始实验之旅吧～

## 认识 AJAX

AJAX 的英文全称为 Asynchronous JavaScript And XML，Asynchronous 是异步的意思。何为异步呢？在这里异步是指通过 AJAX 向服务器请求数据，在不刷新整个页面的情况下，更新页面上的部分内容。

其工作原理图如下所示：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/1389bcd14fc2ba77b5f8343420f96304-0)

用户在浏览器执行一些操作，通过 AJAX 引擎发送 HTTP 请求到服务器请求数据，请求成功后，由服务器把请求的数据拿给 AJAX 引擎，再由 AJAX 拿给浏览器。AJAX 在这个过程中相当于是服务员，用户点好菜，由服务员把菜单交给厨师，厨师做好菜，由服务员把菜送到用户的餐桌上。

同学们可能会想，我直接把菜单交给厨师，省去中间人沟通岂不是更简单？

浏览器如果直接向服务器请求数据的话，在请求过程中，你是不能对页面进行其他操作的，这叫同步请求，而把请求数据这个活外包给 AJAX 后，在请求过程中，用户还是可以对页面进行其他操作，这就是我们的异步请求了，也是 AJAX 的核心特点。

了解了 AJAX，接下来我们学一下 AJAX 的创建吧！

## 创建 AJAX 的基本步骤

**1. 创建 XMLHttpRequest 对象**

在 AJAX 中，`XMLHttpRequest` 对象是用来与服务器进行数据交换的。其创建如下所示：

```js
var httpRequest = new XMLHttpRequest();
```

为了保证浏览器的兼容性，我们可以用以下方式来创建。

```js
if (window.XMLHttpRequest) {
  // Mozilla，Safari，IE7+ 等浏览器适用
  httpRequest = new XMLHttpRequest();
} else if (window.ActiveXObject) {
  // IE 6 或者更老的浏览器适用
  httpRequest = new ActiveXObject("Microsoft.XMLHTTP");
}
```

**2.向服务器发送请求**

在步骤一中我们已经创建了用于服务器交换数据的 `XMLHttpRequest` 对象，要向服务器发送请求，我们需要调用该对象中的 `open` 和 `send` 方法。

其使用如下：

```js
// 规定发送请求的一些要求
httpRequest.open("method", "url", async);
// 将请求发送到服务器
httpRequest.send();
```

`open` 方法中的参数说明如下：

- `method` 是请求的类型，常见的有 `GET` 和 `POST`。
- `url` 是请求的地址。
- `async` 是设置同步或者异步请求，其值为布尔类型，当为 true 时，使用异步请求；当为 false 时，使用同步请求，默认为 true。

**3.服务器响应状态**

我们使用 HTTP 请求数据后，请求是否成功，会反馈给我们相应的请求状态。我们使用 `onreadystatechange` 去检查响应的状态，当 `httpRequest.readyState` 为 4 并且 `httpRequest.status` 等于 200 时，说明数据请求成功，其使用如下：

```js
httpRequest.onreadystatechange = function () {
  if (httpRequest.readyState == 4 && httpRequest.status == 200) {
    // 请求成功执行的代码
  } else {
    // 请求失败执行的代码
  }
};
```

了解了 AJAX 的创建，接下来我们做一做练习吧！

## AJAX 的使用

新建一个 `index.html` 文件，在该文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AJAX 的使用</title>
    <script>
      window.onload = function () {
        if (window.XMLHttpRequest) {
          // Mozilla，Safari，IE7+ 等浏览器适用
          var httpRequest = new XMLHttpRequest();
        } else if (window.ActiveXObject) {
          // IE 6 或者更老的浏览器适用
          var httpRequest = new ActiveXObject("Microsoft.XMLHTTP");
        }
        // 规定发送请求的一些要求
        httpRequest.open(
          "GET",
          "https://jsonplaceholder.typicode.com/users",
          true
        );
        // 将请求发送到服务器
        httpRequest.send();
        httpRequest.onreadystatechange = function () {
          console.log(httpRequest.readyState);
          console.log(httpRequest.status);
          if (httpRequest.readyState == 4 && httpRequest.status == 200) {
            // 请求成功执行的代码
            document.getElementById("item").innerHTML = "请求成功";
          } else {
            // 请求失败执行的代码
            document.getElementById("item").innerHTML = "请求失败";
          }
        };
      };
    </script>
  </head>
  <body>
    <div id="item"></div>
  </body>
</html>
```

完成上面代码后，开启 8080 端口，打开 Web 服务和控制台可以看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/b592e90684c51d1583d1027539d4cd13-0)

在控制台中输出的 200 是 HTTP 的响应状态码，该状态码还有其他取值，感兴趣的同学可以阅读 [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)。

而穿插在 200 之后的数字 2、3、4 是 `readyState` 的值，它的取值有以下几种：

- 0 代表未初始化请求。
- 1 代表已与服务器建立连接。
- 2 代表请求被接受。
- 3 代表请求中。
- 4 代表请求完成。

## 实验总结

本节实验带大家认识了什么是 AJAX，以及它的创建，最后通过练习题带大家体验了一下 AJAX 的使用。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210712-1626055838015)

下节内容更精彩，跟着我走吧～