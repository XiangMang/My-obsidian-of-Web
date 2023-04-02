## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

Vue 借鉴了 redux 和 flux 两种常用的数据流解决方案，开发了一个与 Vue 高度融合的数据流管理插件 Vuex。

下面我们一起来学习 Vuex 的相关知识吧～

#### 知识点

- Vuex 的简介
- Vuex 的安装与配置
- Vuex 的核心概念

## Vuex 的简介

#### 什么是 Vuex

Vuex 是一个专门为 Vue 应用程序开发的**状态管理模式**。通过它可以将 Vue 应用中所有组件的共享状态储存管理起来，并以一定的规则保证这些状态以一种**可预测**的方式发生变化。

只通过这些概念去理解它想必大家都比较懵懂，下面我们通过简单的举例为大家通俗地介绍下它。

#### Vuex 应用场景及工作原理

通过前面的学习我们知道，组件之间的通讯有父子和兄弟这两层关系。其中兄弟组件之间的通信较为复杂，我们借助于它们共有的父组件来负责信息的传递。其过程如图所示：

![img](https://doc.shiyanlou.com/courses/5428/1723100/388978a6a2fd47b81b9f009b206c12e8-0)

但实际上，随着业务逻辑的不断增多，难免会遇到相互之间没有任何联系的组件间共用响应式数据的情况。以[花礼网](https://m.hua.com/)和[京东移动商城](https://m.jd.com/)为例：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/6a1ba51706f0adbd8f391ea5dbff4134-0)

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/f5d617ae3a6929eecf14938ebdf85d0b-0)

上述类似的电商网站中，将商品数据添加到购物车这一应用场景中，如果详情页、首页的商品列表以及搜索列表页中，都需要通过点击按钮添加商品到购物车，并且在底部导航中可以看出动态的更新效果。由于层级较多，组件间关系复杂等因素，借助于传统的组件通信方式来实现就会非常繁琐，代码维护起来也及其费力。组件之间传递数据的过程可能是下面这种场景：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/442e4ef5e7cf0c25f1613a8e5d68a910-0)

针对这种情况，我们就可以使用状态管理器来作为组件件沟通的桥梁。它就像所有组件共用的状态（即响应式数据）管理中心，可以将多个组件共用的状态存储起来，供它们访问或修改，所有组件都可以通过它上下平行地通知其它组件该状态发生了变化。如图所示：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/c3bdd12c489bdf781f0e776d1293c161-0)

通过两个图之间的对比大家就会发现，状态管理器简化了组件之间的关系，以一种一对一的关系去更新它们的共享状态互不干扰，是真的香。😜

那么，该如何使用它呢？🤔

一起去看看吧～

## Vuex 的安装与配置

#### Vuex 的安装

与当前流行的其它插件和框架的安装方式相同，Vuex 也有直接引入式和安装到项目两种方式。

