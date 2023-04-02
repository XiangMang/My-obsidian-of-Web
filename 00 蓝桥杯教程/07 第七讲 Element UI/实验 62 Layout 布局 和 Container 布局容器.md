## 实验介绍

从本节实验开始，我们正式进入了基本组件的学习。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/6523edc8414d683411a8703f26332814-0)

我们从与布局相关的组件开始讲起，通过理论和练习相结合的方式来学习 UI 组件。

点击下一步 👇，快进入实验吧～

#### 知识点

- Container 布局容器
- Layout 布局

## Container 布局容器

当我们在写一个前端项目时，首先应该考虑页面的布局，设计好页面的布局后，才会用 CSS 样式去填充。比如，我们来看看 Element UI 官网组件页面的布局。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/cafc96bd5855d9eaf8281e2a96efe07b-0)

从上图可以看出，官网的布局可以分成四个容器，顶部容器、主要内容区域容器、侧边容器、底栏容器。在 Element UI 的组件库里为我们提供了对应的[布局容器组件](https://element.eleme.io/#/zh-CN/component/container)，方便我们实现页面的基本布局。

- `<el-header>` 是顶部容器。
- `<el-main>` 是主要区域容器。
- `<el-aside>` 是侧边栏容器。
- `<el-footer>` 是底部容器。

除了上述的四个容器组件外，我们还有个外层容器 `<el-container>`，当子元素中包含 `<el-header>` 或 `<el-footer>` 时，全部子元素会垂直上下排列，否则会水平左右排列。

需要注意的是：el-container 的子元素只能是 el-header、el-main、el-aside、el-footer，而这四个容器的父元素也只能是 el-container。

下面我们来看看这些组件是如何使用的。

请同学们根据实验 2 的步骤，创建一个名为 `elementui-container` 的 Vue + Element UI 的项目。

> 本节实验的内容都会在该项目文件中完成。

创建好之后，我们对文件结构进行以下修改~

首先，我们删掉 `elementui-container/src/components` 中的 `HelloWorld.vue` 文件，并把 `App.vue` 文件中不需要的代码删除掉，删除后的文件如下所示：

```html
<!--App.vue-->
<template>
  <div id="app"></div>
</template>

<script>
  export default {
    name: "App",
  };
</script>

<style></style>
```

然后，创建 `elementui-container/src/views/Container.vue` 文件，该文件用来写我们的布局容器相关代码。

最后，我们在 `App.vue` 文件中导入并注册 `Container.vue` 单文件组件，便于查看页面效果。在 `App.vue` 文件添加以下代码：

```html
<!--App.vue-->
<template>
  <div id="app">
    <Container />
  </div>
</template>

<script>
  import Container from "./views/Container.vue";
  export default {
    name: "App",
    components: {
      Container,
    },
  };
</script>

<style></style>
```

准备工作做好了，接下来我们就来学习常见的布局方式吧！

## 常见的布局方式

常见的布局方式有七种，我们通过代码例子带大家过一遍这七种布局方式。

**1. 上下布局**

上下布局就是头部容器+主要区域容器的布局方式，其结构如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/e339455bfd02195d6d094785f1c06939-0)

在 `Container.vue` 文件中的写入以下代码。

```html
<template>
  <div id="app">
    <el-container>
      <el-header>Header</el-header>
      <el-main>Main</el-main>
    </el-container>
  </div>
</template>

<script>
  export default {};
</script>

<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 260px;
  }
  .el-container {
    width: 50%;
  }
</style>
```

使用 `npm run serve` 运行后，打开 **Web 服务**可以看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/0342b0186ca5bc3224d31590d8c05b48-0)

**2. 上中下布局**

上中下布局就是头部容器+主要区域容器+底部容器的布局方式，其结构如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/49026fedd8e803234b08bfca8cee07e4-0)

我们对 `Container.vue` 的代码做如下修改。

