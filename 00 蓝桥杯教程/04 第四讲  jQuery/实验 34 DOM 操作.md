## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验给大家介绍 jQuery 中的 DOM 操作。

#### 知识点

- 节点的创建
- 元素的插入
- 元素的删除
- 元素的替换
- 元素的遍历
- 属性操作
- 样式操作
- 内容操作

## 节点的创建

在 JavaScript 中我们已经学过 DOM 相关的操作了，对于 DOM 创建的流程我们简单回顾一下。整个创建流程可分为以下几个步骤：

- 创建元素节点。
- 给元素添加属性。
- 在标签中添加一些文本。
- 把该元素放入整个文档中。

对于 JavaScript 的繁琐步骤，我们的 jQuery 有自己的优化措施。通过使用 `$()` 来创建元素节点，常见的创建有以下三种。

1. 直接创建元素节点。
2. 创建带有文本的元素节点。
3. 创建带有属性的元素节点。

## 直接创建元素节点

使用格式如下所示：

```js
$("<标签名></标签名>");
```

首先，打开你们的线上环境，新建一个 `index.html` 文件，然后使用 `!` 键生成代码模版。

然后，使用以下命令获取 jQuery 库。保存了环境的同学，请忽略此步骤。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js
```

接着，在 `index.html` 文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 创建</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        width: 50px;
        height: 50px;
        margin-top: 20px;
        background-color: cornflowerblue;
      }
    </style>
    <script>
      $(function () {
        $("input").on("click", function () {
          var div = $("<div></div>"); // 创建一个 div 元素
          $("body").append(div); // 将创建的 div 元素放入 body 中
        });
      });
    </script>
  </head>
  <body>
    <input id="btn" type="button" value="创建元素" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618882543794)

- 点击页面上的按钮会触发 `click` 事件。
- 在函数中我们定义了一个名为 `div` 的变量，用来存储创建的 `div` 元素。
- 通过使用 `append` 方法，我们把创建的 `div` 元素添加到页面上了。

## 创建带有文本的元素节点

使用格式如下所示：

```js
$("<标签名>文本内容</标签名>");
```

新建 `index1.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 创建</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        width: 100px;
        height: 100px;
        text-align: center;
        border-radius: 20%;
        margin-top: 20px;
        background-color: rgb(100, 187, 237);
      }
    </style>
    <script>
      $(function () {
        $("input").on("click", function () {
          var div = $("<div>元素宝宝</div>"); // 创建带有文本的元素节点
          $("body").append(div); // 将创建的 div 元素放入 body 中
        });
      });
    </script>
  </head>
  <body>
    <input id="btn" type="button" value="创建元素" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618883226489)

## 创建带有属性的元素节点

使用格式如下所示：

```js
$("<标签名 属性='属性值'>文本内容</标签名>");
```

新建 `index2.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 创建</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        text-align: center;
        border-radius: 100%;
        margin-top: 20px;
      }
    </style>
    <script>
      $(function () {
        $("input").on("click", function () {
          var div = $(
            "<div style='width:50px; height:50px; background-color: #ddffbc'>嗨</div>"
          ); // 创建带有属性的元素节点
          $("body").append(div); // 将创建的 div 元素放入 body 中
        });
      });
    </script>
  </head>
  <body>
    <input id="btn" type="button" value="创建元素" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618886033323)

从上面举的三个例子中我们可以看出，创建一个元素很容易，只要把它存储到一个变量中，然后使用 `append` 方法添加到指定位置即可。`append` 是 DOM 操作中的一个，在这里我们先了解一下，后面的内容中我们会详细介绍。

## 元素的插入

在 jQuery 中，元素插入的方法有两类，分别是：

- 子级插入方法，包括 `prepend()`、`prependTo()`、`append()`、`appendTo()`。
- 同级插入方法，包括 `before()`、`insertBefore()`、`after()`、`insertAfter()`。

## prepend() 与 prependTo()

`prepend()` 与 `prependTo()` 是在元素**子级**的**开头**插入元素。

`prepend` 方法的语法格式为：

```js
// 在 A 元素的子级最前面的位置插入B
$(A).prepend(B);
```

`prependTo` 方法的语法格式为：

```js
// 在 A 元素的子级最前面的位置插入B
$(B).prependTo(A);
```

`prepend()` 与 `prependTo()` 起到的作用是一样的，只不过使用格式是颠倒的。

新建 `index3.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>prepend() 与 prependTo() 的使用</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        color: cornflowerblue;
      }
    </style>
    <script>
      $(function () {
        // prepend 方法的使用
        $("#div1").one("click", function () {
          var $span = $("<span>欢迎来到</span>");
          $("#div1").prepend($span);
        });
        // prependTo 方法的使用
        $("#div2").one("click", function () {
          var $span = $("<span>欢迎来到</span>");
          $($span).prependTo("#div2");
        });
      });
    </script>
  </head>
  <body>
    <div id="div1">蓝桥云课</div>
    <div id="div2">jQuery 学习</div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618889726511)

