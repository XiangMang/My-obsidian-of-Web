## 实验介绍

终于等到你！

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

前面的内容带大家进入了 HTML 标签之家，我们跟众多标签都聊过天，知道它们日常主要干什么活儿。

同学们有没有觉得，虽然我们学了这么多标签，但并不能实现一个精美的网页，目前我们能做的只是把这些标签堆在页面上，并不能按照我们想要的方式来布局。🤢

CSS 就是为了解决这个问题而诞生的。

CSS 就像一个魔法师，把朴实无华的茅草屋变成了豪宅。😉

跟我一起拿起魔法棒，来学习魔法吧！

本节实验主要给大家介绍 CSS 的基础语法。

#### 知识点

- 选择器
- 背景样式
- 文本属性
- 字体属性
- 链接中的伪类
- 列表样式

## 选择器

何为选择器呢？🤔 在 CSS 中，选择器是用来给指定标签设置样式的容器。

比如，魔法师把指定颜色的布条子装到魔法袋中，然后念过魔法语后，从袋子中拿出一只兔子 🐰。

CSS 中有以下三种基本选择器：

- 标签选择器
- 类选择器
- id 选择器

### 标签选择器

我们来练习一个吧！💪

现在需要完成这样的渲染，将页面的背景色设置成蓝色，将字体设置为白色，把文字居中显示。

新建一个 `index.html` 文件，在其中写入以下内容：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        background-color: deepskyblue;
        color: floralwhite;
      }
      h1 {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <h1>学习 Web 前端技术课程</h1>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616391222257)

> 在选择器里面的内容是「属性:属性值」，在后面我们会学习很多属性，这里我们先体验一下选择器的作用。

### 类选择器

在定义类选择器时，需要用点号和类名来定义，而在使用该类选择器时，需要在使用该类选择器的元素标签中，增加 class="类名"的属性（不包括点号），表示该标签使用了指定的类选择器。

例如：蓝桥云课的一段代码。

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/756c41011206e71f0a3db9240b618270-0)

其语法格式为：

```css
.类名 {
  属性名: 属性值;
}
```

我们来练习一个吧！💪

现在需要完成这样的渲染，将列表中的其中两项设置为蓝色字体。

新建一个 `index1.html` 文件，在其中写入以下代码。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .book {
        color: lightskyblue;
      }
    </style>
  </head>
  <body>
    图书分类：
    <ul>
      <li>经典</li>
      <li>文艺</li>
      <li class="book">科幻</li>
      <li class="book">童书</li>
      <li>生活</li>
    </ul>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616392005632)

### id 选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。

在定义 id 选择器时，需要用 “#” 号和 id 名来定义选择器，而在使用该 id 选择器时，需要在 HTML 标签元素中，增加 id="id 名"的属性（不包括 “#” 号），指定这个 HTML 元素的 id，这个 id 在 HTML 文档中是**唯一**的。

它的使用与类选择器类似，语法格式如下：

```css
#id 选择器名 {
  属性: 属性值;
}
```

我们来练习一个吧！💪

现在需要完成这样的渲染，将列表中的其中一项设置为蓝色字体。

新建一个 `index2.html` 文件，在其中写入以下代码。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      #book {
        color: lightskyblue;
      }
    </style>
  </head>
  <body>
    图书分类：
    <ul>
      <li>经典</li>
      <li>文艺</li>
      <li id="book">科幻</li>
      <li>童书</li>
      <li>生活</li>
    </ul>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616392169104)

学习了这么多选择器，同学们有没有想过一个问题：当我们对某个元素用多种不同的选择器时，计算机该听哪个选择器的话呢？🤔

其实呀，我们的选择器是有优先级的，下面我们来看看这三种选择器有怎样的关系。

### 选择器的优先级

在 HTML 中选择器的优先级为：**id 选择器 > 类选择器 > 标签选择器**。

我们通过例子来看看吧！

