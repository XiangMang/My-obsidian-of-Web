## 实验介绍

Hi，欢迎来到本章节！

![亲亲](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

HTML5 技术结合了 HTML4.01 的相关标准并革新，符合现代网络发展要求，在 2008 年正式发布。与传统的技术相比，HTML5 的语法特征更加明显，可以更加便捷地处理多媒体内容，而且 HTML5 中还结合了其他元素，对原有的功能进行调整和修改，进行标准化工作。HTML5 在 2012 年已形成了稳定的版本。

HTML 语言从 1.0 到 5.0 经历了巨大的变化，从单一的文本显示功能到图文并茂的多媒体显示功能，许多特性经过多年的完善，已经发展成为一种非常重要的标记语言。 HTML5 新增的特性如下。

- 新的语义标签，比如 header、nav、section、article、footer。
- 新的表单元素，比如 calendar、date、time、email、url、search。
- 用于绘画的 canvas 元素。
- 用于媒介回放的 video 和 audio 元素。
- 对本地离线存储的更好支持。
- 地理位置、拖曳、摄像头等 API。

本节实验中，将会给大家介绍 HTML5 中常用的新特性。

#### 知识点

- 基本语义化标签
- 多媒体标签
- HTML5 新属性

## 基本语义化标签

语义化标签就是把 HTML 文档中的元素划分到不同区域，每个区域有自己的含义。

我们可以把语义化标签想成一个房子里的不同区域，一套房子，有客厅、饭厅、卧室、厕所等，它们都属于房子里的一部分空间，不同的划分区域有不同的用处，比如，饭厅是用来吃饭的，我们通常不会在厕所里吃饭。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/39b7118c74c01f99ece9e5f4bece86b6-0)

在 HTML5 中，提供了如下图所示的语义化标签，让我们可以更直观地看到页面的结构。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/d4ded8d905de1f86c7fb75e71b707503-0)

标签说明：

- `header` 标签是头部区域。
- `nav` 标签是导航区域。
- `article` 标签是内容区域。
- `section` 标签是文档中部分内容区域。
- `aside` 标签是侧边内容栏区域。
- `footer` 标签是底部信息区域。

例如，[环球科学](https://huanqiukexue.com/)的首页，我们可以用语义化标签来划分一下结构。

![图片描述](https://doc.shiyanlou.com/courses/4384/1347963/1c8f58e60f0433a89b4282fcd1a314e7-0)

> 由于这些标签本身只有一个块级元素的特点，如果不加入 CSS 样式，是没有任何效果的，这里我们不做练习，等学完 CSS 我们再进行练习。

## 多媒体标签

多媒体标签就是用于在页面中嵌入音频和视频的标签，主要有以下两个标签：

- audio 标签
- video 标签

下面我们一一为大家介绍

### audio 标签

在 HTML5 中，使用 `audio` 标签来播放声音文件或者音频流，该标签支持 Ogg、MP3、WAV 等音频格式。

其使用格式如下：

```html
<audio src="URL" controls></audio>
```

参数说明：

- `src` 属性用于指定要播放的声音文件。
- `controls` 是 `controls="controls"` 简写形式，用于提供播放、暂停和音量控件。

除了上面两种属性，`audio` 标签还有以下属性可用：

- `autoplay` 属性：音频自动播放。
- `loop` 属性：音频自动重复播放。
- `preload` 属性：用来缓冲 `audio` 标签的大文件，它有三个属性值 none（不缓冲）、auto（缓冲音频文件）、metadata （缓冲文件的元数据）。

#### source 标签

`audio` 标签还可以通过子标签 `source` 来进行多数据源的设置。

其使用格式如下：

```html
<audio>
  <source src="URL" />
</audio>
```

一个 `audio` 标签可以包含多个 `source` 标签，当播放器无法识别当前格式的播放源时会调用下一个 `source` 播放源进行播放。

`source` 标签是用来指定多个文件，给不同的浏览器提供可支持的编码格式。

例如：

```html
<audio>
  <source src="filename.opus" />
  <source src="filename.ogg" />
  <source src="filename.mp3" />
</audio>
```

认识了 `audio` 和 `source` 标签，接下来我们做一做练习吧！👇

在终端输入以下命令来获取一个 `.mp3` 的文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/2841/snow.mp3
```

新建一个 `index.html` 文件，在其中写入以下代码：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <audio controls>
      <source src="snow.mp3" />
    </audio>
  </body>
</html>
```

启动 8080 端口，打开 Web 服务，快来播放音乐，放松一下吧！👻

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615959665704)

从上面内容可以看到页面出现了一个简单的播放器，包括播放控制、时间显示、进度条显示和音量调节等控件。

### video 标签

在有些网站的页面上会放上一些视频，我们点击视频就会播放，那么这是怎么实现的呢？🤔

在 HTML 中，提供了 `video` 标签向文档中嵌入媒体播放器。

语法格式如下所示：

```html
<video controls>
  <source src="URL" />
</video>
```

我们举个例子来看看。😉

在终端输入以下命令来获取一个 `.mp4` 的文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3582/video.mp4
```

新建一个 `index1.html` 文件，在其中写入以下代码：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <video muted controls>
      <source src="video.mp4" />
    </video>
  </body>
</html>
```

启动 8080 端口，打开 Web 服务，让我们一起看个动画片吧 😎 ～

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/443353f2853350ee48e6a33f377cbf55-0)

