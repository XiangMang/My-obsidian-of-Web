## 实验介绍

欢迎来到本章节～

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/6523edc8414d683411a8703f26332814-0)

本节实验带大家来认认真真与 Element UI 交个朋友。我会带着大家过一遍官网上的内容，然后说一说如何在 Vue 项目中配置 Element UI，最后会通过一个小 demo 带大家体验一把 Element UI 组件的使用。

快点击下一步 👇，进入实验吧～

#### 知识点

- 认识 Element UI
- Element UI 与 Vue
- Element UI 使用

## 认识 Element UI

Element UI 目前提供了 56 个组件，分成了 6 大类，分别是基础组件、表单类组件、数据类组件、提示类组件、导航类组件和其他类型组件。作为一个 UI 组件库，提供这些丰富的组件能很好地满足大部分 PC 端业务开发需求。同时，若提供的组件无法满足需求，还能对它进行二次开发，节省了开发者的时间。

首先，我们访问一下 Element UI 的[官网](https://element.eleme.cn/#/zh-CN)，逛一逛这个站点。

引入眼帘的是官网首页，如下图所示：

![2-1](https://doc.shiyanlou.com/courses/3815/1438123/ad947d674d2ead6f0b850bbbd56e7ee8-0)

从网站上的导航栏可以看出，官网分为四个部分：**指南**、**组件**、**主题**和**资源**。

然后，我们点击 “指南”，可以发现这部分的内容分为 2 块：**设计原则**和**导航**。其中，包含四个设计原则（一致、反馈、效率、可控），而导航这部分的内容主要讲解是 Element UI 提供的导航功能。它将导航功能分为 “侧栏导航” 和 “顶部导航”，在项目设计工程中选择合适的导航类型能帮助用户降低产品的学习门槛。官方就提到了这两类导航之间的区别：

1. **侧栏导航**：提高导航可见性，方便页面之间切换。
2. **顶部导航**：顺应了从上至下的正常浏览顺序，方便浏览信息，但也限制了导航的数量和文本长度。

接着，我们在官网的顶部导航中点击 “组件”，这部分的内容就是我们平时开发过程中**常用**到的部分了。显而易见，”组件“ 板块提供了 6 大类型的组件，每个组件的下方还附有源码示例，也可以在 [CodePen](https://codepen.io/trending) 中运行源码，如下图所示。

![2-2](https://doc.shiyanlou.com/courses/3815/1438123/544c33a6130ee68b1bcadfc9fff79cc4-0)

同时，在该板块还提供了使用指南等内容，方便开发者查阅。

接下来这个板块是 “主题” 。Element UI 的一大特色就是支持开发者自定义主题，你可以使用在线主题编辑器，可以修改定制 Element 所有全局和组件的 [Design Tokens](https://spectrum.adobe.com/page/design-tokens/)，并可以方便地实时预览样式改变后的视觉效果。

![2-3](https://doc.shiyanlou.com/courses/3815/1438123/2d61ea7246ac24c8cbdad751dcf40e8d-0)

最后一部分是 ”资源“，主要提供给设计师使用。Element UI 目前为 [Axure](https://www.axure.com/) 和 [Sketch](https://www.sketch.com/) 两种设计工具提供了插件，方便设计师在这些软件中进行设计时调用 Element UI 的组件，从而保证视觉风格的统一。

## Element UI 与 Vue

Element UI 是 UI 框架，而 Vue 是前端框架，UI 框架一般是伴随着前端框架产生的。虽然目前 Element UI 为 Angular 和 React 也提供了组件库，但国内大多数开发者还是用它与 Vue 配合使用进行开发。

通常情况下，我们可以利用 Vue CLI 创建一个前端项目，然后引入和配置 Element UI。例如，当你使用 Vue CLI 生成了一个初始化 Vue 项目，你可以通过下面命令安装 Element UI：

```bash
npm install element-ui -S
```

接着在 `package.json` 文件中就会插入一条记录：

```json
"dependencies": {
    "element-ui": "^2.15.1"
}
```

这就表明 Element UI 已成功安装到你的 Vue 项目中了。通过 `import` 语法就可以在项目中引入 Element UI 进行使用。

看到上面的 npm 安装步骤，想必大家都已经跃跃欲试了，同学们不要着急，这里仅是让大家对于 Element UI 与 Vue 有一个初步的理解，接下来我带大家手把手搭建开发环境。😉

> 本课程是基于 Vue 来学习 Element UI，如果同学们对 [Element React](https://elemefe.github.io/element-react/#/zh-CN/quick-start) 和 [Element Angular](https://element-angular.faas.ele.me/guide/install) 感兴趣，可以自行查看官方文档。

## 使用 npm 来创建 Vue 项目

也可以基于命令行工具 [Vue CLI](https://cli.vuejs.org/) 的方式去搭建 Vue 环境，本课程我们基于这个工具去搭建环境。那我们开始吧！

首先，打开你们右侧的环境，环境已经为大家安装了 Vue，所以我们直接在命令行输入以下命令来创建一个名为 `vue-elementui` 的项目。

> 为了保证后面代码正常运行和配置一致，所以先安装下指定版本的 Vue CLI。

```bash
npm install -g @vue/cli@4.5.13
vue create vue-elementui
```

创建项目的过程中会让你选择预设的版本以及安装依赖时使用的包管理器。这里我们分别选择使用 `Default ([Vue 2] babel, eslint)` 和 `NPM` 作为预设以及包管理器。如下图所示。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/46ac492bf7f1e66df1881dab369b9128-0)

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/4f3da5447364b9da0eed9319adc30160-0)

选择之后，就进入安装进程中，安装成功后，我们可以看到创建的 Vue 项目文件，如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/0d9c31cff98e5403e01b189400ed544f-0)

然后，我们使用以下命令来初始化并启动项目。

```bash
cd vue-elementui
npm run serve
```

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/e4a976aaf3bb0f2f765070028749b97b-0)

此时，我们点击右侧的 **WEB 服务**按钮，发现显示如下：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/27277d8c93d699e4a2902a8f37d97313-0)

这是为什么呢？🤔

这是由于我们的线上环境只开放了 8080 端口，但是需要通过网站域名访问，而刚才打开的这个 devServer 服务器并没有与网站域名关联。

为了解决这个问题，我们需要在 `vue-elementui` 目录下创建一个 `vue.config.js` 文件，通过以下配置将该服务器映射到网站域名上：

```js
const HOST = process.env.HOST;
module.exports = {
  publicPath: "./",
  productionSourceMap: false,
  devServer: {
    host: HOST || "0.0.0.0",
    open: true,
    disableHostCheck: true,
  },
};
```

添加完上述配置文件后，需要在终端中使用 `ctrl+c` 关闭 Vue 项目启动的服务器，然后使用以下命令重新启动。

```bash
npm run serve
```

此时浏览器中显示的就是我们的初始化应用了，如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/63adc5787b3fc9ad72f1e047719729d6-0)

## 添加 Element UI 配置

前面我们只是利用 Vue CLI 初始化了基于 Vue 的项目，现在我们还需要添加 Element UI 配置。

在讲配置之前，我们先说一说 [Element UI 的安装](https://element.eleme.io/#/zh-CN/component/installation)。

#### 使用 npm 安装

我们在 `vue-elementui` 目录下命令执行以下命令：

```bash
npm i element-ui -S
```

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/1f053145ca8f5a71c91e7c121ace5247-0)

按照步骤操作的同学，上一步配置好域名映射后并没有关闭 devServer 服务，我们可以另开一个终端来执行 npm 安装，也可以用 ctrl+c 关闭服务后再安装。

安装成功后，我们打开 `vue-elementui\src\main.js` 文件，引入 Element UI。

[Element UI 的引入](https://element.eleme.cn/#/zh-CN/component/quickstart)有两种方式：**完整引入**和**按需引入**。

**完整引入**是把所有 Element UI 的组件都引入其中，在 `main.js` 中添加如下代码即可：

```js
// main.js

import Vue from "vue";
import ElementUI from "element-ui";
import "element-ui/lib/theme-chalk/index.css"; // 样式文件需要单独引入
import App from "./App.vue";

// Vue.config.productionTip = false;
Vue.use(ElementUI);

new Vue({
  render: (h) => h(App),
}).$mount("#app");
```

需要注意：

- 样式文件需要单独引入。
- 本门课后续的课程中都使用完整引入。

**按需引入**是只引入需要的组件。

我们需要 [babel-plugin-component](https://github.com/ElementUI/babel-plugin-component) 的帮助才能实现按需引入。

首先，使用以下命令来安装 babel-plugin-component。

```bash
npm install babel-plugin-component -D
```

然后，将 `.babelrc` 修改为以下内容。

```txt
{
  "presets": [["es2015", { "modules": false }]],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}
```

完成上述配置后，我们就可以按需引入了。比如我们引入 Button 和 Select，那我们需要在 main.js 中添加以下内容。

```js
import Vue from "vue";
import { Button, Select } from "element-ui";
import App from "./App.vue";

Vue.component(Button.name, Button);
Vue.component(Select.name, Select);
/* 或写为
 * Vue.use(Button)
 * Vue.use(Select)
 */

new Vue({
  el: "#app",
  render: (h) => h(App),
});
```

思考一下：按需引入和完整引入有什么区别呢？🤔

完整引入，即便你的代码没有使用所有组件，但所有的组件还是会被整体打包，这会造成模块资源占用的空间较大，而按需引入只会打包你用到的组件，使得项目的体积减小了。

ok！以上便完成了 Element UI 的引入，一个基于 Vue 和 Element UI 的开发环境已经搭建完毕，现在我们可以编写代码了。

## 使用 CDN 的方式创建页面

搭建一个 Vue 的环境有多种方式，除了上面使用 npm 来创建 Vue 项目，你也可以在 html 文件中通过 `<script>` 标签去引入 Vue，如下所示：

```html
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
```

在 html 文件中，同样使用 CDN 的方式引入 ElementUI：

```html
<!-- 引入样式 -->
<link
  rel="stylesheet"
  href="https://unpkg.com/element-ui/lib/theme-chalk/index.css"
/>
<!-- 引入组件库 -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
```

下面，我们创建一个 `index.html` 文件，写入以下代码来试一试。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 导入 ElementUI 的 CSS -->
    <link
      rel="stylesheet"
      href="https://unpkg.com/element-ui/lib/theme-chalk/index.css"
    />
    <!-- 导入 Vue -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <!-- 导入 ElementUI -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>
  </head>

  <body>
    <div id="app">
      <el-button type="primary">我是个按钮</el-button>
    </div>
  </body>
  <script>
    new Vue({
      el: "#app",
      data: function () {
        return {};
      },
    });
  </script>
</html>
```

效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/b7a3b5396b955ab02b52a506b21f87bd-0)

## Element UI 初体验

前面我们已经把 Vue + Element UI 的环境搭建好了，我们来小试牛刀吧～

一起预览下我们接下来要实现的小功能：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/1a87b8e4464631596c38c133bcc47051-0)

需要实现这个功能大致分为两步：

1. 实现 UI 界面。
2. 实现交互效果。

首先，我们要实现类似下图结构的一个小卡片。

![img](https://doc.shiyanlou.com/courses/5246/1347963/a27aa38d112eb335ac128552473b6bbb-0)

上图的界面类似于一张我们日常生活中见到的信件，卡片结构分为以下四部分：

- `TO`：收信人。
- `Content`：信的内容。
- `From`：寄件人。
- `Submit`：用于提交信件的按钮。

#### 实现卡片的 UI 界面

对案例的 UI 界面有了初步的认识之后，我们来看看如何利用 Element UI 来实现这个信件的界面。

在 `vue-elementui/src/App.vue` 文件中写入以下代码：

```html
<template>
  <div id="app">
    <el-card class="box-card clearfix">
      <!--收信人-->
      <div slot="header" class="clearfix">
        <span>To 小白</span>
      </div>
      <!--内容-->
      <div class="text item">
        嗨！小白，有一首诗我想念给你听：“草在结它的种子/风在摇它的叶子/我们站着，不说话/就十分美好”
      </div>
      <!--寄信人-->
      <p class="footer">From 小蓝</p>
      <el-button style="float:right;" type="text">Submit</el-button>
    </el-card>
  </div>
</template>

<script>
  export default {
    name: "App",
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }
  .text {
    font-size: 14px;
  }
  .item {
    margin-bottom: 18px;
  }
  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both;
  }
  .box-card {
    width: 480px;
  }
  .footer {
    font-size: 12px;
  }
</style>
```

> App.vue 是应用首页，是页面入口文件，所有页面都是在 App.vue 下进行切换的。

使用 `npm run serve` 命令运行之后，打开 `Web 服务`，显示效果如下：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/9483d493be3b0c0e64a2f8727e99915d-0)

如果已经运行过了，就不要反复运行，反复运行会造成多个端口的情况，平台只开放了 8080 端口，其他端口访问无效。

如果端口被占用我们可以使用以下两个步骤来释放端口：

- 查看 8080 的进程 PID：lsof -i:8080
- 杀死进程：kill PID

上述代码中，我们分别用到了 Element UI 中的 [el-card](https://element.eleme.io/#/zh-CN/component/card) 和 [el-button](https://element.eleme.io/#/zh-CN/component/button) 组件。从代码结构我们可以看出：

- `<template>` 标签中书写的是视图代码，我们信件的 UI 界面都在这里存放。
- `<script>` 标签中书写 Javascript 逻辑代码，用于控制视图的交互逻辑。
- `<style>` 标签中书写 CSS 样式代码，用于美化视图的外观。

由此，HTML + JavaScript + CSS 的代码在一个 `.vue` 格式的文件中体现，正符合单页面应用开发的思想。

## 添加逻辑交互

上面我们只是搭建了信件的 UI 界面，接下来我们需要实现写好信件之后，点击 `button` 按钮将信件发送出去。

在 `vue-elementui/src/App.vue` 的 `<script>` 标签添加以下代码。

```html
<script>
  export default {
    name: "App",
    methods: {
      onSubmit() {
        alert("发送成功!");
      },
    },
  };
</script>
```

其中，`methods` 这个属性用于添加函数方法。我们需要触发 `onSubmit` 方法的对象，那就是 `submit` 这个按钮。我们在按钮上添加 `@click` 属性，其值是调用的 `onSubmit` 方法。

```html
<el-button style="float:right;" type="text" @click="onSubmit">Submit</el-button>
```

此时，我们点击 `submit` 按钮，会弹出一个警告框。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/1a87b8e4464631596c38c133bcc47051-0)

到此，小卡片的 demo 就完成了～如果同学们对代码里的 Element UI 组件不太理解，没关系，课程的后续内容都会为大家讲到。

## 实验总结

通过本节实验的学习，我们知道了 Element UI 有六大类组件，分别是基础组件、表单类组件、数据类组件、提示类组件、导航类组件和其他类型组件。然后，我们学习了如何用 npm 安装和 CDN 引入这两种形式来使用 Element UI，最后我们实现了一个小卡片的案例，在案例中，我们使用 Element UI 的 el-card 和 el-button 组件来进行页面布局。其次，我们给 el-button 组件添加了交互逻辑。

从下一节实验开始，我们就正式踏入 Element UI 组件的世界。

本节实验的完整代码放在此处，有需要的同学可以点击[下载](https://labfile.oss.aliyuncs.com/courses/5246/vue-elementui.zip)。