新建一个 `index3.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      #idSelector {
        color: rgb(48, 179, 202); /*蓝色*/
      }
      .classSelector {
        color: rgb(102, 160, 76); /*绿色*/
      }
      p {
        color: rgb(123, 52, 133); /*红色*/
      }
    </style>
  </head>
  <body>
    <p id="idSelector" class="classSelector">蓝桥云课</p>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210508-1620452918399)

同学们请继续思考，固定的优先级规则可以打破吗？🤔

### !important 的介绍

可以的，当你在样式声明中加入 !important 规则时，它会改变样式声明的优先级。

我们来看看是如何使用的。👻

新建一个 `index4.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      #idSelector {
        color: rgb(48, 179, 202);
      }
      .classSelector {
        color: rgb(102, 160, 76);
      }
      p {
        color: rgb(123, 52, 133) !important;
      }
    </style>
  </head>
  <body>
    <p id="idSelector" class="classSelector">蓝桥云课</p>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210508-1620453470392)

> 注意：在日常开发中我们尽量不要使用 !important。

除了上述三种基本选择器外，我们还有两种常用的选择器，分别是：

- 后代选择器
- 群组选择器

后代选择器主要可以更加精确定位到指定元素，以免与其他元素混淆。

群组选择器主要用来给多个不同的元素添加相同的 CSS 样式。

下面我们来看看具体用法。

### 后代选择器

后代选择器是选择标签内部中某一标签的所有元素，其包括子元素及其他后代元素。

在使用后代选择器时，父标签名和后代标签名必须用空格隔开，这样才能识别是某个标签内部的后代元素。

我们来举个例子！😉

新建一个 `index5.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      #paragraph p {
        color: lightskyblue;
      }
    </style>
  </head>
  <body>
    <div id="paragraph">
      <p>这是一个段落</p>
    </div>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616394021601)

在上面代码中，使用 `#paragraph p` 可以获取到 `class` 名为 `paragraph` 的 `div` 元素中的子元素 `p` 标签，我们给该标签中的文字内容设置了字体颜色。

### 群组选择器

群组选择器是用于同时对几个选择器进行相同的样式设置。

在使用群组选择器时，两个选择器之间必须要用英文逗号隔开。

新建一个 `index6.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      div,
      span {
        color: lightskyblue;
      }
    </style>
  </head>
  <body>
    <div>段落一</div>
    <span>段落二</span>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616394362544)

在上面代码中，使用 `div,span` 给 `div` 标签和 `span` 标签设置了相同的字体颜色。

## 背景样式

背景样式属性用于定义 HTML 元素的背景色、背景图片，同时还可以进行背景定位、背景图片重复、背景图片固定。

在本节实验中会学到以下几种背景属性：

- background-color
- background-image
- background-size
- background-position
- background-repeat

### background-color 属性

`background-color` 属性可以给指定标签元素设置背景色。

举个例子！👻 我们给 `body` 元素设置一个背景颜色。

新建一个 `index7.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        background-color: yellowgreen;
      }
    </style>
  </head>
  <body></body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616396931028)

### background-image 和 background-size 属性

`background-image` 属性可以把图像插入背景。`background-size` 属性可以给背景图设置大小。

举个例子！👻 我们给 `body` 元素设置一个背景图像。

使用以下命令获取图片。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3773/moon.jpg
```

新建一个 `index8.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        background-image: url("moon.jpg");
        background-size: 300px 300px;
      }
    </style>
  </head>
  <body></body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616398620990)

### background-position 属性

通过 `background-position` 属性，可以改变图像在背景中的位置。

我们在 `index9.html` 中加入 `background-position` 属性，设置属性值为居中。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        background-image: url("moon.jpg");
        background-size: 300px 300px;
        background-position: center;
      }
    </style>
  </head>
  <body></body>
</html>
```

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616398923297)

### background-repeat 属性

`background-repeat` 属性是用来设置背景图像是否平铺。

下表列出了 `background-repeat` 属性的一些可取值以及每个可取值的含义。

| 可 取 值  | 描 述                                        |
| --------- | -------------------------------------------- |
| repeat    | 背景图像将在垂直方向和水平方向重复（默认值） |
| repeat-x  | 背景图像将在水平方向重复                     |
| repeat-y  | 背景图像将在垂直方向重复                     |
| no-repeat | 背景图像将仅显示一次                         |

> 我们规定应该从父元素继承 `background-repeat` 属性的设置。

我们在 `index10.html` 中加入 `background-repeat` 属性并设置值为不平铺。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        background-image: url("moon.jpg");
        background-size: 300px 300px;
        background-repeat: no-repeat;
      }
    </style>
  </head>
  <body></body>
</html>
```

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616399238124)

## 文本属性

