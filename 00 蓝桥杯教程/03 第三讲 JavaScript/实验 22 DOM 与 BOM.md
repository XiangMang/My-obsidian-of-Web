## 实验介绍

Hi！欢迎来到本章节～

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验给大家介绍 JavaScript 中两块重要的知识点 DOM 和 BOM。

下面我们一起来学习吧～

#### 知识点

- DOM
- BOM

## DOM 的使用

那么什么是 DOM 呢？🤔

DOM 的英文全称为 Document Object Model（文档对象模型），它是浏览器为每个窗口内的 HTML 页面创建的一个 document 对象来对页面的元素进行操作。

还记得从开始学 JavaScript 时，我们就用 `document.write()` 在页面上输出值，在本节实验中，我们会学到 DOM 的更多属性。

## DOM 属性

常用的 DOM 属性如下表所示：

| 属性              | 描 述                          |
| ----------------- | ------------------------------ |
| document.title    | 获取文档的 title 元素。        |
| document.body     | 获取文档的 body 元素。         |
| document.URL      | 获取文档的 URL。               |
| document.forms    | 获取文档的 form 元素。         |
| document.images   | 获取文档的 img 元素。          |
| document.links    | 获取文档的 a 元素。            |
| document.cookie   | 获取文档的 cookie。            |
| document.referrer | 返回来用户当前浏览页面的 URL。 |

这里我们来举个例子吧！👻

新建一个 `index.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 属性</title>
  </head>
  <body>
    <a href="https://www.lanqiao.cn/">蓝桥云课</a><br />
    <img
      src="https://labfile.oss.aliyuncs.com/courses/3773/lanqiao.png"
    /><br />
    <script>
      var num = document.links;
      document.write("页面上有 " + num.length + " 个链接。" + "<br>");
      var get_url = document.URL;
      document.write("该页面的链接为 " + get_url + "<br>");
      var get_img = document.images;
      document.write("页面上有 " + get_img.length + " 张图片。" + "<br>");
      var get_title = document.title;
      document.write("该页面标题为 " + get_title + "。");
    </script>
  </body>
</html>
```

启动 8080 端口，打开 Web 服务，可以看到如下结果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210329-1617010137572)

## DOM 方法

常用的 DOM 方法如下表所示：

| 方法                             | 描 述                      |
| -------------------------------- | -------------------------- |
| document.getElementById()        | 通过 id 获取元素。         |
| document.getElementByTagName()   | 通过标签名获取元素。       |
| document.getElementByClassName() | 通过 class 获取元素。      |
| document.getElementByName()      | 通过 name 获取元素。       |
| document.querySelector()         | 通过选择器获取第一个元素。 |
| document.querySelectorAll()      | 通过选择器获取所有元素。   |
| document.createElement()         | 创建元素节点。             |
| document.createTextNode()        | 创建文本节点。             |
| document.write()                 | 输出内容。                 |
| document.writeln()               | 输出内容并换行。           |

这里我们来举个例子吧！👻

新建一个 `index1.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <p id="demo">蓝桥云课</p>
    <button onclick="changeColor()">改变颜色</button>
    <button onclick="createElem()">创建元素</button>
    <div class="item"></div>
    <button onclick="addText()">添加内容</button>
    <script>
      // 改变元素的颜色
      function changeColor() {
        document.getElementById("demo").style.color = "blue"; // 通过 id 改变指定元素的样式
      }
      // 创建一个指定名字的按钮
      function createElem() {
        var btn = document.createElement("BUTTON"); // 创建元素节点
        var t = document.createTextNode("确认"); // 创建文本节点
        btn.appendChild(t);
        document.body.appendChild(btn); // 在 body 中添加一个元素。
      }
      // 在指定标签中添加内容
      function addText() {
        var e = document.getElementsByClassName("item");
        e[0].innerHTML = "蓝桥云课是国内领先的 IT 在线编程及在线实训学习平台。";
      }
    </script>
  </body>
</html>
```

启动 8080 端口，打开 Web 服务，可以看到如下结果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210330-1617071645314)

- 在上面代码中，定义了一个名为 `changeColor` 的函数，在函数内部使用 `document.getElementById("demo").style.color` 改变 id 名为 demo 的元素的字体颜色。
- 定义了一个名为 `createElem` 的函数，在函数内部使用 `document.createElement` 创建了一个元素节点，使用 `document.createTextNode` 创建了一个文本节点，最后通过 `appendChild` 把创建的元素显示到页面上。

我们做个小挑战吧～