从上面的例子中我们可以看出 `prepend` 方法 和 `prependTo` 方法起到的作用是一样的，但是两者的用法是颠倒的。

## append() 与 appendTo()

`append()` 与 `appendTo()` 是在元素**子级**的**尾部**插入元素。

`append` 方法的语法格式为：

```js
// 在 A 元素子级的最后面位置追加 B
$(A).append(B);
```

这里的 A 是待插入的目标元素，B 是我们要插入的内容。

`appendTo` 方法的语法格式为：

```js
// 在 A 元素子级的最后面位置追加 B
$(B).appendTo(A);
```

这里的 B 是待插入的目标元素，A 是我们要插入的内容。

`append` 和 `appendTo` 起到的作用也是一样的，只不过使用格式是颠倒的。

新建 `index4.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>append() 与 appendTo()的使用</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        color: cornflowerblue;
      }
    </style>
    <script>
      $(function () {
        // append 方法的使用
        $("#div1").one("click", function () {
          var $span = $("<span>蓝桥云课</span>");
          $("#div1").append($span);
        });
        // appendTo 方法的使用
        $("#div2").one("click", function () {
          var $span = $("<span>jQuery</span>");
          $($span).appendTo("#div2");
        });
      });
    </script>
  </head>
  <body>
    <div id="div1">欢迎来到</div>
    <div id="div2">欢迎学习</div>
  </body>
</html>
```

接着，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618895654687)

在上面代码中，我们使用 `append` 方法和 `appendTo` 方法分别给页面上的两对 `div` 元素的尾部插入新的元素，两个方法的使用也是颠倒的。

## before() 与 insertBefore()

`before()` 与 `insertBefore()` 是在该元素的**前面**插入元素。

`before` 方法的语法格式为：

```js
// 在 A 的前面插入 B
$(A).before(B);
```

`insertBefore` 方法的语法格式为：

```js
// 在 A 的前面插入 B
$(B).insertBefore(A);
```

`before` 和 `insertBefore` 方法的作用也是相同的，只是使用格式上是颠倒的。

新建 `index5.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>before() 与 insertBefore()</title>
    <script src="https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js"></script>
    <style>
      div {
        border: 1px solid #000;
        margin: 10px;
      }
    </style>
    <script>
      $(function () {
        var i = 0;
        var j = 0;
        // before 的使用
        $("#div1").click(function () {
          i++;
          var $div = $(`<div>我喜欢 jQuery${i}</div>`);
          $("#div1").before($div);
        });
        // insertBefore 的使用
        $("#div2").click(function () {
          j++;
          var $div = $(`<div>I like jQuery${j}</div>`);
          $($div).insertBefore("#div2");
        });
      });
    </script>
  </head>
  <body>
    <div id="div1">before</div>
    <div id="div2">insertBefore</div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/3774/1328821/ebbc4f2b732b1ecfd9a436923c8ca4fd-0)

- 在上面的代码中，我们点击 `before`，触发点击事件，通过 `$("#before").before($div)` 我们把待插入的 `div` 元素插入到了 id 名为 before 的元素前面。
- 我们点击 `insertBefore`，触发点击事件，通过 `$($div).insertBefore("#insertBefore")` 我们把待插入的 `div` 元素插入到了 id 名为 insertBefore 的元素前面。

## after() 与 insertAfter()

`after()` 与 `insertAfter()` 是在元素的**后面**插入元素。

`after` 方法的语法格式为：

```js
// 在 A 的后面插入 B
$(A).after(B);
```

`insertAfter` 方法的语法格式为：

```js
// 在 A 的后面插入 B
$(B).insertAfter(A);
```

`after` 和 `insertAfter` 方法的作用也是相同的，只是使用格式上是颠倒的。

新建 `index6.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>after() 与 insertAfter()</title>
    <script src="https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js"></script>
    <style>
      div {
        border: 1px solid #000;
        margin: 10px;
      }
    </style>
    <script>
      $(function () {
        var i = 0;
        var j = 0;
        // after 的使用
        $("#div1").click(function () {
          i++;
          var $div = $(`<div>我喜欢 jQuery${i}</div>`);
          $("#div1").after($div);
        });
        // insertAfter 的使用
        $("#div2").click(function () {
          j++;
          var $div = $(`<div>I like jQuery${j}</div>`);
          $($div).insertAfter("#div2");
        });
      });
    </script>
  </head>
  <body>
    <div id="div1">after</div>
    <div id="div2">insertAfter</div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/3774/1328821/479bce0df4d0a828ae37d700e0fb5069-0)