文本属性用于定义文本的样式，通过文本属性，可以改变文本的颜色、字间距、对齐方式、文本修饰和文本缩进等。常用文本属性如下表所示：

| 属 性           | 可 取 值                                              | 描 述                              |
| --------------- | ----------------------------------------------------- | ---------------------------------- |
| line-height     | normal、number、length、%                             | 设置行高                           |
| text-indent     | length、%                                             | 设置文本缩进                       |
| text-align      | left、right、center、justify、start、end              | 设置对齐方式                       |
| letter-spacing  | normal、length                                        | 设置字符间距                       |
| text-decoration | line、color、style、thickness                         | 设置文本修饰                       |
| white-space     | normal、pre、nowrap、pre-wrap、pre-line、break-spaces | 规定如何处理空白                   |
| line-break      | auto、loose、normal、strict、anywhere、unset          | 处理如何断开带有标点符号的文本的行 |

这里只给大家介绍两个最常用的文本属性 `line-height` 和 `text-decoration`。

### line-height 的使用

`line-height` 用于设置多行元素的空间量，可取值具体说明如下：

- `normal`：取决于用户端。
- `number`：数字乘以元素的字体大小。
- `length`：指定长度用于计算高度。
- `%`：计算值是给定的百分比值乘以元素计算出的字体大小。

新建一个 `index11.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>line-height 的使用</title>
    <style>
      div {
        width: 300px;
        height: 400px;
        border: 1px solid;
        font-size: 15px;
        display: inline-block;
        vertical-align: top;
      }
      .div1 {
        line-height: 2; /*15 * 2*/
      }
      .div2 {
        line-height: 30%; /*15 * 30% */
      }
    </style>
  </head>
  <body>
    <div class="div1">
      <p>“海水呀，你说的是什么？”</p>
      <p>“是永恒的疑问。”</p>
      <p>“天空呀，你回答的话是什么？”</p>
      <p>“是永恒的沉默。”</p>
    </div>
    <div class="div2">
      <p>“海水呀，你说的是什么？”</p>
      <p>“是永恒的疑问。”</p>
      <p>“天空呀，你回答的话是什么？”</p>
      <p>“是永恒的沉默。”</p>
    </div>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/8f8d05703454428c06e831fdd20ad06a-0)

### text-decoration 的使用

`text-decoration` 属性用于设置文本的装饰线，例如给文本加下划线、中划线、波浪线等。可取值具体说明如下：

- `text-decoration-line` 设置线的位置，可取值包含：`underline`（下划线）、`overline`（上划线）、`line-through`（中划线）。
- `text-decoration-color` 设置线的颜色。
- `text-decoration-style` 设置线的样式，可取值包含：`wavy`（波浪线）、`solid`（实线）、`dashed`（虚线）。
- `text-decoration-thickness` 设置线的粗细。

新建一个 `index12.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>text-decoration 的使用</title>
    <style>
      .item1 {
        text-decoration: underline lime; /*下划线直线*/
      }
      .item2 {
        text-decoration: wavy overline lime; /*上划线波浪线*/
      }
      .item3 {
        text-decoration: line-through lime; /*中划线*/
      }
      .item4 {
        text-decoration: none; /*无样式*/
      }
      .item5 {
        text-decoration: dashed underline overline lime 5px; /*圆点上划线和下划线*/
      }
    </style>
  </head>
  <body>
    <p class="item1">太阳只穿一件朴素的光衣，白云却披了灿烂的裙裾。</p>
    <p class="item2">太阳只穿一件朴素的光衣，白云却披了灿烂的裙裾。</p>
    <p class="item3">太阳只穿一件朴素的光衣，白云却披了灿烂的裙裾。</p>
    <p class="item4">太阳只穿一件朴素的光衣，白云却披了灿烂的裙裾。</p>
    <p class="item5">太阳只穿一件朴素的光衣，白云却披了灿烂的裙裾。</p>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/1b5ce262a33ed291cd1217acfe4b2241-0)

## 字体属性

字体属性用于定义字体的类型、字号大小、加粗、斜体等方面样式。常用的字体属性如下表所示：

