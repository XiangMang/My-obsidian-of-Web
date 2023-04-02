## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

今天我们要学习一个新的章节 AJAX，在学习 jQuery 的 AJAX 前让我们先来回顾一下什么是 AJAX 吧！

AJAX 是 Asynchronous JavaScript and XML（异步的 JavaScript 和 XML 的结合），通俗来讲就是在不刷新页面的情况下，AJAX 可以通过后台来加载数据，并显示在网页上，实现局部刷新。

相比原生 AJAX，在 jQuery 中对 AJAX 操作进行了封装。

下面我们就一起来学习吧～

#### 知识点

- load 方法
- get 方法
- post 方法
- ajax 方法
- getJSON
- getScript

## load 方法

load() 方法让 AJAX 去请求服务器，并从中获得数据，最后将获得的数据放入到指定的元素中。

其语法格式为：

```js
$().load(url, data, callback);
```

参数说明如下所示：

- `url` 是被加载页面的地址，它是必选参数。
- `data` 是发送到服务器的数据，它是可选参数。
- `callback` 是请求完成后的回调函数，它是可选参数。

这里请注意，load 方法中的回调函数有三个额外的参数，以下所示：

- `response`：服务器响应的结果数据。
- `status`：服务器响应的状态。
- `xhr`：XMLHttpRequest 对象。

了解了 load 方法，接下来我们做一做练习吧！

#### load 方法的使用

下面我们看一个加载 txt 文件的例子。

首先，使用以下命令获取 jQuery 库。保存了环境的同学，请忽略此步骤。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js
```

然后，在环境中新建一个 `index.html`，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>加载一个 txt 文件</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $(".text").load("text.txt"); // 获取 text.txt 文件中的数据
      });
    </script>
  </head>
  <body>
    <div class="text"></div>
  </body>
</html>
```

接着，新建一个 `text.txt` 文件，在文件中写入以下内容。

```html
欢迎学习 jQuery 上手指南
```

最后，开启 8080 端口，打开 Web 服务，可以看到 text.txt 文件中的内容已经加载到页面上了。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210601-1622512213538)

接下来我们看一个带有回调函数的例子。

新建一个 `index1.html`，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>加载一个 txt 文件</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $(".text").load("text.txt", function (response, status, xhr) {
          $("p").text(
            "请求结果为：" + response + "；" + "请求状态为：" + status
          );
        });
      });
    </script>
  </head>
  <body>
    <div class="text"></div>
    <p></p>
  </body>
</html>
```

效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210601-1622512702445)

在上面代码中，我们使用回调函数把请求的结果和状态写入到了 p 元素中，使其呈现在页面上。

> 需要注意的是：load 方法一般用于向服务器请求静态的数据文件，如 html、txt 等文件。但是在实际工作中，如果我们要传递一些参数给页面，通常不会使用 load 方法。那么该使用什么呢？🤔️

## get 方法

`get` 方法是通过 HTTP GET 请求从服务器请求数据。HTTP 是超文本传输协议，它是客户与服务器之间通信的一种协议，HTTP 有一些请求方法，在这些方法中 `GET` 和 `POST` 是最常见的。同学们想了解更多关于 HTTP 的内容，可以阅读 [HTTP 请求方法](https://www.w3school.com.cn/tags/html_ref_httpmethods.asp)。

其语法格式为：

```js
$.get(url, data, callback(data, status, xhr), dataType);
```

参数说明如下所示：

- `url`：是请求的 url，它是必须参数。
- `data`：是发送到服务器的数据，它是可选参数。
- `callback`：是当请求成功时的回调函数，该方法包含三个参数，`data` 是请求的结果数据，`status` 是包含请求的状态，`xhr` 是 `XMLHttpRequest` 对象。
- `dataType`：是服务器返回的数据格式，如 xml、html、json 等，默认的 jQuery 会智能判断它的类型。

了解了 `get` 方法，接下来我们一起来练习吧！

#### get 方法的使用

获取实验需要的 `food.html` 文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3774/food.html
```