- 在上面代码中，点击 `after`，使用 `$("#after").after($div)` 把待插入的 `div` 元素插入到 id 名为 `after` 元素外部的尾部。
- 点击 `insertAfter`，使用 `$($div).insertAfter("#insertAfter")` 把待插入的 `div` 元素插入到 id 名为 `insertAfter` 元素外部的尾部。

## 元素的删除

在 jQuery 中，删除元素常用的有如下两种方法：

- remove()
- empty()

接下来我们就来学一学这些方法吧！

## remove 方法

`remove` 方法可以将指定的元素及其子元素删除。

其语法格式为：

```js
$().remove();
```

新建 `index7.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>remove()</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        width: 100px;
        height: 40px;
        text-align: center;
        margin-top: 20px;
        background-color: cornflowerblue;
      }
    </style>
    <script>
      $(function () {
        $("input").click(function () {
          $("div").remove();
        });
      });
    </script>
  </head>
  <body>
    <div>remove me</div>
    <input type="button" value="删除" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618898868830)

在上面代码中，我们点击页面上的删除按钮，会触发 `click` 事件，通过使用 `remove` 方法把页面上的 `div` 元素块给移除掉。

## empty 方法

empty 方法是用来清空指定元素的后代元素和内容的。

其语法格式为：

```js
$().empty();
```

新建一个 `index8.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>empty 的使用</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        width: 290px;
        height: 150px;
        text-align: center;
        margin-top: 20px;
        border: 1px solid #cee6b4;
      }
    </style>
    <script>
      $(function () {
        $("div").click(function () {
          $(this).empty();
        });
      });
    </script>
  </head>
  <body>
    <div>
      <h3>四时田园杂兴</h3>
      <p>谷雨如丝复似尘，煮瓶浮蜡正尝新。</p>
      <p>牡丹破萼樱桃熟，未许飞花减却春。</p>
    </div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618903860680)

## 元素的替换

`replaceWith` 方法和 `replaceAll` 方法都可以用来把指定元素替换成其他元素，只是在使用格式上有些差别。

其语法格式为：

```js
// 将 A 替换为 B
$(A).replaceWith(B);

// 将 A 替换为 B
$(B).replaceAll(A);
```