```html
<template>
  <div id="app">
    <el-container>
      <el-header>Header</el-header>
      <el-main>Main</el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
  export default {};
</script>

<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 260px;
  }
  .el-footer {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 60px;
  }
  .el-container {
    width: 50%;
  }
</style>
```

我们可以看到如下效果：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/a2bfaff0f8b3cc6f8e24d9ad5f8d6ee8-0)

**3. 左右布局**

左右布局就是侧边容器+主要区域容器的布局方式，其结构如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/9137c2db8321484b6fa3339f6a927a30-0)

我们对 `Container.vue` 文件做如下修改：

```html
<template>
  <div id="app">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-main>Main</el-main>
    </el-container>
  </div>
</template>

<script>
  export default {};
</script>

<style>
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 260px;
  }
  .el-aside {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 200px;
  }
  .el-container {
    width: 50%;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/781cddfac9d15d9eae7261c9c47a01ce-0)

细心的同学可能发现了，上面代码中，我在 `<el-aside>` 标签上写了 `width` 属性来设置该容器的宽度，为什么不直接写在选择器里呢？🤔

尝试把宽度放到选择器中的同学们可能发现了，侧边区域框会有一个宽度，但是这个宽度并非我们设置的值，如果你把 `width` 属性删除，会发现也有一个相同的宽度，这是为什么呢？

这与 `<el-aside>` 组件的源码有关，在源码中给 el-aside 组件设置了默认宽度为 300px，若没有设置宽度或者优先级低于默认值的优先级时，都会是使用 width 属性的默认值。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/0257ec67169745c3e1d981f321a9eddc-0)

所以，同学们请记住，想要改变 `el-aside` 容器的宽度一定要使用行内样式。

**4. 上-下（左右）布局**

上-下（左右）布局，就是顶栏容器为上部分，侧边栏容器和主要区域容器为下部分，其结构如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/f1c0b944426a402c8f6fc5aefa5c2e10-0)

我们对 `Container.vue` 文件做如下修改：

```html
<template>
  <div id="app">
    <el-container>
      <el-header>Header</el-header>
      <el-container>
        <el-aside width="200px">Aside</el-aside>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
  export default {};
</script>

<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  .el-aside {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 200px;
  }
  #app {
    width: 50%;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/c7ed84baf4e7058112d3146abcc54c75-0)

**5. 上-下（左右（上下））布局**

上-下（左右（上下）布局，语言不好描述，我们直接看图吧！

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/9b30dc4262cfff1314619baef654ad5e-0)

我们对 `Container.vue` 文件做如下修改：

```html
<template>
  <div class="container">
    <el-container>
      <el-header>Header</el-header>
      <el-container>
        <el-aside width="200px">Aside</el-aside>
        <el-container>
          <el-main>Main</el-main>
          <el-footer>Footer</el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>
<script>
  export default {
    name: "Container",
  };
</script>
<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  .el-aside {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 200px;
  }
  .el-footer {
    background-color: #1c0c5b;
    color: #fff;
    text-align: center;
    line-height: 60px;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/e8bfa7c98911d2c410c7947ccf00e873-0)

**6. 左右（上下）布局**

左右（上下）布局的结构如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/ff684990f29c4e31c33a3418105c57c1-0)

我们对 `Container.vue` 文件做如下修改：

```html
<template>
  <div class="container">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>
<script>
  export default {
    name: "Container",
  };
</script>
<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  .el-aside {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 200px;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/25ebedf9e0957ae469e017bfb4c740f6-0)

**7. 左-右（上中下）布局**

左-右（上中下）布局结构如下图所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/bf84da86341eb8885720813e8c641c52-0)

我们对 `Container.vue` 文件做如下修改：