| 属 性       | 可 取 值                                                     | 描 述                          |
| ----------- | ------------------------------------------------------------ | ------------------------------ |
| font        | font-style、font-variant、font-weight、font-size（或 line-height）、font-family | 在一个声明中设置所有的字体属性 |
| font-family | 字体名称、inherit                                            | 设置字体类型                   |
| font-size   | xx-small、x-small、small、medium（默认）、large、x-large、xx-large smaller、larger length、%、inherit | 设置字体大小                   |
| font-weight | normal（默认）、bold、bolder、lighter、inherit 100、200…900（400=normal，700=bold） | 设置字体粗细                   |
| font-style  | normal、italic、oblique、inherit                             | 设置字体风格                   |

我们来举个例子吧！😉

新建一个 `index13.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      h3 {
        font-size: 20px;
        font-family: 隶书;
        line-height: 28px;
      }
      span {
        font: italic 16px 华文彩云;
      }
    </style>
  </head>
  <body>
    <h3>Web 前端技术</h3>
    <span
      >在当今社会中，Web 已经成为网络信息共享和发布的主要形式。要想开发 Web 应用
      系统，就必须掌握 Web 前端技术。</span
    >
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616404889968)

## 链接中的伪类

何为伪类呢？🤔

在 CSS 中，伪类是添加到选择器的关键字，给指定元素设置一些特殊状态，我们以 `:` 开头。

链接有以下四个状态。这四种状态也称之为超链接的伪类。

| 状态      | 效果                     |
| --------- | ------------------------ |
| a:link    | 普通的、未被访问的链接。 |
| a:hover   | 鼠标指针位于链接的上方。 |
| a:active  | 链接被单击的时刻。       |
| a:visited | 用户已访问的链接。       |

针对超链接的上述四种状态设置样式规则，能起到美化超链接的作用。例如，为了完成下对超链接的显示要求，编写的 CSS 样式代码如下。

| 状 态    | 颜 色 | 背 景 色 | 文 本 修 饰 |
| -------- | ----- | -------- | ----------- |
| 未访问   | 蓝色  | 无       | 无下画线    |
| 鼠标移到 | 黑色  | \#DDDDDD  | 下画线      |
| 正单击   | 红色  | \#AAAAAA  | 删除线      |
| 已访问   | 绿色  | 无       | 无下画线    |

> 对于超链接的伪类，我们推荐的使用顺序是：:link - :visited - :hover - :active。

我们来举个例子吧！😉

新建一个 `index14.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      * {
        text-decoration: none;
      }
      a:link {
        color: red;
      }
      a:visited {
        color: blue;
      }
      a:hover {
        color: green;
      }
      a:active {
        color: yellow;
      }
    </style>
  </head>
  <body>
    <a href="#">这是一个链接</a>
  </body>
</html>
```

开启 8080 端口，打开 Web 服务，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210322-1616408144043)

同学们可能很疑惑，我们为什么要按照这样的顺序来使用呢？🤔 我们调整一下这几个伪类的顺序，看看会发生什么。

我们把 `a:link` 放到最后，效果如下。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210508-1620456798596)

从图中我们可以发现其中的样式属性都被覆盖了。

我们把 `a:hover` 放到 `a:active` 之后，效果如下。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210508-1620457297251)

从图中我们可以发现 `a:active` 的属性样式被覆盖了。

通过上面的例子我们可以知道链接伪类的使用顺序是很重要的。

## 列表样式

| 属 性               | 可 取 值                                               | 描 述                          |
| ------------------- | ------------------------------------------------------ | ------------------------------ |
| list-style          | list-style-type、list-style-position、list-style-image | 在一个声明中设置所有的列表属性 |
| list-style-image    | URL、none                                              | 设置图像为列表项标志           |
| list-style-position | inside、outside、inherit                               | 设置列表中列表项标志的位置     |
| list-style-type     | disc（默认）、circle、square、decimal 等               | 设置列表项标志的类型           |

我们来举个例子吧！😉

使用以下命令获取需要的 gif 动图。

```bash
wget https://labfile.oss.aliyuncs.com/courses/2841/list.gif
```

新建一个 `index15.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      ul {
        list-style-position: inside;
        list-style-image: url(list.gif);
      }
    </style>
  </head>
  <body>
    <ul>
      <li>喵</li>
    </ul>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210323-1616465405412)

## 实验总结

本节实验给大家介绍了 CSS 在前端中充当的角色，然后给大家介绍了 CSS 的基础语法。

- 背景样式
- 文本属性
- 字体属性
- 链接中的伪类
- 列表样式