新建一个 `index9.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>元素替换</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        width: 290px;
        height: 150px;
        text-align: center;
        margin-top: 20px;
        border: 1px solid #cee6b4;
      }
    </style>
    <script>
      $(function () {
        $("div").click(function () {
          var $poem1 = $("<p>柳花深巷午鸡声，桑叶尖新绿未成。</p>");
          var $poem2 = $("<p>坐睡觉来无一事，满窗晴日看蚕生。</p>");
          $("#poem1").replaceWith($poem1);
          $($poem2).replaceAll("#poem2");
        });
      });
    </script>
  </head>
  <body>
    <div>
      <h3>四时田园杂兴</h3>
      <p id="poem1">谷雨如丝复似尘，煮瓶浮蜡正尝新。</p>
      <p id="poem2">牡丹破萼樱桃熟，未许飞花减却春。</p>
    </div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618905154743)

## 元素的遍历

在 jQuery 中，`each` 方法是用于元素遍历的。

其语法格式为：

```js
$().each(function (index, element) {});
```

`each` 方法会接收一个匿名函数作为参数，函数中的 `index` 表示元素的索引号；而函数中的 `element` 表示当前元素。

新建一个 `index10.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>each 的使用</title>
    <script src="jquery-3.6.0.min.js"></script>
    <style>
      div {
        display: inline-flex;
        width: 50px;
        height: 50px;
        margin: 20px 0 10px 0;
        border: 1px solid #78c4d4;
      }
    </style>
    <script>
      $(function () {
        var colors = ["#ffc478", "#d3e0dc", "#fce2e1", "#aee1e1"];
        $("div").click(function () {
          $("div").each(function (index, element) {
            $(this).css("background-color", colors[index]);
          });
        });
      });
    </script>
  </head>
  <body>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210420-1618909765054)

## 属性操作

本文给大家介绍两种属性操作：

- 获取指定元素的属性
- 删除指定元素的属性

下面我们一一来学习吧～

## attr 方法

`attr` 方法可以用来获取指定元素的属性值，也可以用来设置指定属性的属性值。

其语法格式为：

```js
jQuery对象.attr("属性名"); // 获取属性
jQuery对象.attr("属性名", "属性值"); // 修改属性
```

我们来举个例子～

使用以下命令下载需要的图片。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3774/bird1.jpg

wget https://labfile.oss.aliyuncs.com/courses/3774/bird2.jpg
```

新建一个 `index11.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>attr 的使用</title>
    <style>
      input {
        width: 200px;
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("input").click(function () {
          //1. 使用 attr 方法来获取 width 的属性值
          alert("图片的宽为：" + $("img").attr("width"));
          // 2.使用 attr 方法来修改 src 的属性值
          $("img").attr("src", "bird2.jpg");
          // 3. attr 可以传入 json 来同时修改多个属性
          $("img").attr({ src: "bird2.jpg", width: "400px", height: "300px" });
        });
      });
    </script>
  </head>
  <body>
    <img width="200px" height="150px" src="bird1.jpg" /><br />
    <input type="button" value="切换" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619070284052)

- 在上面代码中，页面上有一张图片和一个按钮。
- 当我们点击页面上的按钮时，会触发 `click` 事件，页面上会弹出警告框。
- 通过使用 `$("img").attr("width")` 会获取到图片的宽度，输出到警告框中。
- 通过使用 `$("img").attr("src","bird2.jpg")` 把 img 中原有 src 的属性值替换为 `bird2.jpg` 了。

## removeAttr 方法的使用

`removeAttr` 方法可以删除指定元素的某个属性。

其语法格式为：

```js
jQuery对象.removeAttr("属性名");
```

新建一个 `index12.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>removeAttr 的使用</title>
    <style>
      body {
        text-align: center;
      }
      input {
        width: 200px;
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("input").click(function () {
          alert("删除图片！！");
          $("img").removeAttr("src"); // 删除 img 的 src 属性
        });
      });
    </script>
  </head>
  <body>
    <img width="200px" height="150px" src="bird1.jpg" /><br />
    <input type="button" value="删除图片" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619071415517)

点击页面上的删除按钮，会触发 `click` 事件，弹出警告框显示“删除图片！！”，使用 `removeAttr("src")` 移除 src 属性，移出之后，图片无法正常显示到图片上。

## 样式操作

这里给大家介绍四种样式操作的方法，分别是：

- css 方法
- addClass 方法
- removeClass 方法
- toggleClass 方法

下面我们一一来学习吧～

## css 方法的使用

`css` 方法可以用来获取指定属性的属性值，也可以用来设置属性值。

```js
// 获取指定属性的属性值
$().css("属性名");