然后，在环境中新建一个 `index2.html`，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>get</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("input").click(function () {
          $.get("food.html", function (data, status) {
            $("div").html(data);
            $("p").append(status);
          });
        });
      });
    </script>
  </head>
  <body>
    <input type="button" value="加载数据" />
    <p>请求状态为：</p>
    <div></div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务会看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/3774/1328821/dfa212ed0ed48be637d2f9fddba9ad5d-0)

从上面我们看到使用 `get` 请求获取到了 `food.html` 页面的数据，通过在方法中使用回调函数在页面上输出了请求页面的内容和请求页面的状态。

## post 方法

前面我们学习了 `get` 方法，从练习中我们可以知道用 GET 请求指定页面，可以返回实体主体，它的请求会被缓存。`post` 方法是用的 POST 请求，它向指定资源提交数据进行处理请求，该请求不会被缓存。

接下来我们看看 jQuery 中 post 方法的应用吧！

`post` 方法的使用格式如下：

```js
$.post(url, data, callback(data, textStatus, jqXHR), dataType);
```

参数说明如下所示：

- `url`：是请求的 url，它是必须参数。
- `data`：是发送到服务器的数据，它是可选参数。
- `callback`：是当请求成功时的回调函数，该方法包含三个参数，`data` 是请求的结果数据，`textStatus` 是包含请求的状态，`jqXHR` 是 `XMLHttpRequest` 对象。
- `dataType`：是服务器返回的数据格式，如 xml、html、json 等。

认识了 post 方法，接下来我们做一做练习吧！

#### post 方法的使用

新建一个 `index3.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>post 方法</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("input").click(function () {
          // 如果链接失效，可以试试 https://labfile.oss.aliyuncs.com/courses/3774/posts.json
          $.post(
            "https://jsonplaceholder.typicode.com/posts",
            function (data, textStatus) {
              $("p").append(textStatus);
            }
          );
        });
      });
    </script>
  </head>
  <body>
    <input type="button" value="请求数据" />
    <p>请求状态：</p>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，可以看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210607-1623048757890)

在上面代码中，当我们点击页面上的按钮时，触发点击事件，`post` 请求会去请求指定链接的数据，最后我们把请求的状态输出到 `p` 元素中。

## post 与 get 方法的比较

post 和 get 有个明显的区别，使用 POST 请求，提交的数据不会显示到 URL 上，查看历史记录不会看到提交的数据。而 GET 请求，则相反，它提交的数据会显示在 URL 上，并且查看历史记录可以看到提交的数据。

接下来我们通过一个练习来比较一下吧！

新建一个 `index4.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>get 和 post 的对比</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $.get(
          "https://jsonplaceholder.typicode.com/users",
          {
            id: "2",
            name: "Cici",
          },
          function (data, success) {
            $("div").text("请求状态：" + success);
          }
        );
        $.post(
          "https://jsonplaceholder.typicode.com/users",
          {
            id: "3",
            name: "Lee",
          },
          function (data, success) {
            $("p").text("请求状态：" + success);
          }
        );
      });
    </script>
  </head>
  <body>
    <div></div>
    <p></p>
  </body>