同学们有没有注意到打开页面视频默认是静音状态？这是因为我加入了 `muted` 属性，如果你去掉该属性视频默认是有声播放。

#### 给视频加上封面

有时候我们不想让别人一眼看出播放的视频内容，为了保持神秘，吊人胃口，我们可以给视频加上一个封面。

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/3a59b7aae4112a3ab3c4dd277725e51e-0)

我们在 `video` 标签中加入 `poster` 属性即可给视频添加封面。

使用格式如下：

```html
<video poster="URL"></video>
```

属性值 URL 是封面图的地址。

下面我们做个练习吧！

大家可以选择自己的封面图和视频放到页面中，也可以使用下方为大家提供的视频和封面图。新建 `index2.html` 完成此练习。

封面图下载：

```bash
wget https://labfile.oss.aliyuncs.com/courses/4421/elena.png
```

视频下载：

```bash
wget https://labfile.oss.aliyuncs.com/courses/3582/video.mp4
```

实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/9f3a9082fa72adfa8ff06b79bcc39393-0)

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; touch-action: manipulation; display: list-item; cursor: pointer; outline: none;">参考答案</summary><pre style="box-sizing: border-box; font-size: 14px; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; margin-top: 0px; margin-bottom: 1rem; overflow: visible; display: block; color: rgb(157, 154, 149); position: relative; word-break: break-all; border-radius: 4px; white-space: pre-wrap;"><code class="language-html hljs xml" style="box-sizing: border-box; font-size: inherit; font-family: &quot;Source Code Pro&quot;, Consolas, monospace; color: rgb(174, 174, 160); overflow-wrap: break-word; word-break: normal; display: block; overflow-x: auto; padding: 0.5em; background: rgb(19, 20, 21);"><span class="hljs-meta" style="box-sizing: border-box; color: rgb(124, 119, 110);">&lt;!DOCTYPE <span class="hljs-meta-keyword" style="box-sizing: border-box;">html</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">html</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">lang</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"en"</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">head</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">charset</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"UTF-8"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">name</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"viewport"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">content</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"width=device-width, initial-scale=1.0"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">title</span>&gt;</span>Document<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">title</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">head</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">body</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">video</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">poster</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"elena.png"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">controls</span>&gt;</span>
      <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">source</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">src</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"video.mp4"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">video</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">body</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">html</span>&gt;</span>