我们可以通过 [Unpkg.com](https://unpkg.com/) 提供的 CDN 链接直接在 HTML 中引入最新版和指定版本。语法如下：

```html
<!-- 引入最新版本 -->
<script src="https://unpkg.com/vuex"></script>
<!-- 引入指定版本 -->
<script src="https://unpkg.com/vuex@2.0.0"></script>
```

也可以通过 NPM 或 Yarn 将其安装在项目中。

```bash
# NPM 安装命令
npm install vuex --save
# Yarn 安装命令
yarn add vuex
```

在一个模块化的打包系统中，我们必须显式地通过 `Vue.use()` 来安装 Vuex：

```js
import Vue from "vue";
import Vuex from "vuex";

Vue.use(Vuex);
```

接下来，我们就一起动手在我们的单页面应用项目中安装 Vuex。

> 本节实验我们使用 npm 安装的方式来学习。

## Vuex 的核心概念

在 Vuex 中有五个核心概念，它们分别是 [State](https://v3.vuex.vuejs.org/zh/guide/state.html)、[Getters](https://v3.vuex.vuejs.org/zh/guide/getters.html)、[Mutations](https://v3.vuex.vuejs.org/zh/guide/mutations.html)、[Actions](https://v3.vuex.vuejs.org/zh/guide/actions.html) 和 [Modules](https://v3.vuex.vuejs.org/zh/guide/modules.html)。

接下来我们会通过示例为大家介绍 Vuex 的核心概念。

在介绍核心概念之前我们先在项目中安装 Vuex。

#### 在项目中安装 Vuex

首先，打开我们的线上环境，使用下面命令获取 Vue 项目文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/10532/first-vuex.zip && unzip first-vuex.zip && rm first-vuex.zip
cd first-vuex
npm install
```

然后，使用以下命令快速将 Vuex 安装到我们的项目中：

```bash
npm install vuex@3.6.2
```

> 因为 Vue 2 中只能使用 vuex 3 所有这里我们下载指定版本的 vuex。

安装成功后我们会在 `package.json` 中找到它的相关信息：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/acb29e7ab126f67dae3831838fdfb9d0-0)

## 核心概念之：State

首先，在 `main.js` 文件中写入以下代码：

```js
import Vue from "vue";
import App from "./App.vue";
import Vuex from "vuex"; // 导入 Vuex

Vue.use(Vuex); // 使用 Vuex，让 Vuex 可以访问到 Vue
Vue.config.productionTip = false;

// 创建 Store 实例
const store = new Vuex.Store({
  state: {
    count: 0, // 计数器的初始值
  },
});

new Vue({
  store, // 注入 Store
  render: (h) => h(App),
}).$mount("#app");
```

有同学可能会问：为啥不叫 vuex 而是 store 呢？🤔

这是因为，Vuex 应用的核心就是 store（仓库）。它是一个用于存储组件共享状态（state）的容器，就像一个小型的数据仓库。它所有的功能和操作都是用于处理这个仓库中的状态而存在的，所以我们在创建 Vuex 配置的时候都是以 store 命名。

接下来，我们在 `App.vue` 中将计数器的状态展示出来，在文件中写入以下代码。

```html
<template>
  <div id="app">{{count}}</div>
</template>

<script>
  export default {
    name: "App",
    // 通过计算属性来访问 count
    computed: {
      count() {
        return this.$store.state.count;
      },
    },
  };
</script>
```

来这里我们就可以在页面上访问到 count 的数据了，当前页面会显示 0。

接下来，我们要实现点击按钮计数的功能，每点一次按钮数据 +1。

## 核心概念之：Mutations

在 `App.vue` 文件中定义一个按钮，新增代码如下：

```html
<!--绑定一个点击事件，用 increment 来执行 count++ 的逻辑-->
<button @click="$store.commit('increment')">++</button>
```

我们在 `main.js` 文件中增加 `mutations`，代码如下：

```js
const store = new Vuex.Store({
  // 此处省略 ...
  mutations: {
    increment(state) {
      state.count++; // 执行 count++ 的操作
    },
  },
});
```

计数器的功能就实现啦～ 🎉 效果如下：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/6166336bf2d9cde9377a48e254cb9099-0)

到此我们已经实现了一个最简单的 Vuex 状态管理，从上面的使用我们可以看出 `state` 就是用来存储和初始化状态。

通过上面简单的示例，我们知道了 Vuex 主要是用来存储并管理组件共享状态的。

## 核心概念之：Actions

有时候我们需要向后台发出一些异步请求，我们不能直接在 `mutations` 里进行操作，这时就可以在 `actions` 中定义一些异步操作。

下面我们来模拟一下异步操作，在页面上新增一个按钮，触发 `count--` 的操作。在 `App.vue` 中新增以下代码：

```html
<button @click="$store.dispatch('decrement')">--</button>
```

> 注意哦！！！ Actions 是通过 `store.dispatch` 方法来触发 `actions` 更新 `state` 状态。

在 `main.js` 文件中新增以下内容。

```js
const store = new Vuex.Store({
  mutations: {
    decrement(state) {
      state.count--;
    },
  },
  actions: {
    decrement({ commit }) {
      setTimeout(() => {
        // 通过 commit 交给 mutations 去处理
        commit("decrement");
      }, 500);
    },
  },
});
```

到这里我们 `count--` 的功能也实现了，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/23828431d3d026838a875127d37f4ca2-0)

#### actions 与 mutations 的区别。

`actions` 类似于 `mutations`，不同的是：

- `actions` 中的更新函数最终仍是通过调用 `mutations` 中的函数来更新状态的，不能通过它直接变更状态。
- 与 `mutations` 不同，`actions` 中可以包含任意异步操作。

关于 `mutations`、`actions` 等的用法还有其它形式，这些在官网上都有详细的 API，大家可以根据[官网 API](https://next.vuex.vuejs.org/zh/guide/actions.html) 对它们进行更多更深入的了解，这里就不再一一细说了。

## 核心概念之：Getters

`getters` 可以帮助我们缓存数据。

我们增加一个每次计数增加两倍的功能，在 `main.js` 中新增以下代码：

```js
getters: {
    doubleCount(state) {
      return state.count * 2
    }
}
```

然后在页面上获取数据，在 `App` 文件中新增以下代码：

```html
{{$store.getters.doubleCount}}
```

这样，当点击 ++ 按钮时，计数会以乘 2 的形式增加。效果如下：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/087f5d85586c7eea863c534e9c39923a-0)

## Vuex 规则

在实际开发中 Vuex 并不会限制我们的代码结构。但是，它规定了一些需要遵守的规则：

1. 应用层级的状态应该集中到单个 store 对象中。
2. 提交 mutation 是更改状态的唯一方法，并且这个过程是同步的。
3. 异步逻辑都应该封装到 action 里面。

只要你遵守以上规则，如何组织代码随你便。

不过随着业务的增多，我们可能会面临这样一个问题：由于 `state`、`mutations`、`getters`、`actions` 存储的内容越来越多，会导致 store 文件及其庞大，开发和维护起来变得困难。没关系，学习过 ES6+ 的同学都知道模块化的概念，这里我们可以将它们作为单独的文件从 store 中分割出去。这样做对于大型应用开发来说在合适不过。😊

我们可以将 store 分割为如下所示的结构：

```txt
└── store
    ├── index.js          # 我们组装模块并导出 store 的地方
    ├── state.js          # 根级别的 state
    ├── getters.js        # 根级别的 getters
    ├── actions.js        # 根级别的 action
    ├── mutations.js      # 根级别的 mutation
```

## 核心概念之：Module

不过，前面对于 `store/index.js` 的分割并不是最小单元，我们在开发中仍然面临类似的问题。

有同学开始疑惑了：还有什么问题？

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/3847634a6285e2c20e4aac46bae6eca1-0)

这要从 Vuex 的第一条规则说起。

来回顾下它的第一条规则：应用层级的状态应该集中到单个 store 对象中。

这句话也就意味着，一个应用的所有状态都会集中到一个比较大的对象中，当我们的应用变得非常复杂时，store 对象就有可能变得相当臃肿，其形式参考下图：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/72aead6e0d7a1ea5867ed7f2f4eea442-0)

从图中可以看到，所有业务模块的 `state`、`mutations` 等都存储在一个对象中，这使得我们的代码又一次变得复杂了。😫

这并不能仅靠将 `state`、`mutations` 等对象从 `store/index.js` 文件中分割出来就能解决。

理想状态应该是这样的，我们可以按照业务逻辑划分为单个的 store，里面包含该模块中的 `state`、`mutations` 等。就像下图那样：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/f6380c3cbfc7d6e2ff57334e2f8f265b-0)

这样怎么实现呢？🤔

实际上 Vuex 已经为我们考虑到了，并给出了解决方案，那就是 Vuex 的另一个核心概念——[Modules](https://vuex.vuejs.org/zh/guide/modules.html)。

如前面所说，由于使用单一的状态树，应用的所有状态会集中到一个比较大的对象中。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。

为了解决这个问题，Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/f2edac6224137daed69e78647e03c285-0)

具体语法如下：

```js
const moduleA = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态
```

分割后的项目结构如下：

```txt
└── store
    ├── index.js          # 我们组装模块并导出 store 的地方
    ├── state.js          # 根级别的 state
    ├── getters.js        # 根级别的 getters
    ├── actions.js        # 根级别的 action
    ├── mutations.js      # 根级别的 mutation
    └── modules
        ├── cart.js       # 购物车模块
        └── products.js   # 产品模块
```

至此，前面的问题便迎刃而解了。🎉

## 实验总结

本节实验我们学习了 Vuex 的安装与配置，并通过示例了解到它的几个核心概念 State、Getter、Mutation、Action 以及 Module 的作用及基本使用方式。

通过示例可以体会到 Vuex 状态管理器在简化组件间数据传递方面为开发带来的便利，不过状态管理器也不是所有组件传参的替代方案，大家要在使用前先对实际情况进行分析，把它用在必要的地方。