</html>
```

打开控制台，我们可以看到如下显示：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210624-1624548051711)

从上图我们可以看出，当使用 get 方法时，发送的数据内容会显示到 URL 上，而 post 方法发送的数据则不会显示。

## ajax 方法

`ajax` 方法也是向服务器请求数据的，在方法内部我们可以指定是使用 POST 请求还是使用 GET 请求。在日常开发中 `ajax` 方法是最常用的。

`ajax` 方法的语法格式为：

```js
$.ajax({ 配置项 });
```

接下来我们看一下配置项都有哪些参数吧！

| 参数        | 类型             | 描述                                                         |
| ----------- | ---------------- | ------------------------------------------------------------ |
| url         | String           | 发送请求地址，默认为当前页面地址。                           |
| type        | String           | 请求数据的方式（POST 或 GET），默认为 GET。                  |
| timeout     | Number           | 设置请求超时的时间，其单位为毫秒。                           |
| data        | Object 或 String | 发送到服务器的数据。                                         |
| dataType    | String           | 服务器返回的数据类型。                                       |
| beforeSend  | Function         | 发送请求前可以修改的 XMLHttpRequest 对象的函数。             |
| complete    | Function         | 请求完成后的回调函数，这里的回调函数无论请求成功或者失败都会被调用。 |
| success     | Function         | 请求成功后的回调函数。                                       |
| error       | Function         | 请求失败后被调用的函数。                                     |
| contentType | String           | 发送信息至服务器时内容的编码形式。                           |
| async       | Boolean          | 设置请求方式，当值为 true 时，所有请求为异步请求；当值为 false 时，所有请求为同步请求，默认值为 true。 |
| cache       | Boolean          | 设置浏览器是否缓存当前页面，当值为 true 时浏览器会缓存该页面，反之不会，默认值为 false。 |

当然配置项中的参数不止我们上表介绍的这几种，同学们如果想了解更多参数，请阅读 [jQuery 官方文档](https://www.jquery123.com/jQuery.ajax/)。

了解了 ajax 方法，我们来做一下练习吧！

#### ajax 的使用

新建一个 `index5.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ajax 方法</title>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        // 请求页面原始数据
        $.ajax({
          type: "GET",
          url: "https://jsonplaceholder.typicode.com/users",
          // 如地址失效，可以使用 https://labfile.oss.aliyuncs.com/courses/3774/users.json
          success: function (users) {
            $.each(users, function (i, order) {
              $("#results").append("<li>" + order.name + "</li>");
            });
          },
          error: function () {
            alert("数据请求失败");
          },
        });
        // 添加新数据
        $("#addName").click(function () {
          $.ajax({
            type: "POST",
            url: "https://jsonplaceholder.typicode.com/users",
            // 如地址失效，可以使用 https://labfile.oss.aliyuncs.com/courses/3774/users.json
            data: { name: $("#name").val() },
            success: function (data) {
              $("#results").append("<li>" + data.name + "</li>");
            },
            error: function () {
              alert("数据请求失败");
            },
          });
        });
      });
    </script>
  </head>
  <body>
    <div id="results"></div>
    <!--当前添加的所有名字-->
    名字：<input type="text" id="name" /><!--名字输入框-->
    <button id="addName">添加</button
    ><!--添加名字的按钮-->
  </body>
</html>
```

> 练习题中的数据来自 [JSONPlaceholder](https://jsonplaceholder.typicode.com/)。

最后，开启 8080 端口，打开 Web 服务可以看到以下效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210607-1623035354361)

- 在上面代码中，页面上有对 `div` 标签来显示当前存放的名字信息，另有一个按钮可以添加新的名字。
- 当我们打开页面，可以看到我们发出的 `GET` 请求获得的数据已经加载到页面上了，我们只是获得了 `JSON` 文件中 `name` 的数据。
- 在输入框写入数据，点击按钮会触发点击事件，在函数中我们使用 `POST` 请求获得数据，在当前列表中添加自定义的新名字。

## getJSON

在前面我们学了 `ajax` 方法，当我们要向服务器发送一个 GET 请求并获取 JSON 类型的数据时，写法如下：

```js
$.ajax({
  type: "GET",
  dataType: "json",
  url: url,
  data: data,
  success: success,
});
```

`getJSON` 相当于是以上内容的缩写。

`getJSON` 其实看名字就很好理解，我们分开来看 get 和 JSON。在前面我们学过 get 方法，这里的 get 就是 GET 请求的意思，JSON 就是 JSON 编码了，把两个词合起来理解就是使用 `GET` 请求从服务器加载 `JSON` 格式的数据。

该方法的使用格式如下所示：

```js
$.getJSON(url [,data] [,success(data, textStatus, jqXHR)])
```

参数说明如下：

| 参数                             | 类型        | 描述                                      |
| -------------------------------- | ----------- | ----------------------------------------- |
| url                              | String      | 包含发送请求的 URL 字符串。               |
| data                             | PlainObject | 发送给服务器的字符串或 Key/value 键值对。 |
| success(data, textStatus, jqXHR) | Function    | 当请求成功后执行的回调函数。              |

认识了 `$.getJSON()`，接下来我们做一做练习吧！

#### getJSON 的使用

新建一个 `index6.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>getJSON 方法</title>
    <style>
      ul {
        list-style: none;
      }
      body {
        text-align: center;
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        // 如地址失效，可以使用 https://labfile.oss.aliyuncs.com/courses/3774/users.json
        $("input").click(function () {
          $.getJSON(
            "https://jsonplaceholder.typicode.com/users",
            function (data, textStatus) {
              alert(textStatus);
              $.each(data, function (i, val) {
                $("ul").append("<li>" + val.name + "<li>");
              });
            }
          );
        });
      });
    </script>
  </head>
  <body>
    <input type="button" value="按照JSON格式加载数据" />
    <ul></ul>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务可以看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210608-1623120277016)