挑战要求：

页面上有一个宽和高均为 `50 px` 的元素块，当我们点击旁边的按钮，会冒出一个相同的元素块。

挑战效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4385/1347963/67de75c340399d59c904113e08e232c1-0)

<details open="" style="box-sizing: border-box; display: block; margin-bottom: 16px; margin-top: 0px;"><summary style="box-sizing: border-box; touch-action: manipulation; display: list-item; cursor: pointer; outline: none;">参考答案</summary><pre style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14px; margin-bottom: 1rem; margin-top: 0px; overflow: visible; color: rgb(33, 37, 41); display: block; position: relative; word-break: break-all; border-radius: 4px; white-space: pre-wrap;"><code class="language-html hljs xml" style="box-sizing: border-box; font-family: &quot;Source Code Pro&quot;, Consolas, monospace; font-size: inherit; overflow-wrap: break-word; color: rgb(248, 248, 242); word-break: normal; background: rgb(35, 36, 31); display: block; overflow-x: auto; padding: 0.5em;"><span class="hljs-meta" style="box-sizing: border-box; color: rgb(117, 113, 94);">&lt;!DOCTYPE <span class="hljs-meta-keyword" style="box-sizing: border-box;">html</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">html</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(249, 38, 114);">lang</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"en"</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">head</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(249, 38, 114);">charset</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"UTF-8"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(249, 38, 114);">name</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"viewport"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(249, 38, 114);">content</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"width=device-width, initial-scale=1.0"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">title</span>&gt;</span>Document<span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">title</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">style</span>&gt;</span><span class="css" style="box-sizing: border-box;">
      <span class="hljs-selector-tag" style="box-sizing: border-box; color: rgb(249, 38, 114);">div</span> {
        <span class="hljs-attribute" style="box-sizing: border-box; color: rgb(102, 217, 239);">display</span>: inline-block;
        <span class="hljs-attribute" style="box-sizing: border-box; color: rgb(102, 217, 239);">width</span>: <span class="hljs-number" style="box-sizing: border-box; color: rgb(174, 129, 255);">50px</span>;
        <span class="hljs-attribute" style="box-sizing: border-box; color: rgb(102, 217, 239);">height</span>: <span class="hljs-number" style="box-sizing: border-box; color: rgb(174, 129, 255);">50px</span>;
        <span class="hljs-attribute" style="box-sizing: border-box; color: rgb(102, 217, 239);">margin</span>: <span class="hljs-number" style="box-sizing: border-box; color: rgb(174, 129, 255);">10px</span>;
        <span class="hljs-attribute" style="box-sizing: border-box; color: rgb(102, 217, 239);">background</span>: greenyellow;
      }
    </span><span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">style</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">head</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">body</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">div</span>&gt;</span><span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">div</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">button</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(249, 38, 114);">onclick</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"myFunc()"</span>&gt;</span>创建元素<span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">button</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">script</span>&gt;</span><span class="javascript" style="box-sizing: border-box;">
      <span class="hljs-function" style="box-sizing: border-box;"><span class="hljs-keyword" style="box-sizing: border-box; color: rgb(249, 38, 114);">function</span> <span class="hljs-title" style="box-sizing: border-box; color: rgb(166, 226, 46);">myFunc</span>(<span class="hljs-params" style="box-sizing: border-box; color: rgb(248, 248, 242);"></span>) </span>{
        <span class="hljs-keyword" style="box-sizing: border-box; color: rgb(249, 38, 114);">var</span> e = <span class="hljs-built_in" style="box-sizing: border-box; color: rgb(230, 219, 116);">document</span>.createElement(<span class="hljs-string" style="box-sizing: border-box; color: rgb(230, 219, 116);">"div"</span>);
        <span class="hljs-built_in" style="box-sizing: border-box; color: rgb(230, 219, 116);">document</span>.body.appendChild(e);
      }
    </span><span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">script</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">body</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(248, 248, 242);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(249, 38, 114);">html</span>&gt;</span>