</code><div class="btn-copy" style="box-sizing: border-box; position: absolute; display: flex; flex-direction: column; align-items: center; width: 18px; right: 8px; top: 8px; cursor: pointer; opacity: 0; transition: opacity 0.3s linear 0s; word-break: normal; white-space: normal;"><img class="icon-copy" title="copy" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAYAAACtWK6eAAALCElEQVR4Xu2dXchlZRXH/+uiyDAV7SIm+pg+MBvxow9IpNTArFCbQrS6iKhJ+zCwspu8UKOb6MML+8BREypTCCslI6xw1IiCbMopSTCxEiSKagy8qIsVD52hSXrfs85+zrP3c/b6bTjMxbvW86z1X//fu8857569TRwogAJbKmBogwIosLUCAII7UGAbBQAEe6AAgOABFBimAGeQYbqRlUQBAEkyaNocpgCADNONrCQKAEiSQdPmMAUAZJhuZCVRAECSDJo2hykAIMN0IyuJAgCSZNC0OUwBABmmG1lJFOgGEHc/RdJuScce9joiyRx6bfMOSfea2f29Fti6rkkBcfcTJF0s6WxJu1o3y/qDFfi4mX12cPYGJ04CiLs/Q9LHJF0u6ZgN1i9T6a81sx9narj0Ojog7n6upE9KOjWb2Bve78/M7DUb3sPK5Y8KiLt/SNIXVq6ShF4U2Glmj/ZSzBh1jAaIu39A0pfGaIo9mikAIC2kdffXSbqnxdqsOZoCB8zspNF262Sj5mcQdz9R0p2Snt9Jz5QxTIGrzeyqYambmzUGINctvsrdXJWo/JtmdmFGGZoC4u6vlPTzgcI+IukPA3NJW48CZQY/MrNvrGe5zVulNSCrnj3uk3STpPvM7OHNk5OK56ZAM0DcvVwm8tjispGIbinf40aEIWY6BVoC8jZJtwVb22FmjwdjCUOB0RRoCcj1kvYEOuHMERCJkGkUaAnIAUnlK97tjiclvYSzxzTDZ9flCrQE5J+SnrakhP1m9orlZRKBAtMo0AQQd3+RpN8FWrrFzN4ZiCMEBSZRoBUgZ0q6O9ARnz8CIhEynQIAMp327LwBCgDIBgyJEqdTAECm056dN0ABANmAIVHidAoAyHTas/MGKAAgGzAkSpxOAQCZTnt23gAFUgLi7i+XVP6vyvGSXibpuA2Y1ZxLLJccPXToZWb7emk2DSDu/kZJZ0g6j5vU9WK/Lev48+JK8HvM7NYpq509IO5+uqQPS7poSqHZe7AC5bane81s7+AVKhJnDYi7f17SRyr0IbUfBQool4/99mu2gLj7TySd1s98qWQNCvxL0hvGhGSWgLi7r2EYLNGvArvM7MExypsdIO5+syQuoR/DPdPuMQokswLE3T8l6Ypp58buIynwG0kXtj6TzAYQd399uYfTSMNhmz4UKN9uXdKylDkBUm5v+uaWYrF2lwq8quUTsGYBiLu/V9INK4zvL5I+LekBSb8ysz+tkEvomhVw9yMllRtjl1d54tgqz45pehaZCyB3LR7jFhlduXvjbjP7aySYmPEVcPdV5nlQ0gvMrPy79mPjAXH3561wD9/bzOyCtavIgmtXwN2vkXRZcOF3mdnXgrErhc0BkEslXRvsmjs4BoXqIczd90sqTz9edjT7xTcHQD4n6aPLFJTEHVQCIvUU4u7nS7o9UNMvzKxcnb32Yw6AlLvBvzugzDlmVt7bcmyIAu7+dEnlyt6jlpT8qJntbNHWHAApD7svl7BvdzxhZke3EJA12yrg7t+XdM5U850DIOUGdeVGddsd+8zsrLajZPUWCrh7eezblcvWNrMmXm6yqLuPdmdFdweQZe7Z4J8DSOWDIQFkg90fKB1AACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whcwXkKEkHA2M9z8y+G4jbMsTd75Z05pI19pnZWTX7kDuNArMEpEjp7rdLOn+JrDvM7PEa6QGkRr3+c+cMSPmtXn67b3XsNbNLakcEILUK9p0/W0AWZ5H3S/qMpCOfMoarrfKzx6H1AKRvg9dWN2tAFpCcLOlUSS+U9EdJvzezH9YKByDrUrDvdWYPSGv5OYO0Vnja9QGkUn8AqRSw83QAqRwQgFQK2Hk6gFQOCEAqBew8HUAqBwQglQJ2ng4glQMCkEoBO08HkMoBAUilgJ2nA0jlgACkUsDO0wGkckAAUilg5+kAUjkgAKkUsPN0AKkcEIBUCth5OoBUDghAKgXsPB1AKgcEIJUCdp4OIJUDApBKATtPB5DKAQFIpYCdpwNI5YAApFLAztMBpHJAAFIpYOfpAFI5IACpFLDzdACpHBCAVArYeTqAVA4IQCoF7DwdQCoH5O53STp7yTKPmNmLK7cifQIF3P0aSZct2fqgmR3TojxrseiYa7r7LZLeHtjzpWb2cCCOkI4UcPf9kk5ZUtIBMzupRdlzAORaSZcGxHmPmd0UiCOkEwXc/XhJvw2Uc6eZnRuIWzlkDoBcJenKQOc/NbPTAnGEdKKAu18n6eJAOWu5S+f/22cOgJTTbzkNR44bzOx9kUBiplXA3d8k6XvBKtZ2p86n7rfxgJSG3P3XknYFxXyHmd0ajCVsAgXc/URJB4JbPynp5FafL+cCSOSbjsP1/qqkvZIeMLN/BAdBWGMF3L3covYCSZ9YYavrzSzyNmyFJf8bOhdAyle490raMUCFhyRVPYJhwJ6k/K8Cz5J0gqRnDhDmDDMrs29yzAKQxdusD0r6YhOVWLRXBb5jZm9tWdxsAFlA8m1Ju1sKxtrdKPB3Saeb2YMtK5obIM9efLh7TkvRWLsLBfaY2Y2tK5kVIIuzSHkeyS9bC8f6kypwo5ntGaOC2QGygKR8aL9f0tFjiMgeoyrwZTMrnzdHOWYJyAKSYyV9RdJbRlGSTVor8DdJF5nZD1pvdPj6swXkUJPufoWk8jpiTGHZa60KfKtc0Wtm5RF+ox6zB2RxNnn1AhLOJqPaq2qz8hfymyV9veXfOZZVmAKQw84mz5VUrvEpr52Syrdexw38A9Uybfl5XIEnFg94fUzSoVcBY/L/npAKkPi8iESB/ygAIDgBBbZRAECwBwoACB5AgWEKcAYZphtZSRQAkCSDps1hCgDIMN3ISqIAgCQZNG0OUwBAhulGVhIFACTJoGlzmAIAMkw3spIoACBJBk2bwxQAkGG6kZVEAQBJMmjaHKbAvwGyE7Iy90AbtwAAAABJRU5ErkJggg==" style="box-sizing: initial; vertical-align: middle; border-style: none; max-width: 100%; background: rgb(18, 20, 21); border-radius: 4px;"></div></pre></details>