```html
<template>
  <el-container>
    <el-aside width="200px">Aside</el-aside>
    <el-container>
      <el-header>Header</el-header>
      <el-main>Main</el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </el-container>
</template>
<script>
  export default {
    name: "Container",
  };
</script>
<style>
  .el-header {
    background-color: #916bbf;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #c996cc;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  .el-aside {
    background-color: #3d2c8d;
    color: #fff;
    text-align: center;
    line-height: 200px;
  }
  .el-footer {
    background-color: #1c0c5b;
    color: #fff;
    text-align: center;
    line-height: 60px;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/f4f32e1a9b2a35da8e41c56fc5618d21-0)

ok，以上就是我们 Container 容器的全部内容，接下来我们学习 Layout 布局。

## Layout 布局

当我们拿到一个 PC 端页面的设计稿时，往往会发现页面的布局有一定的规律：行与行之间会以某种方式对齐。比如，Element UI 官网的 Header 部分，其内部又可划分为如下图所示的几个模块。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/412d6c08cd8e76bb766b4c84d76d2164-0)

对于这样的设计，我们可以使用 Element UI 提供的[栅格布局](https://element.eleme.io/#/zh-CN/component/layout)来实现。

学过 Bootstrap 的同学，对栅格布局应该不会陌生，整个布局包括行和列，Bootstrap 会把屏幕分成 12 列，我们通过 CSS 样式可以设置每一列的占比。

而在 Element UI 中也提供了类似 Bootstrap 的栅格布局，那它是如何实现的呢？快点击下一步 👇，揭晓答案吧！

## 基础布局

首先，新建 `elementui-container/src/views/Layout.vue` 文件，该文件用来写我们的 Layout 布局代码。

然后，我们对 `App.vue` 文件做如下修改：

```html
<template>
  <div id="app">
    <Layout />
  </div>
</template>

<script>
  import Layout from "./views/Layout.vue";
  export default {
    name: "App",
    components: {
      Layout,
    },
  };
</script>

<style></style>
```

准备工作做好了，那我们正式进入 Layout 的学习吧！

Layout 布局把屏幕分成 24 列，也就是说每一行可以分成 24 等份。在 Element UI 中，用 `<el-row>` 组件代表行，用 `<el-col>` 组件代表列，如下图所示。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/af28243e01f194625251da13f261cba4-0)

如果想要设置 `<el-col>` 的占比，使用它的 `:span` 属性来制定所占份数就好了，这样我们就可以自由地组合布局了。

话不多说，我们直接看例子吧！

在 `Layout.vue` 文件中添加以下内容。

```html
<template>
  <div>
    <el-row>
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="7"><div class="grid-content bg3">3</div></el-col>
      <el-col :span="8"><div class="grid-content bg4">4</div></el-col>
    </el-row>
    <el-row>
      <el-col :span="1"><div class="grid-content bg4">1</div></el-col>
      <el-col :span="2"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="3"><div class="grid-content bg3">3</div></el-col>
      <el-col :span="4"><div class="grid-content bg1">4</div></el-col>
      <el-col :span="14"><div class="grid-content bg5">5</div></el-col>
    </el-row>
  </div>
</template>
<script></script>
<style>
  .bg1 {
    background: #e2c2b9;
  }
  .bg2 {
    background: #bfd8b8;
  }
  .bg3 {
    background: #e7eab5;
  }
  .bg4 {
    background: #f1f7e7;
  }
  .bg5 {
    background: #b8dfb8;
  }
  .grid-content {
    min-height: 36px;
    text-align: center;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/208cdff705d2d89ef3254c0c61b40d20-0)

代码说明如下：

- 在第一行 `<el-row>` 组件里，一共分成了四列，第一列 `1` 占 4 份，第二列 `2` 占 5 份，第三列 `3` 占 7 份，第四列 `4` 占 8 份。总宽度为 24 份，每一列指定 `span` 份就是占总宽度的 `span/24`。
- 在第二行 `<el-row>` 组件里，一共分成了五列，第一列 `1` 占 1 份，第二列 `2` 占 2 份，第三列 `3` 占 3 份，第四列 `4` 占 14 份，总宽度为 24 份。