</code><div class="btn-copy" style="box-sizing: border-box; align-items: center; cursor: pointer; display: flex; flex-direction: column; opacity: 0; position: absolute; right: 8px; top: 8px; transition: opacity 0.3s linear 0s; white-space: normal; width: 18px; word-break: normal;"><img class="icon-copy" title="copy" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAYAAACtWK6eAAALCElEQVR4Xu2dXchlZRXH/+uiyDAV7SIm+pg+MBvxow9IpNTArFCbQrS6iKhJ+zCwspu8UKOb6MML+8BREypTCCslI6xw1IiCbMopSTCxEiSKagy8qIsVD52hSXrfs85+zrP3c/b6bTjMxbvW86z1X//fu8857569TRwogAJbKmBogwIosLUCAII7UGAbBQAEe6AAgOABFBimAGeQYbqRlUQBAEkyaNocpgCADNONrCQKAEiSQdPmMAUAZJhuZCVRAECSDJo2hykAIMN0IyuJAgCSZNC0OUwBABmmG1lJFOgGEHc/RdJuScce9joiyRx6bfMOSfea2f29Fti6rkkBcfcTJF0s6WxJu1o3y/qDFfi4mX12cPYGJ04CiLs/Q9LHJF0u6ZgN1i9T6a81sx9narj0Ojog7n6upE9KOjWb2Bve78/M7DUb3sPK5Y8KiLt/SNIXVq6ShF4U2Glmj/ZSzBh1jAaIu39A0pfGaIo9mikAIC2kdffXSbqnxdqsOZoCB8zspNF262Sj5mcQdz9R0p2Snt9Jz5QxTIGrzeyqYambmzUGINctvsrdXJWo/JtmdmFGGZoC4u6vlPTzgcI+IukPA3NJW48CZQY/MrNvrGe5zVulNSCrnj3uk3STpPvM7OHNk5OK56ZAM0DcvVwm8tjispGIbinf40aEIWY6BVoC8jZJtwVb22FmjwdjCUOB0RRoCcj1kvYEOuHMERCJkGkUaAnIAUnlK97tjiclvYSzxzTDZ9flCrQE5J+SnrakhP1m9orlZRKBAtMo0AQQd3+RpN8FWrrFzN4ZiCMEBSZRoBUgZ0q6O9ARnz8CIhEynQIAMp327LwBCgDIBgyJEqdTAECm056dN0ABANmAIVHidAoAyHTas/MGKAAgGzAkSpxOAQCZTnt23gAFUgLi7i+XVP6vyvGSXibpuA2Y1ZxLLJccPXToZWb7emk2DSDu/kZJZ0g6j5vU9WK/Lev48+JK8HvM7NYpq509IO5+uqQPS7poSqHZe7AC5bane81s7+AVKhJnDYi7f17SRyr0IbUfBQool4/99mu2gLj7TySd1s98qWQNCvxL0hvGhGSWgLi7r2EYLNGvArvM7MExypsdIO5+syQuoR/DPdPuMQokswLE3T8l6Ypp58buIynwG0kXtj6TzAYQd399uYfTSMNhmz4UKN9uXdKylDkBUm5v+uaWYrF2lwq8quUTsGYBiLu/V9INK4zvL5I+LekBSb8ysz+tkEvomhVw9yMllRtjl1d54tgqz45pehaZCyB3LR7jFhlduXvjbjP7aySYmPEVcPdV5nlQ0gvMrPy79mPjAXH3561wD9/bzOyCtavIgmtXwN2vkXRZcOF3mdnXgrErhc0BkEslXRvsmjs4BoXqIczd90sqTz9edjT7xTcHQD4n6aPLFJTEHVQCIvUU4u7nS7o9UNMvzKxcnb32Yw6AlLvBvzugzDlmVt7bcmyIAu7+dEnlyt6jlpT8qJntbNHWHAApD7svl7BvdzxhZke3EJA12yrg7t+XdM5U850DIOUGdeVGddsd+8zsrLajZPUWCrh7eezblcvWNrMmXm6yqLuPdmdFdweQZe7Z4J8DSOWDIQFkg90fKB1AACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whcwXkKEkHA2M9z8y+G4jbMsTd75Z05pI19pnZWTX7kDuNArMEpEjp7rdLOn+JrDvM7PEa6QGkRr3+c+cMSPmtXn67b3XsNbNLakcEILUK9p0/W0AWZ5H3S/qMpCOfMoarrfKzx6H1AKRvg9dWN2tAFpCcLOlUSS+U9EdJvzezH9YKByDrUrDvdWYPSGv5OYO0Vnja9QGkUn8AqRSw83QAqRwQgFQK2Hk6gFQOCEAqBew8HUAqBwQglQJ2ng4glQMCkEoBO08HkMoBAUilgJ2nA0jlgACkUsDO0wGkckAAUilg5+kAUjkgAKkUsPN0AKkcEIBUCth5OoBUDghAKgXsPB1AKgcEIJUCdp4OIJUDApBKATtPB5DKAQFIpYCdpwNI5YAApFLAztMBpHJAAFIpYOfpAFI5IACpFLDzdACpHBCAVArYeTqAVA4IQCoF7DwdQCoH5O53STp7yTKPmNmLK7cifQIF3P0aSZct2fqgmR3TojxrseiYa7r7LZLeHtjzpWb2cCCOkI4UcPf9kk5ZUtIBMzupRdlzAORaSZcGxHmPmd0UiCOkEwXc/XhJvw2Uc6eZnRuIWzlkDoBcJenKQOc/NbPTAnGEdKKAu18n6eJAOWu5S+f/22cOgJTTbzkNR44bzOx9kUBiplXA3d8k6XvBKtZ2p86n7rfxgJSG3P3XknYFxXyHmd0ajCVsAgXc/URJB4JbPynp5FafL+cCSOSbjsP1/qqkvZIeMLN/BAdBWGMF3L3covYCSZ9YYavrzSzyNmyFJf8bOhdAyle490raMUCFhyRVPYJhwJ6k/K8Cz5J0gqRnDhDmDDMrs29yzAKQxdusD0r6YhOVWLRXBb5jZm9tWdxsAFlA8m1Ju1sKxtrdKPB3Saeb2YMtK5obIM9efLh7TkvRWLsLBfaY2Y2tK5kVIIuzSHkeyS9bC8f6kypwo5ntGaOC2QGygKR8aL9f0tFjiMgeoyrwZTMrnzdHOWYJyAKSYyV9RdJbRlGSTVor8DdJF5nZD1pvdPj6swXkUJPufoWk8jpiTGHZa60KfKtc0Wtm5RF+ox6zB2RxNnn1AhLOJqPaq2qz8hfymyV9veXfOZZVmAKQw84mz5VUrvEpr52Syrdexw38A9Uybfl5XIEnFg94fUzSoVcBY/L/npAKkPi8iESB/ygAIDgBBbZRAECwBwoACB5AgWEKcAYZphtZSRQAkCSDps1hCgDIMN3ISqIAgCQZNG0OUwBAhulGVhIFACTJoGlzmAIAMkw3spIoACBJBk2bwxQAkGG6kZVEAQBJMmjaHKbAvwGyE7Iy90AbtwAAAABJRU5ErkJggg==" style="box-sizing: initial; border-style: none; vertical-align: middle; max-width: 100%; background: rgb(35, 35, 30); border-radius: 4px;"></div></pre></details>