## HTML5 新属性

在 HTML5 中增加了很多新属性，帮助我们更加灵活地写代码。

下面会给大家介绍常用的新属性。

跟着我一起来学习吧～

### 新表单类型-email

`email` 类型用于邮件地址的输入，很明显，它只适用于邮箱输入。

使用格式如下：

```html
<input type="email" />
```

我们来练习一下吧！

新建一个 `index3.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      email: <input type="email" />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615964622502)

从上面的效果我们可以看出，如果你输入的邮箱格式不正确，当你点击提交按钮时，会提醒你格式错误。

### 新表单类型-url

`url` 类型是专门用来输入网址的。

使用格式如下：

```html
<input type="url" />
```

我们来练习一下吧！

新建一个 `index4.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      url: <input type="url" />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615965919187)

从上图可以看出，如果你输入的字符不是一个网址，点击提交后，会提示你这个输入框需要输入一个网址。

### 新表单类型-number

`number` 类型用于数字的输入。

`number` 类型表单有以下属性。

| 属性  | 描述                                                |
| ----- | --------------------------------------------------- |
| max   | 输入框允许的最大值。                                |
| min   | 输入框允许的最小值。                                |
| step  | 合法的数字间隔，例如 step=2，则合法为：2、4、6、8。 |
| value | 默认值。                                            |