接下来，我们看一看分栏间隔的用法～

## 分栏间隔

对于栅格布局来说，我们可能会有这样一个需要，就是列与列之间有一定的间隔间隙，故在 `<el-row>` 组件里提供了 `gutter` 属性来指定每一列之间的间隔。

> `<el-row>` 与需要设置间隔的列是父子关系。

`gutter` 属性的使用格式如下所示：

```html
<el-row :gutter="像素值"> ... </el-row>
```

我们来举个例子，修改 `Layout.vue` 文件中的代码：

```html
<template>
  <div>
    <el-row :gutter="10">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="7"><div class="grid-content bg3">3</div></el-col>
      <el-col :span="8"><div class="grid-content bg4">4</div></el-col>
    </el-row>
  </div>
</template>
<script></script>
<style>
  .bg1 {
    background: #e2c2b9;
  }
  .bg2 {
    background: #bfd8b8;
  }
  .bg3 {
    background: #e7eab5;
  }
  .bg4 {
    background: #f1f7e7;
  }
  .grid-content {
    min-height: 36px;
    text-align: center;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/7adc97e0cd1a92097e553009fb12aba6-0)

在上面代码中，使用 `<el-row :gutter="10">` 设置列与列之间的间隔为 10 个像素点。

## 分栏偏移

分栏偏移就是我们可以指定某列的偏移，由于作用域是列，所以 Element UI 给 `el-col` 组件提供了 `offset` 属性来设置列的偏移栏数。

`offset` 属性的使用格式如下所示：

```html
<el-col :offset="偏移栏数"></el-col>
```

我们来举个例子，修改 `Layout.vue` 文件中的代码：

```html
<template>
  <div>
    <el-row :gutter="10">
      <el-col :span="4" :offset="7"
        ><div class="grid-content bg1">1</div></el-col
      >
      <el-col :span="5" :offset="8"
        ><div class="grid-content bg2">2</div></el-col
      >
      <el-col :span="7" :offset="2"
        ><div class="grid-content bg3">3</div></el-col
      >
      <el-col :span="8" :offset="5"
        ><div class="grid-content bg4">4</div></el-col
      >
    </el-row>
  </div>
</template>
<script></script>
<style>
  .bg1 {
    background: #e2c2b9;
  }
  .bg2 {
    background: #bfd8b8;
  }
  .bg3 {
    background: #e7eab5;
  }
  .bg4 {
    background: #f1f7e7;
  }
  .grid-content {
    min-height: 36px;
    text-align: center;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/5525b2d9cafe5b49eb419c0f321bf7b0-0)

代码说明如下：

- 第一列 `<el-col :span="4" :offset="7">` 占 4 份，其偏移栏数为 7。
- 第二列 `<el-col :span="5" :offset="8">` 占 5 份，其偏移栏数为 8。
- 第三列 `<el-col :span="7" :offset="2">` 占 7 份，其偏移栏数为 2。
- 第四列 `<el-col :span="8" :offset="5">` 占 8 份，其偏移栏数为 5。

## 对齐方式

当一行分栏的总占比没有达到 24 份的时候，我们可以通过使用 `flex` 布局让分栏灵活对齐。

对于不同的对齐方式，`flex` 布局提供了 `justify` 属性来指定 start、center、end、space-between、space-around 其中的属性值来设置元素的排版方式，具体如下表所示：

| 属性值        | 说明                                                       |
| ------------- | ---------------------------------------------------------- |
| start         | 从起始位置开始排列元素。                                   |
| center        | 居中排列。                                                 |
| end           | 从尾部位置开始排列元素。                                   |
| space-between | 均匀排列每个元素，首个元素放置于起点，末尾元素放置于终点。 |
| space-around  | 均匀排列每个元素，每个元素周围分配相同的空间。             |

