## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验我们要学习一个 AJAX 的封装插件—— Axios。

事不宜迟，我们开始吧～ 😊

#### 知识点

- 什么是 Axios
- Axios 基本用法
- Axios 与 Vue 的钩子函数的结合使用

## Axios 简介

#### 什么是 Axios

[Axios](http://www.axios-js.com/) 是一个基于 Promise 语法的、用于浏览器和 Node.js 的 HTTP 库。简单的理解就是对 Ajax 的封装，且具有易用、简洁、高效等特点。

#### Axios 的特点

它本身具备以下作用：

1. 可以从浏览器中创建 XMLHttpRequest。
2. 能从 Node.js 创建 HTTP 请求。
3. 支持 Promise API。
4. 能够拦截请求和响应。
5. 可以转换请求和响应数据。
6. 也可取消请求。
7. 可以自动转换 JSON 数据。
8. 在客户端支持防止 [CSRF/XSRF](https://baike.baidu.com/item/跨站请求伪造/13777878?fromtitle=CSRF&fromid=2735433&fr=aladdin) 攻击。

#### Axios 的安装方式

Axios 的安装与其他框架或插件类似，也是分为以下两种：

- **npm 安装**

```bash
npm install axios
```

- **使用 `<script>` 直接引入**

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

在本实验中，我们使用 `<script>` 直接引入的方式来学习它的用法。

#### Axios 基本用法

使用以下命令获取 axios 文件：

```bash
wget https://labfile.oss.aliyuncs.com/courses/10532/axios.min.js
```

首先，打开我们的线上环境，创建一个名为 `demo1.html` 的文件，并引入 `axios.js`。代码如下：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 引入 Axios 的 CDN -->
    <script src="axios.min.js"></script>
  </head>
  <body></body>
</html>
```

然后，创建一个名为 `test.json` 的文件，作为接下来使用 Axios 请求的数据文件，并写入以下数据：

```json
{
  "msg": "Hello Axios!"
}
```

最后，在 `demo1.html` 中使用 Axios 发送一个简单的 Ajax 请求，用于获取 `test.json` 中的数据，并输出在控制台：

```html
<script type="text/javascript">
  axios.get("./test.json").then((res) => {
    console.log(res);
  });
</script>
```

在 Web 服务器中访问 `demo1.html` 后效果如下：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/3bde7ea20aaba8ae47840b3f6dfc6e9c-0)

我们会发现，通过 Axios 获取到的数据实际上就是一个 Ajax 对象，真正需要我们请求的数据是该 Ajax 对象的 `data` 属性值。

上面这个例子只是 Axios 众多使用方式中的一种，它主要是用于执行 `get` 请求。

下面我们看几个它比较常用的使用方式。

1. 执行 `get` 数据请求。

```js
axios.get('url',{
  params:{
    id:'接口配置参数（相当于url?id=xxxx）'，
  },
}).then(function(res){
  console.log(res); // 处理成功的函数 相当于 success
}).catch(function(error){
  console.log(error) // 错误处理 相当于 error
})
```

1. 执行 `post` 数据请求并发送数据给后端。

```js
axios
  .post(
    "url",
    { data: {} },
    {
      headers: "xxxx", // 头部配置
    }
  )
  .then(function (res) {
    console.log(res); // 处理成功的函数 相当于 success
  })
  .catch(function (error) {
    console.log(error); // 错误处理 相当于 error
  });
```

1. 通用方式（适用于任何请求方式）。

```js
//-------------------get-----------------------//
axios({
  method: "get",
  url: "xxx",
  cache: false,
  params: {
    id: 123,
  },
  headers: "xxx",
});
//-------------------post-----------------------//
axios({
  method: "post",
  url: "xxx",
  data: {
    firstName: "Tom",
    lastName: "Sun",
  },
});
```

其中需要注意的是，`get` 和 `post` 请求中向后端传递参数的配置项名字不同：`get` 请求的需要使用 `params`，`post` 请求用于发送数据的为 `data`。

关于 Axios 的基本使用方式就为大家演示到这里，作为一个独立的强大的 HTTP 库，它的功能远不止这些，大家可以通过 [Axios 的官网](http://www.axios-js.com/)学习。后续的实验中，我们也会结合实际案例，为大家展示它的更多功能，这里就不再一一展开讲解。

接下来，让我们一起看看它是如何与 Vue 的钩子函数结合使用的。

## Axios 与 Vue 的钩子函数的结合使用

假设有这样一个需求：”当页面加载后我们就要展示一组数据到页面中“。

这个需求对于我们前端开发者来说稀松平常，因为对于大部分网页，我们需要保证的第一个需求基本上就是——这个页面加载后有数据展示。

那么，如果当前页面在使用 Vue 框架之后应该如何实现呢？🤔

有同学会说，这个我会。😼

于是大手一挥，创建了一个名为 `demo2.html` 的文件，并有了如下代码：

使用以下命令获取 vue.js 文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/1262/vue.min.js
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>syl-vue-test</title>
    <!-- 引入 vue.js -->
    <script src="vue.min.js"></script>
  </head>
  <body>
    <div id="app">
      <ul>
        <li v-for="item in dataList">{{item}}</li>
      </ul>
    </div>
    <script>
      var app = new Vue({
        el: "#app",
        data: {
          dataList: ["HTML", "CSS", "JavaScript", "Vue.js", "Axios"],
        },
      });
    </script>
  </body>
</html>
```

页面效果如下：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/f7e2778cce503e26e7c540106397c0db-0)

上面代码虽然看似满足了我们的需求，但是仔细想一下，又有些不对。到底哪里出问题了呢？🤔

细心的同学很快发现了端倪：这不符合现实场景啊！😱

对了，现实中页面的这些数据并不是写死在代码中的，而是需要动态的发送异步请求从后台接口中读取的。就像下图展示的那样：

![图片描述](https://doc.shiyanlou.com/courses/5428/1723100/cc74b5a36a0e2ee609d29271cfb12530-0)

由上图我们可以知道前后端的交互原理如下：

- 前台接收用户的信息，发送到后台。
- 后台获得信息后进行数据处理，到数据库取一些数据。
- 后台拿到数据库数据返回给前台页面进行显示。

回过头来看我们的代码，并没有与后台交互的行为，而是直接将数据 `dataList` 初始化在了 `data` 中。

如何改进呢？🤔

又有同学说了：这个我会！🙋‍♂️

先把数据存储在 JSON 文件中，然后使用 Ajax 将它读出来就行了。

于是就有了下面的代码。

#### Vue 与 Axios 结合使用

首先，创建 `dataList.json` 文件，将 `demo2.html` 中 `dataList` 的初始值存入其中：

```json
["HTML", "CSS", "JavaScript", "Vue.js", "Axios"]
```

然后，对 `demo2.html` 进行了如下改写：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>syl-vue-test</title>
    <script src="vue.min.js"></script>
    <script src="axios.min.js"></script>
  </head>
  <body>
    <div id="app">
      <ul>
        <li v-for="item in dataList">{{item}}</li>
      </ul>
    </div>
    <script>
      var app = new Vue({
        el: "#app",
        data: {
          dataList: [],
        },
      });
      axios.get("dataList.json").then((res) => {
        console.log(res.data);
        app.dataList = res.data;
      });
    </script>
  </body>
</html>
```

结果一运行，居然成功了～ 😂

不过...这代码怎么感觉很奇怪？🤔

有没有觉得 `axios()` 方法有种“超脱三界之外”的错觉。😏

这样做虽然也实现了我们的需求，但是对于数据请求的方法我们没办法在 Vue 实例中进行管理，代码量多了之后就很难控制了。😓

如何改进呢？🤔

“将 `axios()` 方法的使用封装到 Vue 实例的 `methods` 中，并在适当时机调用！”

热心的同学们又给出主意了。😜

没错，这个思路是对的，我们一起来实现下。

先将使用 `axios()` 方法异步请求数据的步骤封装在 `methods` 中：

```js
methods:{
    getData(){
        axios.get('dataList.json')
        .then(res=>{
                this.dataList = res.data;
        })
    }
}
```

然后再选择适当的时机，让程序自动调用上面封装好的 `getData` 方法。

那么问题来了，那个可以“自动调用 `methods` 中方法”的适当时机在哪？😳

这个时候就有需要钩子函数了～ 😊

但是，这么多钩子函数那个具备呢？

我们回想一下可以发现，从 `created` 开始，我们就可以更新 `data` 中的数据了；`beforeUpdate` 和 `update` 中又不能执行对 `data` 的更新操作（因为会死循环）；`beforeUnmount` 和 `unmounted` 也不太合适（因为组件实例都要销毁了）；这么看来，合适的也只有 `created`、`beforeMount` 和 `mounted` 了。

事实证明这三个函数都可以，不过我们一般会在 `created` 和 `mounted` 中做数据更新的操作，因为这两个函数分别是“实例初始化完成”和“组件挂载完成”的最佳时机。

心急的同学可能会问了：那到底要用哪个呢？🤔

这里我们直接用 `created` 即可，因为这个时候组件还未挂载到 DOM 树上，并不会因为 `data` 中数据的更新而触发组件重新渲染一遍。😊

话不多说，直接上代码：

```js
created(){
    this.getData();
},
```

由于效果与前面的一样，这里就不再重复的贴图了。

以上就是本实验的全部内容，大家掌握住了吗？😄

## 实验总结

本实验先为大家介绍了什么是 Axios，以及它的基本用法。再结合 Vue 组件实例的钩子函数，为大家讲解了如何在 Vue 中，合理使用 Axios 发送异步数据请求，并在适当时机更新页面响应式数据的操作。

今天的学习就到这里，我们下个实验见～ 🙋‍♂️