例如：

```html
<input type="number" value="5" step="2" />
```

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/89aea9ec442294a35750fc2f1a6fae3a-0)

设置默认值为 5，步长为 2，每点 ⬆️ 一次，数字 + 2。

练习要求：

新建一个 `index5.html` 文件，页面上有个 number 类型的输入框和一个提交按钮，输入框中输入的最大值为 10。

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615967522154)

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; touch-action: manipulation; display: list-item; cursor: pointer; outline: none;">参考答案</summary><pre style="box-sizing: border-box; font-size: 14px; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; margin-top: 0px; margin-bottom: 1rem; overflow: visible; display: block; color: rgb(157, 154, 149); position: relative; word-break: break-all; border-radius: 4px; white-space: pre-wrap;"><code class="language-html hljs xml" style="box-sizing: border-box; font-size: inherit; font-family: &quot;Source Code Pro&quot;, Consolas, monospace; color: rgb(174, 174, 160); overflow-wrap: break-word; word-break: normal; display: block; overflow-x: auto; padding: 0.5em; background: rgb(19, 20, 21);"><span class="hljs-meta" style="box-sizing: border-box; color: rgb(124, 119, 110);">&lt;!DOCTYPE <span class="hljs-meta-keyword" style="box-sizing: border-box;">html</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">html</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">lang</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"en"</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">head</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">charset</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"UTF-8"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">meta</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">name</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"viewport"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">content</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"width=device-width, initial-scale=1.0"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">title</span>&gt;</span>Document<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">title</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">head</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">body</span>&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">form</span>&gt;</span>
      number: <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">input</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">type</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"number"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">max</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"10"</span> /&gt;</span>
      <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">input</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">type</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"submit"</span> <span class="hljs-attr" style="box-sizing: border-box; color: rgb(187, 40, 93);">value</span>=<span class="hljs-string" style="box-sizing: border-box; color: rgb(173, 164, 86);">"提交"</span> /&gt;</span>
    <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">form</span>&gt;</span>
  <span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">body</span>&gt;</span>