由于对齐方式的作用域是行，所以我们给 `<el-row>` 组件添加 `type` 和 `justify` 属性，其使用格式如下所示：

```html
<el-row type="flex" justify="start/center/end..."> ... </el-row>
```

我们来举个例子，修改 `Layout.vue` 文件中的代码：

```html
<template>
  <div>
    <el-row type="flex" justify="start">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="6"><div class="grid-content bg3">3</div></el-col>
    </el-row>
    <el-row type="flex" justify="center">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="6"><div class="grid-content bg3">3</div></el-col>
    </el-row>
    <el-row type="flex" justify="end">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="6"><div class="grid-content bg3">3</div></el-col>
    </el-row>
    <el-row type="flex" justify="space-between">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="6"><div class="grid-content bg3">3</div></el-col>
    </el-row>
    <el-row type="flex" justify="space-around">
      <el-col :span="4"><div class="grid-content bg1">1</div></el-col>
      <el-col :span="5"><div class="grid-content bg2">2</div></el-col>
      <el-col :span="6"><div class="grid-content bg3">3</div></el-col>
    </el-row>
  </div>
</template>
<script></script>
<style>
  .bg1 {
    background: #e2c2b9;
  }
  .bg2 {
    background: #bfd8b8;
  }
  .bg3 {
    background: #e7eab5;
  }
  .bg4 {
    background: #f1f7e7;
  }
  .grid-content {
    min-height: 36px;
    text-align: center;
  }
  .el-row {
    background: #f3f1f5;
    margin-top: 10px;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/650c947ce898caa709d67d38ab03e7c4-0)

## 响应式布局

Element UI 参照了 Bootstrap 的响应式设计，预设了五个响应尺寸：

- `xs`：特小，手机端。
- `sm`：小于浏览器一半的宽度。
- `md`：浏览器一半宽度左右。
- `lg`：接近浏览器全屏宽度。
- `xl`：浏览器全屏宽度。

这五个响应尺寸的默认值为 24，也就是说，任何一个尺寸属性不设置，则该尺寸下的响应式宽度为 24。

响应尺寸属性的使用格式如下所示：

```html
<el-col
  :xs="占比份数"
  :sm="占比份数"
  :md="占比份数"
  :lg="占比份数"
  :xl="占比份数"
></el-col>
```

我们来举个例子，修改 `Layout.vue` 文件中的代码：

```html
<template>
  <div>
    <el-row :gutter="10">
      <el-col :xs="9" :sm="6" :md="4" :lg="3" :xl="2"
        ><div class="grid-content bg1">1</div></el-col
      >
      <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="10"
        ><div class="grid-content bg4">2</div></el-col
      >
      <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11"
        ><div class="grid-content bg2">3</div></el-col
      >
      <el-col :xs="7" :sm="6" :md="4" :lg="3" :xl="1"
        ><div class="grid-content bg3">4</div></el-col
      >
    </el-row>
  </div>
</template>
<script></script>
<style>
  .bg1 {
    background: #e2c2b9;
  }
  .bg2 {
    background: #bfd8b8;
  }
  .bg3 {
    background: #e7eab5;
  }
  .bg4 {
    background: #f1f7e7;
  }
  .grid-content {
    min-height: 36px;
    text-align: center;
  }
  .el-row {
    background: #f3f1f5;
    margin-top: 10px;
  }
</style>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/6546ed9b4838e0f6ac4ef487a2bfc106-0)

在上面代码中，我们可以看出四列里，每一个相应尺寸属性总占比都为 24。

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/ad65697613b3328fe950010afc7e031c-0)

以上就是本节实验的所有内容，同学们学会了吗？😏

## 实验总结

本节实验我们学习了 Layout 布局和 Container 布局容器。

这里我们来总结一下，这两类布局组件的区别～

Layout 布局组件应用于局部布局，而 Container 布局容器应用于整体布局。

ok，布局容器我们就学完了，现在有了一个全局观，我们该去细化每一部分了。