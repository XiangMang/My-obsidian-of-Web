## 实验介绍

Hi，欢迎来到本章节！

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验我们将为大家解锁 html5 本地存储。

本地存储是指在客户端存储数据，HTML5 为我们提供了两种 API，分别是 localStorage 与 sessionStorage，二者作为 HTML5 新增的特性，它们的使用方法类似，都可以用来存储客户端临时信息，并且二者存储的数据格式均为 key/value 对的数据。区别在与生命周期，localStorage 除非手动清除，否则会永久保存在客户端，而 sessionStorage 仅仅在当前网页回话下有效，在关闭页面或者浏览器就会被清除。

localStorage 对象提供的方法如下：

| 方法               | 说明                              |
| ------------------ | --------------------------------- |
| setItem(key,value) | 保存数据到本地存储                |
| getItem(key)       | 从本地存储获取数据                |
| removeItem(key)    | 根据指定 key 从本地存储中移除数据 |
| clear()            | 清除所有保存数据                  |

sessionStorage 对象提供的方法与 localStorage 对象相同，具体如下：

| 方法               | 说明                              |
| ------------------ | --------------------------------- |
| setItem(key,value) | 保存数据到本地存储                |
| getItem(key)       | 从本地存储获取数据                |
| removeItem(key)    | 根据指定 key 从本地存储中移除数据 |
| clear()            | 清除所有保存数据                  |

> 本节实验会涉及到 JavaScript 的内容，但我们还没有学习 JavaScript，对于 JavaScript 不熟悉的内容先不用管，后面会学到，这里重点关注本地存储。

#### 知识点

- localStorage
- sessionStorage

## localStorage

`localStorage` 对象是 HTML 5 新增的特性，主要用于本地存储。

说到在本地存储数据，大家第一个联想到的应该是 `cookie` 吧。

那么，它们有什么区别呢？👇

#### localstorage 与 cookie 的区别：

- `localStorage` 解决了早期使用 `cookie` 存储遇到的存储空间不足的问题( 每条 `cookie` 的存储空间为 4k )；
- `localStorage` 一般浏览器支持的是 5M 大小，具体存储大小根据浏览器的不同会有所不同。
- 并且相较于 `cookie` 而言，`localStorage` 中的信息不会被传输到服务器。

好了，接下来让我们来看看如何使用 `localStorage` 吧！

`localStorage` 对象提供的方法如下：

| 方法               | 说明                              |
| ------------------ | --------------------------------- |
| setItem(key,value) | 保存数据到本地存储                |
| getItem(key)       | 从本地存储获取数据                |
| removeItem(key)    | 根据指定 key 从本地存储中移除数据 |
| clear()            | 清除所有保存数据                  |

新建一个 `index.html` 文件，然后在文件中写入以下内容：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script>
      // 语句 1： 保存数据到本地存储
      localStorage.setItem("ExpireTime", "1527592757");
      localStorage.UserId = "2021008";
      // 语句 2： 根据指定名称获取本地存储中的数据
      var expireTime = localStorage.getItem("ExpireTime");
      console.log(expireTime);
      // 语句 3： 根据指定名称从本地存储中移除
      localStorage.removeItem("ExpireTime");
      // 语句 4： 清除本地存储中所有数据
      localStorage.clear();
    </script>
  </head>

  <body></body>