<span class="hljs-tag" style="box-sizing: border-box; color: rgb(174, 174, 160);">&lt;/<span class="hljs-name" style="box-sizing: border-box; color: rgb(187, 40, 93);">html</span>&gt;</span>
</code><div class="btn-copy" style="box-sizing: border-box; position: absolute; display: flex; flex-direction: column; align-items: center; width: 18px; right: 8px; top: 8px; cursor: pointer; opacity: 0; transition: opacity 0.3s linear 0s; word-break: normal; white-space: normal;"><img class="icon-copy" title="copy" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAYAAACtWK6eAAALCElEQVR4Xu2dXchlZRXH/+uiyDAV7SIm+pg+MBvxow9IpNTArFCbQrS6iKhJ+zCwspu8UKOb6MML+8BREypTCCslI6xw1IiCbMopSTCxEiSKagy8qIsVD52hSXrfs85+zrP3c/b6bTjMxbvW86z1X//fu8857569TRwogAJbKmBogwIosLUCAII7UGAbBQAEe6AAgOABFBimAGeQYbqRlUQBAEkyaNocpgCADNONrCQKAEiSQdPmMAUAZJhuZCVRAECSDJo2hykAIMN0IyuJAgCSZNC0OUwBABmmG1lJFOgGEHc/RdJuScce9joiyRx6bfMOSfea2f29Fti6rkkBcfcTJF0s6WxJu1o3y/qDFfi4mX12cPYGJ04CiLs/Q9LHJF0u6ZgN1i9T6a81sx9narj0Ojog7n6upE9KOjWb2Bve78/M7DUb3sPK5Y8KiLt/SNIXVq6ShF4U2Glmj/ZSzBh1jAaIu39A0pfGaIo9mikAIC2kdffXSbqnxdqsOZoCB8zspNF262Sj5mcQdz9R0p2Snt9Jz5QxTIGrzeyqYambmzUGINctvsrdXJWo/JtmdmFGGZoC4u6vlPTzgcI+IukPA3NJW48CZQY/MrNvrGe5zVulNSCrnj3uk3STpPvM7OHNk5OK56ZAM0DcvVwm8tjispGIbinf40aEIWY6BVoC8jZJtwVb22FmjwdjCUOB0RRoCcj1kvYEOuHMERCJkGkUaAnIAUnlK97tjiclvYSzxzTDZ9flCrQE5J+SnrakhP1m9orlZRKBAtMo0AQQd3+RpN8FWrrFzN4ZiCMEBSZRoBUgZ0q6O9ARnz8CIhEynQIAMp327LwBCgDIBgyJEqdTAECm056dN0ABANmAIVHidAoAyHTas/MGKAAgGzAkSpxOAQCZTnt23gAFUgLi7i+XVP6vyvGSXibpuA2Y1ZxLLJccPXToZWb7emk2DSDu/kZJZ0g6j5vU9WK/Lev48+JK8HvM7NYpq509IO5+uqQPS7poSqHZe7AC5bane81s7+AVKhJnDYi7f17SRyr0IbUfBQool4/99mu2gLj7TySd1s98qWQNCvxL0hvGhGSWgLi7r2EYLNGvArvM7MExypsdIO5+syQuoR/DPdPuMQokswLE3T8l6Ypp58buIynwG0kXtj6TzAYQd399uYfTSMNhmz4UKN9uXdKylDkBUm5v+uaWYrF2lwq8quUTsGYBiLu/V9INK4zvL5I+LekBSb8ysz+tkEvomhVw9yMllRtjl1d54tgqz45pehaZCyB3LR7jFhlduXvjbjP7aySYmPEVcPdV5nlQ0gvMrPy79mPjAXH3561wD9/bzOyCtavIgmtXwN2vkXRZcOF3mdnXgrErhc0BkEslXRvsmjs4BoXqIczd90sqTz9edjT7xTcHQD4n6aPLFJTEHVQCIvUU4u7nS7o9UNMvzKxcnb32Yw6AlLvBvzugzDlmVt7bcmyIAu7+dEnlyt6jlpT8qJntbNHWHAApD7svl7BvdzxhZke3EJA12yrg7t+XdM5U850DIOUGdeVGddsd+8zsrLajZPUWCrh7eezblcvWNrMmXm6yqLuPdmdFdweQZe7Z4J8DSOWDIQFkg90fKB1AACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whAAIged0f6BxAACRgk7whcwXkKEkHA2M9z8y+G4jbMsTd75Z05pI19pnZWTX7kDuNArMEpEjp7rdLOn+JrDvM7PEa6QGkRr3+c+cMSPmtXn67b3XsNbNLakcEILUK9p0/W0AWZ5H3S/qMpCOfMoarrfKzx6H1AKRvg9dWN2tAFpCcLOlUSS+U9EdJvzezH9YKByDrUrDvdWYPSGv5OYO0Vnja9QGkUn8AqRSw83QAqRwQgFQK2Hk6gFQOCEAqBew8HUAqBwQglQJ2ng4glQMCkEoBO08HkMoBAUilgJ2nA0jlgACkUsDO0wGkckAAUilg5+kAUjkgAKkUsPN0AKkcEIBUCth5OoBUDghAKgXsPB1AKgcEIJUCdp4OIJUDApBKATtPB5DKAQFIpYCdpwNI5YAApFLAztMBpHJAAFIpYOfpAFI5IACpFLDzdACpHBCAVArYeTqAVA4IQCoF7DwdQCoH5O53STp7yTKPmNmLK7cifQIF3P0aSZct2fqgmR3TojxrseiYa7r7LZLeHtjzpWb2cCCOkI4UcPf9kk5ZUtIBMzupRdlzAORaSZcGxHmPmd0UiCOkEwXc/XhJvw2Uc6eZnRuIWzlkDoBcJenKQOc/NbPTAnGEdKKAu18n6eJAOWu5S+f/22cOgJTTbzkNR44bzOx9kUBiplXA3d8k6XvBKtZ2p86n7rfxgJSG3P3XknYFxXyHmd0ajCVsAgXc/URJB4JbPynp5FafL+cCSOSbjsP1/qqkvZIeMLN/BAdBWGMF3L3covYCSZ9YYavrzSzyNmyFJf8bOhdAyle490raMUCFhyRVPYJhwJ6k/K8Cz5J0gqRnDhDmDDMrs29yzAKQxdusD0r6YhOVWLRXBb5jZm9tWdxsAFlA8m1Ju1sKxtrdKPB3Saeb2YMtK5obIM9efLh7TkvRWLsLBfaY2Y2tK5kVIIuzSHkeyS9bC8f6kypwo5ntGaOC2QGygKR8aL9f0tFjiMgeoyrwZTMrnzdHOWYJyAKSYyV9RdJbRlGSTVor8DdJF5nZD1pvdPj6swXkUJPufoWk8jpiTGHZa60KfKtc0Wtm5RF+ox6zB2RxNnn1AhLOJqPaq2qz8hfymyV9veXfOZZVmAKQw84mz5VUrvEpr52Syrdexw38A9Uybfl5XIEnFg94fUzSoVcBY/L/npAKkPi8iESB/ygAIDgBBbZRAECwBwoACB5AgWEKcAYZphtZSRQAkCSDps1hCgDIMN3ISqIAgCQZNG0OUwBAhulGVhIFACTJoGlzmAIAMkw3spIoACBJBk2bwxQAkGG6kZVEAQBJMmjaHKbAvwGyE7Iy90AbtwAAAABJRU5ErkJggg==" style="box-sizing: initial; vertical-align: middle; border-style: none; max-width: 100%; background: rgb(18, 20, 21); border-radius: 4px;"></div></pre></details>

