## 实验介绍

嗨！欢迎大家进入 Vue 的学习～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节将带领大家了解 Vue.js 是一个什么样的前端框架，与其他框架的区别和特点，以及怎么去安装使用它。

#### 知识点

- Vue 与其他框架的对比及特点
- 安装 Vue 的方法
- node 的安装
- vue-cli 的安装
- Vue 开发者工具的安装
- Vue 创建实例
- Vue 数据的双向绑定及响应式

#### 官网

- 中文：https://cn.vuejs.org/
- 英文：https://vuejs.org/

## Vue.js

#### Vue.js 是什么

Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[现代化的工具链](https://cn.vuejs.org/v2/guide/single-file-components.html)以及各种[支持类库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。<信息来源：Vue 官网>

#### 作者

尤雨溪毕业于上海复旦附中，在美国完成大学学业，本科毕业于 Colgate University，后在 Parsons 设计学院获得 Design & Technology 艺术硕士学位，任职于纽约 Google Creative Lab。<信息来源：百度百科>

#### 作用

Vue.js 框架的作用主要注重动态的构建用户界面，前端工程化和模块化开发。

#### Vue 与其他框架的对比

| 框架    | 设计模式 | 数据绑定 | 灵活度 | 文件模式  | 复杂性 | 学习曲线           | 生态 |
| ------- | -------- | -------- | ------ | --------- | ------ | ------------------ | ---- |
| Vue     | MVVM     | 双向     | 灵活   | 单文件    | 小     | 缓                 | 完善 |
| React   | MVC      | 单向     | 较灵活 | all in js | 大     | 陡                 | 丰富 |
| Angular | MVC      | 双向     | 固定   | 多文件    | 较大   | 较陡（Typescript） | 独立 |

Vue 是一个推陈出新的前端框架，吸收了很多前端框架的优点。例如，Vue 借鉴了 React 的组件化和虚拟 DOM ，借鉴了 Angular 的模块化和数据绑定。因此，我们以 Vue.js 作为入手，以后深入学习其他框架，你会发现他们的共通之处，更好地高效地学习。

选择 Vue.js 的更多原因是，就框架的 API 而言，对比之下，Vue 更加轻便简洁。Vue 自身拥有开箱即用的生态开发包（[Vuex](https://vuex.vuejs.org/)、[Vue-Router](https://router.vuejs.org/)）等，复杂性低、学习成本低，是一门比较好入门的前端框架。

如果你刚开始学习前端开发，将框架作为你的第一步可能不是最好的选择，推荐进入实验楼前端基础知识课程。假入你已掌握了关于 `HTML`、`CSS` 和 `JavaScript` 的中级知识，那让我们进入 Vue 的学习吧!

## 安装

#### CDN 引入

不用下载到本地，即引即用，学习推荐使用这种模式：

推荐 2 个较稳定的 cdn，以下任选其一

```js
<script src="https://cdn.jsdelivr.net/npm/vue@2.7.10/dist/vue.js"></script>
<script src="https://cdn.jsdelivr.net/npm/vue@2.7.10"></script>
```

> 由于非会员用户无法访问外网，所以统一使用引用链接为 `https://labfile.oss.aliyuncs.com/courses/1262/vue.min.js`。

#### 脚手架工具

> 线上环境已经安装好了所需工具，直接使用即可。步骤 1、2、3 可以直接略过。

1、`vue-cli` 是基于 `npm` 的，所以应该先安装 `node` 环境，通过 `node` 官网：http://nodejs.cn/ 下载系统对应的 `node` 安装程序。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/5d025419eb391e95161af79af909211e-0)

**注意：** NPM 是随同 Node.js 一起安装的包管理工具。因此当我们安装好 Node.js 的时候，也安装好了 NPM。由于在线上环境下已经安装好了 Node.js，大家可以直接使用，不用安装 Node。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/a625f5a377a503e88e466d44f7d495e1-0)

2、`node` 安装完毕使用，`npm` 包管理工具安装 `vue-cli`。

```bash
npm i -g @vue/cli-init
```

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/84870ea7cad9c743085aa6ae8d4960bb-0)

3、命令行输入 `vue`，出现 Usage 表示安装成功。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/c2c30346646ab85def15d4a8b095a43c-0)

4、使用 `vue create` 命令来创建一个 Vue 项目。

```bash
vue create first-vue # 这里的 first-vue 项目名
```

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/accc5f203ebe7fd2561e5a8025f20a65-0)

> 由于线上环境只开放了 8080 端口，所以我们需要在 vue.config.js 进行以下配置。

```js
const HOST = process.env.HOST;
module.exports = {
  publicPath: "./",
  productionSourceMap: false,
  devServer: {
    host: HOST || "0.0.0.0",
    open: true,
    historyApiFallback: true,
    allowedHosts: "all",
  },
};
```

5、完成配置后，使用以下命令将 Vue 项目运行起来。