// 设置属性值
$().css("属性名", "属性值");
```

新建一个 `index13.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>css 方法的使用</title>
    <style>
      div {
        width: 100px;
        height: 100px;
        background-color: rgb(100, 198, 237);
      }
      input {
        width: 100px;
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("div").click(function () {
          alert("背景颜色为：" + $("div").css("background-color")); // 获取背景颜色的属性值
        });
        $("input").click(function () {
          $("div").css("border", "4px solid #94ebcd"); // 给 div 元素添加一个边框
        });
      });
    </script>
  </head>
  <body>
    <div></div>
    <br />
    <input type="button" value="添加边框" />
  </body>
</html>
```

最后，8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619075736204)

- 在上面代码中，当我们点击「添加边框」的按钮时，会触发 `$("input").click`，给 `div` 元素块添加边框。
- 当我们点击 `div` 元素块时，会触发 `$("div").click`，页面上弹出警告框，通过 `$("div").css("background-color")` 可以获取到 `div` 元素的背景颜色编码值。

## addClass 方法的使用

addClass 方法是用来添加类选择器的。

其使用格式为：

```js
$().addClass("类名");
```

新建一个 `index14.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>addClass 方法的使用</title>
    <style>
      div {
        width: 100px;
        height: 100px;
        border-radius: 100px;
        border: 1px solid #c7ffd8;
      }
      .circle {
        background-image: radial-gradient(#ffe6e6, #c6c9ff, #8ad7c1);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("div").click(function () {
          $(this).addClass("circle"); // 给 div 添加一个 circle 选择器
        });
      });
    </script>
  </head>
  <body>
    <div></div>
  </body>
</html>
```

接着，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619078404706)

在上面代码中，点击页面上的圆环，触发 `click` 事件；通过使用 `addClass` 给圆环添加 `class="circle"` 的样式属性。

## removeClass 方法的使用

`removeClass` 方法可以用来移除已有的类选择器。

其语法格式为：

```js
$().removeClass("类名");
```

新建一个 `index15.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>removeClass 方法的使用</title>
    <style>
      div {
        width: 100px;
        height: 100px;
        border-radius: 100px;
        border: 1px solid #c7ffd8;
      }
      .circle {
        background-image: radial-gradient(#ffe6e6, #c6c9ff, #8ad7c1);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("div").click(function () {
          $(this).removeClass("circle"); // 移除类选择器
        });
      });
    </script>
  </head>
  <body>
    <div class="circle"></div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619082430344)

在上面代码中，当点击页面上的 `div` 元素，会触发 `click` 事件，通过 `removeClass` 会移除 `class="circle"` 的样式。

## toggleClass 方法的使用

`toggleClass` 方法是用来切换类选择器的。

其使用格式为：

```js
$().toggleClass("类名");
```

新建一个 `index16.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>toggleClass 方法的使用</title>
    <style>
      div {
        width: 100px;
        height: 100px;
        border-radius: 100px;
        border: 1px solid #c7ffd8;
      }
      .circle {
        background-image: radial-gradient(#ffe6e6, #c6c9ff, #8ad7c1);
      }
      .circle1 {
        background-image: linear-gradient(#1687a7, #583d72, #b8de6f);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("div").click(function () {
          $(this).toggleClass("circle1");
        });
      });
    </script>
  </head>
  <body>
    <div class="circle"></div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210422-1619083187496)

通过使用 `toggleClass` 让 `div` 元素的 `circle1` 样式在添加和移除之间切换，没有 `circle1` 这个类就加上，有则移除。

## 内容操作

本文会给大家介绍以下三种内容操作的方法：

- html 方法
- text 方法
- val 方法

下面我们一一来学习吧～

## html 方法的使用

`html` 方法可用来获取 HTML 文档中指定元素内部的元素标签和标签中的内容，也可以给元素添加内容。

其语法格式为：

```js
// 获取元素内容
$().html();
// 设置元素内容
$().html("内容");
```

新建一个 `index17.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>html 方法的使用</title>
    <style>
      div {
        width: 300px;
        height: 150px;
        margin-top: 10px;
        text-align: center;
        border: 1px solid rgb(27, 179, 128);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("#poem1").click(function () {
          alert($(this).html());
        });
        $("#poem2").click(function () {
          $(this).html(
            "<h3>客中行</h3><p>兰陵美酒郁金香，玉碗盛来琥珀光。</p><p>但使主人能醉客，不知何处是他乡。</p>"
          );
        });
      });
    </script>
  </head>
  <body>
    <div id="poem1">
      <h3>山中问答</h3>
      <p>问余何意栖碧山，笑而不答心自闲。</p>
      <p>桃花流水窅然去，别有天地非人间。</p>
    </div>
    <div id="poem2"></div>
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210423-1619141542554)