### 新表单类型-range

`range` 类型用于包含一定范围内数值的输入。

其使用格式为：

```html
<input type="range" />
```

接下来我们练习一下吧！😁

新建一个 `index6.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      number: <input type="range" />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615969867908)

### 新表单类型-date

`date` 是用来选取年、月、日的类型。

其使用格式为：

```html
<input type="date" />
```

`datetime-local` 是用来选取年、月、日和本地时间。

其使用格式为：

```html
<input type="datetime-local" />
```

这里我们用 `date` 和 `datetime-local` 两个日期选择控件来做一下练习。

新建一个 `index7.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      date： <input type="date" /> <br />
      datetime-local：<input type="datetime-local" /> <br />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615971153569)

### 新表单类型-search

`search` 类型的 `input` 标签提供用于输入搜索关键字的文本框，从外观看 `search` 和 `text` 是一样的，功能也是相近的可以输入任意的字符串。

使用格式如下：

```html
<input type="search" />
```

我们来练习一下吧！💪

新建 `index8.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      search: <input type="search" />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210317-1615972352913)

从例子中，同学们似乎也不能从外观和功能上能发现 `search` 类型和 `text` 类型的区别。那么我们为何还要学 `search` 类型呢？🤔

如果使用不同的浏览器去看，就会发现有细微的差异，比如 Chrome 浏览器给 `search` 类型的输入框提供了清空按钮。如果在移动端的话，虚拟键盘会根据不同类型的输入框给出不同的反应。还有就是起到语义化的作用，我们一眼能够明白这里的 `input` 是起到搜索的效果。

### 新表单类型-color

`color` 类型是 `input` 标签提供的专门用于设置颜色的文本框。通过单击文本框可以打开一个调色板，用户可以在面板中选择需要的颜色。不同的操作系统打开的拾色面板也不相同。

我们来练习一下吧！💪

`index9.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      color: <input type="color" />
      <input type="submit" value="提交" />
    </form>
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4421/1347963/34e724c29327a454eac005718cf83534-0)

