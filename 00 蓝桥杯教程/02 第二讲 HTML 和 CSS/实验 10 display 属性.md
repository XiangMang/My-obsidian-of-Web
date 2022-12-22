## 实验介绍

Hi！欢迎来到本章节。

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验主要给大家讲解 `display` 的常用属性，我们通过例子带着大家来学习这些属性吧！

#### 知识点

- display 属性

点击底部的 ![img](https://labfile.oss.aliyuncs.com/courses/4421/btn.png)，开始实验之旅吧～

## 认识 display 属性

`display` 属性可以用来设置元素在页面上的排列方式，也可用来隐藏元素。

`display` 属性值的说明如下表所示。

| 属性值       | 说明                     |
| ------------ | ------------------------ |
| block        | 元素以块级方式展示。     |
| inline       | 元素以内联方式展示。     |
| inline-block | 元素以内联块的方式展示。 |
| none         | 隐藏元素。               |

### block 属性值

block 属性值可以让行内元素以块级元素的方式显示在页面上。

其使用格式如下：

```css
display: block;
```

还记得前面学过的行内元素的概念吗？😜 行内元素就是可以和其他元素同处一行的元素，例如 `span` 标签元素。

举个例子～ 👻

新建一个 `index.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      span {
        display: block;
      }
    </style>
  </head>
  <body>
    <span>蓝桥</span><span>云课</span>
  </body>
</html>
```

点击预览，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/c1a5de63e10e287530f4fab49fad93fc-0)

可以看到，原本 `span` 标签是行内元素，却因为设置 `display: block;` 导致「蓝桥」与「云课」分开了。

### inline 属性值

inline 属性值可以让像 `div` 这样的霸道块，接纳其他元素来自己的地盘。

其使用格式如下：

```css
display: inline;
```

举个例子～ 👻

新建一个 `index1.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      div {
        display: inline;
      }
    </style>
  </head>
  <body>
    <div>蓝桥</div>
    <div>云课</div>
  </body>
</html>
```

看，原本霸道的大块头，也被 display 属性给治服了，「蓝桥」与「云课」又在一起了。

### inline-block 属性值

我们的块内元素和行内元素有其独特的优势，在某些情况下，我们想让一个元素既具有块内元素的特点，又具备行内元素的特点。这就要请出 inline-block 属性值来施展这个魔法了。

其使用格式如下：

```css
display: inline-block;
```

那么到底在哪些情况下可以用到这个属性呢？

比如，我们用 `a` 标签来实现导航的时候，`a` 标签虽然可以让元素在一行显示，但若我们想给每个 `a` 标签加上高和宽时发现没有任何效果。这时候用上 `display: inline-block`，它就具备块的特性了。

我们来看个例子～ 👻

新建一个 `index2.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      a {
        text-decoration: none;
        background-color: rgb(95, 118, 160);
        display: inline-block;
        width: 70px;
        height: 30px;
        text-align: center;
      }
    </style>
  </head>
  <body>
    <a href="#">首页</a>
    <a href="#">分类</a>
    <a href="#">展示</a>
    <a href="#">更多</a>
  </body>
</html>
```

点击预览，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/98007bde171abf36ac6c06d0d72d0d64-0)

## none 属性值

none 属性值可以用来隐藏页面上的元素。

使用格式如下：

```css
display: none;
```

举个例子～ 💪

新建一个 `index3.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      div {
        display: none;
      }
    </style>
  </head>
  <body>
    <div>哈哈，看不见我🤫</div>
  </body>
</html>
```

点击预览，可以发现页面上空空的。

## 实验总结

在本节实验中，我们对 `display` 属性的部分属性值做了练习。当然实验中的内容远远不够，同学们需要多加练习才能掌握。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210712-1626055838015)