## 实验介绍

Hi，欢迎来到本章节！

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

你将入住 HTML 之家，为了以后更好地与 HTML 大家庭的成员相处，我先当个引路人，带你熟悉一下 HTML 家族中的重要成员。

#### 知识点

- html 标签
- head 标签
- title 标签
- meta 标签
- body 标签

点击底部的 ![img](https://labfile.oss.aliyuncs.com/courses/4421/btn.png)，开始实验之旅吧～

## 什么是标签

本节实验的题目是标签大家族，那么「标签」与 HTML 之间有何关联呢？🤔

想象一下： 打游戏时，有各种装备，每种装备的功能是不同的，不同的标签就像游戏装备一样，各有各的功能。

下面我们来认识一下 HTML 中的标签吧！

![酷](https://static.shiyanlou.com/lanqiao/frontend/dist/img/cool.b2a3fd2.png)

👉 请打开右边的环境，在环境中建立一个 `index.html` 文件，输入一个英文 `!`，然后按 `tab` 键生成模版。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/bda7b4d8149669ae75ef7979d7bacaf8-0)

从上图可以看到，所有的字符内容都是用尖括号 `<` 和 `>` 括起来的，这样的内容被称为**标签**，其中 `<>` 代表开始标签，`</>` 代表结束标签。下面放个图，帮助大家更好滴理解标签～

![图片描述](https://doc.shiyanlou.com/courses/4384/1347963/bb5b828ebc68cf683aebea68bab4b9af-0)

上图展示的是双标签元素，其实 HTML 标签有两种形式：

**1. 双标签**

```html
<标签名>内容</标签名>
```

双标签是指标签是成对出现的，也就是有一个开始标签和一个结束标签，开始标签用 `<标签名>` 表示，结束标签用 `</标签名>` 表示，只有一对标签一起使用才能表示一个具体的含义。例如 `<html></html>`。

**2. 单标签**

单标签没有开标签和闭标签之分，它只有一个标签，其写法如下所示：

```html
<标签名>
```

或者

```html
<标签名/>
```

例如，在 HTML 中有个换行标签 `<br/>`，使用该标签可以给文字段落换行，效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/0dc67359c444dc370be49df641e6daf9-0)

总结一下：HTML 就是由各种各样的标签组成的。

下面我们来认识一下，模版中的几个标签吧！👇

## html标签

在介绍 `html` 标签之前，我们先说说 `<!DOCTYPE html>` 的意思，它是文档类型声明标签，用于一个文档类型的声明，`DOCTYPE` 用来保证文档能够正确被读取，`html` 声明这是一个 html 文档。

`html` 标签标识该文档为 HTML 文档。它相当于是一个两层楼的房子框架，第一层是 `body` 楼，居民住在不同类型的房间中，第二层是 `head` 楼，里面放着居民的信息文件。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/25bda4ec7624f812e8816b14a44339ef-0)

> 房子图片来自于 [ICONS8](https://icons8.com/)。

`<html>` 标签置于 HTML 文档最前边，用来标识 HTML 文档的开始，而 `</html>` 标签恰好相反，它放在 HTML 文档最后边，用来标识 HTML 文档的结束。

两个标签必须成对使用，网页中其他的所有标签都应该放在 `<html>` 和 `</html>` 标签之间。

基本语法：

```html
<html>
  ...
</html>
```

## head标签

`head` 标签是头部元素的家 🏠 ，头部元素是对页面的一些基本描述。在上面的模板中，我们可以看到 `head` 标签里有两个成员，`title` 标签和 `meta` 标签。其实不止这两个，常见的头部标签如下表所示：

| 标 签      | 描 述                                                        |
| ---------- | ------------------------------------------------------------ |
| `<title>`  | 定义页面标题内容。                                           |
| `<meta>`   | 有关文档本身的元信息，例如：文档的作者，用于查询的关键词，关于文档的描述等。 |
| `<style>`  | 定义 CSS 层叠样式表的内容。                                  |
| `<link>`   | 定义外部文件的链接，最常见的用途是链接外部样式表。           |
| `<script>` | 定义页面中程序脚本的内容。                                   |

## meta标签

`meta` 标签的功能是提供关于页面的元信息，能够提供文档作者、关键字、描述等多种信息，在 HTML 的头部可以包括任意数量的 `meta` 标签。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

其中，`name`、`content` 被称为属性，`viewport` 和 `width=device-width, initial-scale=1.0` 被称为属性值。

例如：我们添加一个作者的信息。

```html
<meta name="author" content="Lee,1234567@qq.com" />
```

除了上面介绍的属性，这里再给大家介绍一个字符编码的属性，大家知道我们现在常用的是 UTF-8 编码，这种通用的编码使我们的页面内容能够在不同情况下被正确的解析。

在 `meta` 标签中，我们使用 `charset` 属性来规定字符编码，在解析文档时，会告诉浏览器我们使用的编码形式。使用如下：

```html
<meta charset="utf-8" />
```

这里只是简单介绍了 `meta` 标签，若想了解更多内容，请阅读[文档级元数据](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)。

## title标签

`<title>` 标签是用来设置页面标题的，我们随便打开一个网页都可见其标题。例如，下方我打开了「蓝桥云课」和「蓝桥杯大赛」的官网，可以看见两个网站的标题是不同的。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/1e869009705698c26affb77e8912d435-0)

它有以下几个方面的用处：

1. 可以在浏览者保存该页面时成为默认的保存文件名。
2. 可以在浏览者将该网址添加进收藏夹时成为收藏夹中该网址的名称。
3. 方便搜索引擎索引页面。
4. 搜索引擎显示的页面标题往往就是网页 `<title>` 标签的内容。

在我们的 HTML 模板中 `<title>Document</title>`，意思是设置页面的标题为 Document，我们如下修改这个默认标题，然后来看看该标题会显示在哪里。

```html
<title>我是蓝桥宝宝</title>
```

这里不能用预览效果查看，因为预览只能预览显示在页面上的内容，而 `head` 标签中的内容并不会显示在页面上，所以这里我们需要打开浏览器，其步骤为：

第一步：在编辑区域鼠标右击选择 Open with Live Server。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/e2caa3b2e5f789bbdfd33df006496a21-0)

当弹出如下所示窗口，说明 8080 端口被成功启动。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/2c51e94e94643158a1d6667fa7a66b32-0)

第二步：点击右侧箭头符号，选择 Web 服务。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/c7aabb6b0fff6e697098c828341df2d2-0)

我们可以看到如下所示的位置会显示网页标题。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/1a7041819a61d92aac44800a7083fe73-0)

## body标签

`body` 标签界定了 HTML 文档的主体。在 `<body>` 和 `</body>` 之间放的是要显示在页面上的所有内容，如文本、超链接、图像、表格和列表等。

基本语法：

```html
<body>
  ...
</body>
```

例如，我们在 `body` 标签中写入以下内容：

```html
<body>
  欢迎来到 body 楼！
</body>
```

页面显示效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4384/1347963/bffd2363bf2501713f62e8bf9a82503d-0)

## 实验总结

总结一下本节实验学习的内容，我带大家认识了 HTML 家族中几个重要结构元素。

- 一个基本的 HTML 模版需要 `<!DOCTYPE html>` 去声明文档的类型。
- 然后需要一对 `html` 标签去搭建 HTML 房子的框架。
- 在房子里面有两层楼，头部信息住在 `head` 标签楼里，页面显示内容住在 `body` 楼里。

在未来我们会认识很多住在 `body` 中的元素，尽情期待吧！

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210712-1626055838015)

跟着我继续走吧～