```bash
cd first-vue
npm run serve
```

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/0d121e01a52e2526d2cd5fb907b49b50-0)

6、成功执行命令行后，我们打开右侧的 Web 服务，即可访问项目的页面。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/effdc7af59632998745b9b4579f667ad-0)

#### vue 开发者工具安装

**注意：** 由于线上环境使用的是 Preview 或 Mini Browser 是一个轻量级的浏览器，不支持插件安装，如需安装，请在自己的电脑上对应安装。

在使用 Vue 时，我们推荐在你的浏览器上安装 [Vue Devtools](https://github.com/vuejs/vue-devtools#vue-devtools)。它允许你在一个更友好的界面中审查和调试 Vue 应用。

1、下载对应浏览器的 Vue Devtools。

- [Get the Chrome Extension](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd) / ([beta channel](https://chrome.google.com/webstore/detail/vuejs-devtools/ljjemllljcmogpfapbkkighbhhppjdbg))
- [Get the Firefox Addon](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/) / ([beta channel](https://github.com/vuejs/vue-devtools/releases))
- [Get standalone Electron app (works with any environment!)](https://github.com/vuejs/vue-devtools/blob/master/shells/electron/README.md)

2、打开浏览器，打开设置>开发工具>扩展程序，将下载好的 Vue Devtools 拖到界面中，即可完成安装(谷歌浏览器为例)。

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552636491907.png)

3、你就可以在浏览器中轻松调试你的 vue 应用。

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552636492331.png)

#### 更多安装方式

其他安装方式请参考：[官网教程](https://cn.vuejs.org/v2/guide/installation.html)

## 使用

后续教程我们会采用 cdn 引入的方式，来讲解知识点。

那么我们开始创建第一个 Vue 应用。

#### 创建第一个实例

每个 Vue 应用都是通过用 `Vue` 函数创建一个新的 **Vue 实例** 开始的：

```js
var app = new Vue({
  // 选项
});
```

Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统，我们新建一个 .html 后缀的文件，输入以下代码，运行（右击文件 > open with > Preview 或 Mini Browser），你就会看到 `{{msg}}` 被渲染成 `hello`。

使用以下命令获取 vue.js 文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/1262/vue.min.js
```

在 html 文件中写入以下代码。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>syl-vue-test</title>
    <!--引入 vue.js-->
    <script src="vue.min.js"></script>
  </head>
  <body>
    <div id="app">{{msg}}</div>
    <script>
      var app = new Vue({
        el: "#app", // dom 挂载点
        data: {
          // 数据项
          msg: "hello syl",
        },
      });
    </script>
  </body>
</html>
```

运行效果：

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552636493498.png)

**说明：** el 为实例挂载点，上面表示挂载在 id 为 app 的 dom 元素中。data 选项为数据选项，存放绑定数据。除了这两个之外还有实例选项，methods（实例方法）、computed（计算属性） 等，后面我们会学习到。

## 理解 Vue 的 MVVM 模式

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552636493741.png)

M：Model 即数据逻辑处理。

V：View 即视图（用户界面）。

VM：ViewModel 即数据视图，用于监听更新，View 与 Model 数据的双向绑定。

所以，Vue 一大特点就是数据双向绑定，另一大特点就是响应式，接下来，我们来看看它的魅力。

## 数据双向绑定

在 Vue 中数据双向绑定随处可见，最常见的是表单数据中的双向绑定，例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>syl-vue</title>
    <!--引入 vue.js-->
    <script src="vue.min.js"></script>
  </head>
  <body>
    <!-- 数据双向绑定 -->
    <div id="app">
      <input type="text" v-model="msg" />
      <p>{{msg}}</p>
    </div>
    <script>
      var app = new Vue({
        el: "#app", // el: 挂载点

        data: {
          // data:数据选项

          msg: "hello",
        },
      });
    </script>
  </body>
</html>
```

在我们对文本框输入值时，实例 data 中的 msg 值也随之变化。运行效果：

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552637277999.png)

#### 感受响应式

上面我们了解到 Vue 是一个 MVVM 架构的框架，成功创建了一个 Vue 应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue 在背后做了大量工作。现在数据和 DOM 已经被建立了关联，所有东西都是 **响应式的**。我们可以看看他是不是响应式的，打开你的浏览器的 JavaScript 控制台 (就在这个页面打开)，并修改 `app.msg` 的值，你将看到上例相应地更新，更改数据也触发视图的相应更新。

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid940410labid10292timestamp1552636492707.png)

## 实验总结

我们学习了以下内容：

- Vue 与其他框架的对比及特点
- 安装 Vue 的方法
- node 的安装
- vue-cli 的安装
- Vue 开发者工具的安装
- Vue 创建实例
- Vue 数据的双向绑定及响应式

本节内容让我们掌握了 vue 的基础安装，以及怎么样去实例化第一个 vue 应用，需要自己亲手去写代码，初步感受一下 vue 的神奇之处。