## BOM 的使用

BOM（Browser Object Mode）是浏览器对象模型，通过操作对象的属性和方法来实现与浏览器的交互。

BOM 的构成如下所示：

![图片描述](https://doc.shiyanlou.com/courses/4385/1347963/934aa25def575c514b29c151a0cab411-0)

从图中可以看出，window 是顶级对象，它也是我们学习的核心。

在 window 下面有：

- document 是 DOM 对象。
- location 是用于获取或设置窗体。
- navigation 包含浏览器配置相关的信息。
- history 浏览器的历史记录。
- screen 用于显示设备信息。

window 对象的方法如下所示：

| 方法      | 描 述                              |
| --------- | ---------------------------------- |
| alert()   | 显示一个警告框。                   |
| prompt()  | 显示可提示用户输入的对话框。       |
| confirm() | 显示一个有确认和取消按钮的对话框。 |
| open()    | 打开一个新的浏览器窗口。           |
| close()   | 关闭浏览器。                       |
| print()   | 打印当前窗口内容。                 |

若想了解更多关于 BOM 的知识，请阅读 [JavaScript Window - The Browser Object Model](https://www.w3schools.com/js/js_window.asp)。

这里我们来举个例子吧！👻

新建一个 `index2.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script>
      // 警告框
      function myFunction1() {
        alert("你好!");
      }
      // 输入对话框
      function myFunction2() {
        var info;
        var name = prompt("请输入你的名字", "");
        info = "欢迎" + name + "的到来！";
        document.getElementById("demo").innerHTML = info;
      }
    </script>
  </head>
  <body>
    <div id="demo"></div>
    <input type="button" onclick="myFunction2()" value="欢迎" />
    <input type="button" onclick="myFunction1()" value="点我" />
  </body>
</html>
```

启动 8080 端口，打开 Web 服务，可以看到如下结果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210330-1617074955073)

## 实验总结

本节实验给大家介绍了文档对象模型（document）中常用的属性和方法，以及浏览器对象模型（window）的属性和方法。