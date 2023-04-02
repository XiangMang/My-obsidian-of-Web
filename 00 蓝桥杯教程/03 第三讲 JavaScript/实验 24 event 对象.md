## 实验介绍

Hi！欢迎来到本章节～

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验给大家介绍 event 对象。

#### 知识点

- type
- keyCode
- shiftKey
- ctrlKey
- altKey
- DOM 0 级事件与 DOM 2 级事件

点击底部的 ![img](https://labfile.oss.aliyuncs.com/courses/4421/btn.png)，开始实验之旅吧～

## event 对象的使用

event 对象，是事件对象，通过事件对象的属性，我们可以了解一个事件的详细情况。

常用的 event 对象属性如下表所示：

| 属性                                                         | 说明              |
| ------------------------------------------------------------ | ----------------- |
| type                                                         | 查看事件类型      |
| [keyCode](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/keyCode) | 查看键值码        |
| shiftKey                                                     | 是否按下 shift 键 |
| ctrlkey                                                      | 是否按下 ctrl 键  |
| altkey                                                       | 是否按下 alt 键   |

> keyCode 属性已经从 Web 标准中删除，这里了解即可。

## type 的使用

这里我们来举个例子吧！👻

新建一个 `index.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>type 的使用</title>
    <style></style>
    <script>
      window.onload = function () {
        var value = document.getElementById("btn");
        value.onclick = function (e) {
          console.log("这是一个" + e.type + "事件"); // 控制台打印事件类型
        };
      };
    </script>
  </head>
  <body>
    <input type="button" value="点击" id="btn" />
  </body>
</html>
```

开启 8080 端口，打开 Web 服务，按下 F12 打开控制台。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210429-1619667190970)

从上图我们可以看出，当点击按钮时，控制台就会打印事件类型。

> 建议使用 chrome 浏览器，由于个人偏好设置，所以控制台的界面有差异。

## 键值码的使用

新建一个 `index1.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>keyCode 的使用</title>
    <style></style>
    <script>
      window.onload = function () {
        var value = document.getElementById("item");
        var value1 = document.getElementById("item1");
        value.onkeydown = function (e) {
          // 判断键入的是否为 shift、alt、ctrl
          if (e.shiftKey || e.altKey || e.ctrlKey) {
            value1.innerHTML = "不能键入 shift|alt|ctrl";
            value1.style.color = "red";
            // 当键入的不为 shift、alt、ctrl 时，输出你的键入码
          } else {
            value1.innerHTML = "你输入的键值码为：" + e.keyCode;
            value1.style.color = "black";
          }
        };
      };
    </script>
  </head>
  <body>
    <input type="text" id="item" />
    <p id="item1"></p>
  </body>
</html>
```

开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210429-1619676740943)

从上面的效果图我们可以看出，当你输入的是 shift、alt、ctrl 键时，输入框的下方会出现红色字样的提示语；当你输入其他键时，会打印其对应的键值码。

## DOM 0 级事件与 DOM 2 级事件

#### DOM 0 级事件的使用

DOM 0 级事件是直接使用像 onclick 这样的方式来实现相应的事件，例如，你可以在 HTML 标签里直接写 onclick 事件或者在 JavaScript 中直接使用 `onclick = function(){}`。

在环境中新建一个 `index2.html` 文件，写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <input type="button" value="点我" onclick="alert('欢迎来到蓝桥云课');" />
  </body>
</html>
```

或者我们可以把上面代码修改成 JavaScript 版的。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <input id="btn" type="button" value="点我" />
    <script>
      document.getElementById("btn").onclick = function () {
        alert("欢迎来到蓝桥云课");
      };
    </script>
  </body>
</html>
```

打开 8080 端口，效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210521-1621589117899)

需要注意的是：在 DOM 0 级事件中，如果有多个事件，后面的事件会覆盖前面的事件，比如下面这个例子。

我们新建一个 `index3.html` 文件，写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <input
      id="btn"
      type="button"
      value="点我"
      onclick="alert('欢迎来到蓝桥云课')"
    />
    <script>
      document.getElementById("btn").onclick = function () {
        alert("嗨！蓝桥");
      };
    </script>
  </body>
</html>
```

实现效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210521-1621589737835)

从上面内容我们可以看出，在按钮上绑定了两个点击事件，但页面上只有第二个点击事件有效果。

那么同学们可能会想，我想执行多个事件该怎么办呢？接下来我们来认识一下 DOM 2 级事件吧！

#### DOM 2 级事件的使用

DOM 2 级事件可以让多个事件执行。

在 DOM 2 级事件里，所有的 DOM 节点都有两个方法，分别是 addEvenetListener 和 removeEventListener。

addEvenetListener 和 removeEventListener 的语法格式如下所示：

```js
target.addEvenetListener(type,listener[,useCapture]);// 添加事件

target.removeEventListener(type,listener[,useCapture]);// 移出事件
```

其参数说明如下所示：

- `type` 是事件类型。
- `listener` 是事件处理的方法。
- `useCapture` 指定事件是否在捕获或冒泡阶段执行，其值为布尔类型，当取值为 true 时，事件句柄在捕获阶段执行，当取值为 false 时，事件句柄在冒泡阶段执行。

了解了 DOM 2 级事件，接下来我们做一做练习吧！

新建一个 `index4.html`，写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <input id="btn" type="button" value="点我" />
    <script>
      document.getElementById("btn").onclick = function () {
        alert("1");
      };
      document.getElementById("btn").addEventListener("click", function () {
        alert("2");
      });
      document.getElementById("btn").addEventListener("click", function () {
        alert("3");
      });
    </script>
  </body>
</html>
```

效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210521-1621591214925)

从上面可以看出，我们给同一个按钮绑定了三个点击事件都显示出来了。

`removeEventListener` 可以移除 `addEventListener` 添加的事件句柄，但使用时需要注意，两者的处理方法必须相同，`removeEventListener` 才会生效，我们来看看下面的示例。新建一个 `index5.html`，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <input id="btn" type="button" value="按钮" />
    <script>
      var btn = document.getElementById("btn");
      btn.addEventListener("click", handler, false);
      function handler() {
        alert("已点击");
        document
          .getElementById("btn")
          .removeEventListener("click", handler, false);
      }
    </script>
  </body>
</html>
```

效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210524-1621828654071)

在上面代码中，如果我们不添加 `removeEventListener` 的话，当你点击按钮，警告框会一直弹出，但添加了 `removeEventListener`，点击一次后，事件被移除，警告框不会被弹出。

## 实验总结

本节实验，我们对 event 对象的五种属性，分别是 type、keyCode、shiftKey、ctrlKey、altKey。最后还给大家简单介绍了 DOM 0 级事件与 DOM 2 级事件。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210712-1626055838015)

下节内容更精彩，跟着我走吧～