- 在上面代码中，点击第一个 `div` 元素，会弹出警告框，通过 `html()` 会获取该 `div` 元素中的子元素及内容。
- 当点击第二个 `div` 元素，通过使用 `html()` 会把 `h3`、`p` 元素中内容放入到该元素中。

## text 方法的使用

`text` 方法可以获取指定标签里的文本，也可以为指定标签添加文本。

其语法格式为：

```js
// 获取指定标签中的文本
$().text();
// 给指定标签设置文本
$().text("内容");
```

新建一个 `index18.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>text 方法的使用</title>
    <style>
      div {
        width: 300px;
        height: 150px;
        margin: 10px 0 10px 0;
        text-align: center;
        border: 1px solid rgb(27, 179, 128);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("#poem1").click(function () {
          alert($(this).text());
        });
        $("input").click(function () {
          $("h3").text("山中问答");
        });
      });
    </script>
  </head>
  <body>
    <div id="poem1">
      <h3></h3>
      <p>问余何意栖碧山，笑而不答心自闲。</p>
      <p>桃花流水窅然去，别有天地非人间。</p>
    </div>
    <input type="button" value="添加标题" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210423-1619142085384)

> 注意：`html` 方法和 `text` 方法的区别在于，`html` 方法是带着标签一起操作，而 `text` 方法操作的是标签里的文本。

## val 方法的使用

`val` 方法用于获取表单元素的值，也可以给表单元素设置值。

新建一个 `index19.html` 文件，在文件中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>val 方法的使用</title>
    <style>
      div {
        width: 300px;
        height: 150px;
        margin: 10px 0 10px 0;
        text-align: center;
        border: 1px solid rgb(27, 179, 128);
      }
    </style>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
      $(function () {
        $("#get").click(function () {
          alert($("#name").val());
        });
        $("#set").click(function () {
          $("#phone").val("1234567");
        });
      });
    </script>
  </head>
  <body>
    <div>
      <input type="text" value="请输入你的名字" id="name" />
      <input type="phone" id="phone" />
    </div>
    <input type="button" value="获取名字" id="get" />
    <input type="button" value="设置电话" id="set" />
  </body>
</html>
```

最后，开启 8080 端口，打开 Web 服务，会看到以下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210423-1619144002295)

- 在上面代码中，点击「获取名字」的按钮，通过 `$("#name").val()` 可以获取输入框中的当前内容。
- 点击「设置电话」的按钮，通过 `$("#phone").val("1234567")` 可以给 `id="phone"` 元素里的输入框添加内容为 1234567。

## 实验总结

本节实验给大家介绍了几种常用的 DOM 操作。分别是：

- 节点的创建：使用 `$()` 来创建元素节点。
- 元素的插入：分为子级插入和同级插入。
  - 子级插入方法，包括 `prepend()`、`prependTo()`、`append()`、`appendTo()`。
  - 同级插入方法，包括 `before()`、`insertBefore()`、`after()`、`insertAfter()`。
- 元素的删除：使用 `remove()` 或者 `empty()` 方法可以删除元素。
- 元素的替换：使用 `replaceWith()` 或者 `replaceAll()` 可以替换元素。
- 元素的遍历：使用 `each` 可以遍历元素。
- 属性操作：使用 `attr()` 设置属性、获取属性和使用 `removeAttr` 删除属性。
- 样式操作：使用 `css()` 获取样式，使用 `addClass()` 添加样式，使用 `removeClass()` 移除样式，使用 `toggleClass()` 切换类选择器。
- 内容操作：使用 `html()` 获取指定元素内部的元素标签和标签中的内容 ，使用 `text()` 获取指定标签里的文本或者给指定标签添加文本，使用 `val()` 获取表单元素的值或者给表单元素设置值。