- 在上面代码中，我们点击页面上的按钮，触发点击事件。
- 在函数里，使用 `$.getJSON` 向指定地址发出 `GET` 请求获取 `JSON` 格式的数据。
- 使用 `alert(textStatus)` 弹出警告框显示请求数据的状态。
- 使用 `$.each(data,function(kay,val)` 遍历获取的 `JSON` 格式的数据。
- 最后，使用 `$("ul").append('<li>'+val.name+'<li>')` 让数据文件中 key 值为 `name` 的数据项以列表的形式显示在页面上。

## getScript

在前面我们学习了 `ajax` 方法，当我们使用 GET 请求从服务器中加载并执行一个 JavaScript 文件，写法如下：

```js
$.ajax({
  url: url,
  dataType: "script",
  success: success,
});
```

`getScript` 也很容易理解，拆分成 get 和 Script 来看，get 是 `GET` 请求，Script 是 `JavaSctip` 文件，所以合在一起就是使用一个 `GET` 请求从服务器加载并执行一个 `JavaScript` 文件。

其使用格式如下所示：

```js
$.getScript( url [, success(script, textStatus, jqXHR) ] )
```

参数说明如下所示：

| 参数                               | 类型     | 说明                         |
| ---------------------------------- | -------- | ---------------------------- |
| url                                | String   | 包含发送请求的 URL 字符串。  |
| success(script, textStatus, jqXHR) | Function | 当请求成功后执行的回调函数。 |

认识了 `$.getScript`，接下来我们做一做练习吧！

#### getScript 的使用

首先，新建一个 `index7.js` 文件，在文件中写入以下内容。

```js
$(function () {
  $("div").animate({ width: "300px", height: "300px" });
});
```

接着，新建一个 `index7.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>getScript</title>
    <style>
      div {
        width: 50px;
        height: 50px;
        background-color: #b6c9f0;
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("div").click(function () {
          $.getScript("index7.js", function (script, textStatus) {
            $("p").text("请求状态为：" + textStatus);
          });
        });
      });
    </script>
  </head>
  <body>
    <div></div>
    <p></p>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，可以看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210608-1623139593924)

- 页面上有一个 `div` 元素，点击该元素触发 `click` 事件。
- 通过 `$.getScript("index.js",function(script, textStatus)` 我们向 `index.js` 文件发出 `GET` 请求。
- 请求成功后，在 `p` 标签里输出请求状态，并且 `div` 元素根据 `index.js` 文件发生了相应的改变。

## 实验总结

本节实验给大家介绍了 jQuery 中 AJAX 各种方法的使用。这里我们再来总结一下：

- load 方法：让 AJAX 去请求服务器，并从中获得数据，最后将获得的数据放入到指定的元素中。
- get 方法：通过 HTTP GET 请求从服务器请求数据。
- post 方法：用的 POST 请求，它向指定资源提交数据进行处理请求，该请求不会被缓存。
- ajax 方法：是向服务器请求数据，在方法内部我们可以指定是使用 POST 请求还是使用 GET 请求。
- getJSON：请求时获取 JSON 类型的数据。
- getScript：请求从服务器中加载并执行一个 JavaScript 文件。