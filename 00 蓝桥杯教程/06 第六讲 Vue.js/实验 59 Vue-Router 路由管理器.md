## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验我们进入路由的学习。

不满足是向上的车轮，让我们加足马力开始出发吧～ 🚗

#### 知识点

- 前端路由的概念及作用
- Vue-Router 的安装
- Vue-Router 的基本使用

## 前端路由的概念及作用

需要大家注意的是，这里的路由可不是指我们日常生活中的路由器 😂 ，但是其实现原理基本相同。它代表一个 URL 与相应处理程序的映射关系。

用户在输入要访问的 URL 之后，路由会解析 URL 中的路径，之后根据映射表中的映射关系查找相应的预设函数，并将结果返回给用户，以此完成一次操作。

其工作流程如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/uid1723100-20211109-1636427844206)

以上图为例，当一个用户使用 `https://www.lanqiao.cn/a` 来访问网页时，Web 服务会接收到这个请求，然后解析 URL 中的路径 `/a`，在 Web 服务程序中该路径对应着响应的处理逻辑，程序会把请求交给路径所对应的处理逻辑，这样就完成了一次“路由分发”，这个分发就是通过“路由”来完成的。

简单地说，路由所做的工作就是：根据不同的 URL 地址展示不同的内容或页面。

前端路由不同于传统路由，它不需要服务器来进行解析，而是通过一个 hash 函数或者 H5 提供的 history API 来实现。一般使用前端路由的应用为不涉及到页面间跳转的单页面应用，也就是我们当下正在学习的。😄

> 关于前端路由的 hash 和 history 两种模式的实现，感兴趣的同学可以通过这篇《[前端路由实现方法](https://labfile.oss.aliyuncs.com/courses/5428/前端路由实现方法.pdf)》文章去了解。

#### 前端路由的优缺点

前端路由的优点如下：

1. **页面刷新速度快**：由于不需要向服务器发送请求，所以这个过程不会受到网络延迟的影响，实际上只是完成部分组件间的切换，因此页面的刷新速度会比较快，用户体验也更好些。
2. **复用性强**：由于使用前端路由的应用为单页面应用，所以代码中很多 CSS、JS 都可以共用，避免了过多的重复加载，大大提升了性能。
3. **页面状态可记录**：如果不使用前端路由，仅通过 Ajax 在页面进行局部切换的应用，由于页面 URL 始终保持不变，因此页面的状态是无法记录的，而前端路由很好的解决了这个问题。例如，使用了前端路由的应用中访问 `https://www.lanqiao.cn/a` 这个链接，再打开后会直接触发 `/a` 匹配的路由页面中的事件。

当然，前端路由也有一些缺点，比如使用浏览器的前进、后退键的时候，会重新发送请求，没有合理地利用缓存。

了解了前端路由的概念及原理，一起来看看今天要学习的前端路由——[Vue-Router](https://next.router.vuejs.org/zh/introduction.html)。

## Vue-Router 的安装

Vue-Router 是 Vue 的官方路由，专门为 Vue 的单页面应用量身打造。

其功能包括：

- 嵌套路由映射
- 动态路由选择
- 模块化、基于组件的路由配置
- 路由参数、查询、通配符
- 展示由 Vue 的过渡系统提供的过渡效果
- 细致的导航控制
- 自动激活 CSS 类的链接
- HTML5 history 模式或 hash 模式
- 可定制的滚动行为
- URL 的正确编码

与当前大部分流行的框架或插件的使用方式相同，Vue-Router 的安装也有 CDN 和 NPM 两种主流方式。如下所示：

#### CDN 引入

[Unpkg.com](https://unpkg.com/) 提供了基于 npm 的 CDN 链接。

```bash
https://unpkg.com/vue-router@2.0.0/dist/vue-router.js
```

#### NPM 安装

我们可以在项目文件夹下直接运行以下命令来安装 Vue-Router。

```bash
npm install vue-router@4
```

安装完成后，我们还需通过简单配置将 Vue-Router 与 Vue 实例联系在一起。

> 本节实验中我们使用 CDN 的方式来学习。

## Vue-Router 的基本使用

我们通过一个单页面应用来看看 Vue-Router 的使用，其基本步骤如下所示：

- 使用 `router-link` 组件来导航，其通过 `to` 属性来指定跳转链接（这相当于 HTML 中的 a 标签）。
- 使用 `router-view` 组件定义路由出口，路由匹配到的组件将会渲染到此处。
- 使用 `const routes = [{ path, component }]` 来定义路由（路径和组件名）。
- 使用 `const router = new VueRouter({})` 来创建路由实例，在其中传入上一步定义的路由配置 `routes`。
- 创建和挂载根实例，在 `new Vue` 中挂载上一步创建的路由实例 `router`。

步骤清楚了，我们来举个例子吧～

使用以下命令获取 Vue 和 Vue-Router 文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/1262/vue.min.js
wget https://labfile.oss.aliyuncs.com/courses/10532/vue-router.js
```

新建一个 `index.html` 文件，在文件中写入以下内容：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="vue.min.js"></script>
    <script src="vue-router.js"></script>
  </head>

  <body>
    <div id="app">
      <h1>路由的使用</h1>
      <p>
        <!-- 使用 router-link 组件来导航 -->
        <router-link to="/home">首页</router-link>
        <router-link to="/hot">热门</router-link>
        <router-link to="/class">分类</router-link>
      </p>
      <!-- 路由出口 -->
      <!-- 路由匹配到的组件将渲染在这里 -->
      <router-view></router-view>
    </div>
    <script>
      const Home = { template: "<div>首页</div>" };
      const Hot = { template: "<div>热门</div>" };
      const Class = { template: "<div>分类</div>" };

      // 定义路由
      const routes = [
        { path: "/home", component: Home },
        { path: "/hot", component: Hot },
        { path: "/class", component: Class },
      ];

      // 创建 router 实例，然后传 routes 配置
      const router = new VueRouter({
        routes,
      });

      // 创建和挂载根实例
      const app = new Vue({
        router,
      }).$mount("#app");
    </script>
  </body>
</html>
```

效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/c60ce628cc702cc13e22bfb688fbf9e0-0)

## 实验总结

本节实验先给大家介绍了前端路由的概念，然后给大家讲解了路由安装的两种方式，最后我们通过一个简单的路由示例为大家演示了路由的基本使用方法。

实验只是引导大家去学习路由，关于路由的更多知识，推荐大家直接阅读[官方文档](https://v3.router.vuejs.org/zh/installation.html)。