</html>
```

最后，启动 8080 端口，打开 Web 服务。

接下来，根据让我们根据执行语句的顺序（对照注释中标注的语句序号阅读）依次来看执行的效果。

#### 执行语句 1

> 语句 1 中的两种方式都可以完成数据的存储。

> 执行完成后，打开浏览器开发人员调试工具，“Application” 面板下，左侧菜单项 “Storage” → “localStorage”。

即可看到所保存的数据，如下所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620464758035)

#### 执行语句 2

> 使用 `getItem()` 方法，根据名称获取 `value` 值，打开浏览器开发人员调试工具，找到 `Console` 面板。

即可看到输出结果：

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620464908515)

#### 执行语句 3

> 使用 `removeItem()` 方法根据指定名称删除数据；

> 执行完成后，再次打开浏览器开发人员调试工具，找到 “Application” 面板下，左侧菜单项 “Storage” → “localStorage”。

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620465032915)

#### 执行语句 4

> 使用 `Clear()` 方法清空所有数据；

> 执行完成后，再次打开浏览器开发人员调试工具，找到 “Application” 面板下，左侧菜单项 “Storage” → “localStorage”。

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620465113632)

## sessionStorage

`localStorage` 和 `sessionStorage` 对象作为 HTML5 新增的特性，都可以用来存储客户端临时信息，并且二者存储的数据格式均为 key/value 键值对数据。

`sessionStorage` 对象提供的方法与 `localStorage` 对象相同，具体如下：

| 方法               | 说明                              |
| ------------------ | --------------------------------- |
| setItem(key,value) | 保存数据到本地存储                |
| getItem(key)       | 从本地存储获取数据                |
| removeItem(key)    | 根据指定 key 从本地存储中移除数据 |
| clear()            | 清除所有保存数据                  |

那么`localStorage` 和 `sessionStorage` 二者有什么区别呢？🤔️

💡 他们的区别在于：

> `localStorage` 的生命周期是永久的，除非用户清除 localStorage 信息，否则这些信息将永远存在。

> `sessionStorage` 的生命周期是临时的，一旦当前窗口或标签页被关闭了，那么通过它存储的数据也就被清空了。

了解了 `sessionStorage` 对象的概念后，接下来让我们一起学习下 `sessionStorage` 的使用吧！

新建一个 `index1.html` 文件，在文件中写入以下内容：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script>
      // 语句 1： 保存数据到本地存储
      sessionStorage.setItem("ShopId", "SH1290333211");
      sessionStorage.ShopNumber = "10";
      // 语句 2： 根据指定名称获取本地存储中的数据
      var ShopId = sessionStorage.getItem("ShopId");
      console.log(ShopId);
      // 语句 3： 根据指定名称从本地存储中移除
      sessionStorage.removeItem("ShopId");
      // 语句 4： 清除本地存储中所有数据
      sessionStorage.clear();
    </script>
  </head>

  <body></body>
</html>
```

启动 8080 端口，打开 Web 服务，接下来，根据执行语句顺序（对照注释中标注的语句序号阅读）依次来看执行效果。

#### 执行语句 1

> 语句 1 中的两种方式都可以完成数据的存储。

> 当语句 1 执行后，打开浏览器开发人员调试工具，找到 Application 面板下，左侧菜单项 Storage → sessionStorage，即可看到所保存的数据。

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620466164502)

🌟 需要注意的是，上图中所出现的 Key 为 `IsThisFirstTime_Log_From_LiveServer` 的数据是由于启动 Web 服务，使用了 LiveServer 所产生，这里不用进行关注。

#### 执行语句 2

> 语句 2 中使用 `getItem()` 方法，根据名称获取 value 值，打开浏览器开发人员调试工具，找到 Console 面板，即可看到输出结果。

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620466212341)

#### 执行语句 3

> 语句 3 中使用 `removeItem()` 方法根据指定名称删除数据，执行完成后，再次打开浏览器开发人员调试工具，找到 “Application” 面板下，左侧菜单项 “Storage” → “sessionStorage”，效果如下。

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620466272275)

#### 执行语句 4

> 语句 4 中使用 `Clear()` 方法清空所有数据，执行完成后，再次打开浏览器开发人员调试工具，找到 “Application” 面板下，左侧菜单项 “Storage” → “sessionStorage”，效果如下。

![图片描述](https://doc.shiyanlou.com/courses/uid1693782-20210508-1620466328117)

## 实验总结

在本节实验中给大家介绍了 HTML5 中本地存储两种 API，分别是 localStorage 和 sessionStorage。

虽然使用 localStorage 和 sessionStorage 对象都可以轻松进行数据的存储与取出，但是两者之间也是有区别的，它们的区别在于页面刷新后，对于 sessionStorage 来说，浏览器完全重，而对于 localStorage，数据仍然保留在浏览器中。