### 新属性-form

HTML5 中 `input` 标签新增了一个 `form` 属性，通过该属性可以将表单元素绑定到指定的 `form` 标签上，这样就可以灵活进行布局，同时一个表单元素可以从属于多个表单，这就让表单和表单元素的组合变得更加灵活。

我们来练习一下吧！💪

新建 `index10.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form id="myForm1" action="#" method="GET"></form>
    <form id="myForm2" action="#" method="POST"></form>
    提交到 myForm1：<input type="text" form="myForm1" name="myForm1" />
    <input type="submit" value="提交" form="myForm1" />
    提交到 myForm2：<input type="text" form="myForm2" name="myForm2" />
    <input type="submit" value="提交" form="myForm2" />
  </body>
</html>
```

点击预览页面，实验效果如下：

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/6006292d57a38a7822689b6036aac02d-0)

我们把第一个 `text` 类型的输入框绑定到 `myForm1` 上，我们把第二个 `text` 类型的输入框绑定到 `myForm2` 上。

### 新属性-autofocus

打开一个页面，当某个文本框需要获得光标焦点时，可以使用 `autofocus` 属性来实现。

例如，百度搜索页面，用户的鼠标点击搜索栏会获得光标焦点，用户直接输入需要搜索的内容即可，这种设置可以很好地提高用户体检。

![图片描述](https://doc.shiyanlou.com/courses/3773/1347963/c3378d960f68c3131c974c830f40c813-0)

我们来练习一下吧！💪

新建 `index11.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      <input type="text" autofocus /> <input type="submit" value="搜索" />
    </form>
  </body>
</html>
```

点击预览页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210318-1616047467620)

### 新属性-autocomplete

`autocomplete` 属性是用来规定表单是否应该启用自动完成功能。

自动完成功能就是当用户输入一次数据过后，再次输入相同的数据时可以自动补全内容。

`autocomplete` 属性包括两个属性值：on、off。

其语法格式为：

```html
<form autocomplete="on"></form>
```

`on` 为默认值，意思是启用自动完成功能。

```html
<form autocomplete="off"></form>
```

`off` 为禁用自动完成功能。

我们来练习一下吧！💪

新建 `index12.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form autocomplete="on">
      您最喜欢前端技术: <input type="text" list="selectList" />
      <datalist id="selectList">
        <option>html</option>
        <option>css</option>
        <option>js</option>
        <option>vue</option>
      </datalist>
      <input type="submit" />
    </form>
  </body>
</html>
```

点击预览页面，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210318-1616050250970)

### 新属性-placeholder

`placeholder` 属性规定可描述输入字段预期值的提示信息，也就是说设置了该属性，它会提示用户设置的输入值。

其语法格式为：

```html
<input placeholder="text" />
```

我们来练习一下吧！💪

新建 `index.html` 文件，在其中写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <form>
      <input type="text" placeholder="姓名" />
      <input type="text" placeholder="性别" />
    </form>
  </body>
</html>
```

打开预览页面，效果如下。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210331-1617180543706)

## 实验总结

本节实验主要给大家介绍了 HTML5 中的两大块内容：语义化标签和新属性。

其中，我们讲解了用于布局的 6 个基本语义化标签，分别是：

- `header` 标签是头部区域。
- `nav` 标签是导航区域。
- `article` 标签是内容区域。
- `section` 标签是文档中部分内容区域。
- `aside` 标签是侧边内容栏区域。
- `footer` 标签是底部信息区域。

还讲解了与多媒体相关的语义化标签，分别是：

- `audio` 标签：添加音频文件。
- `source` 标签：设置多数据源播放。

最后给大家介绍了新增的表单类型和一些常见的新属性。