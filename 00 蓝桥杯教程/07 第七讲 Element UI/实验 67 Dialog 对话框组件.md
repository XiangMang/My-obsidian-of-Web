## 实验介绍

欢迎来到本章节～

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/6523edc8414d683411a8703f26332814-0)

在前面我们已经学习了各种各样的消息提示框了，但那些都只能实现简单的消息提示。如果需要更多定制化的操作，我们还需要学一学 [Dialog 对话框](https://element.eleme.io/#/zh-CN/component/dialog)。

那么我们快点走进实验，去探索一下 Dialog 对话框的神奇之处 😉。

获取本节实验初始项目：

```bash
wget https://labfile.oss.aliyuncs.com/courses/5246/elementui.zip && unzip elementui.zip
```

#### 知识点

- 基本用法
- 自定义内容
- 嵌套的 Dialog
- 居中布局

## 对话框的基本用法

学之前，先来给大家说一说什么是对话框。

对话框就是将某些消息告知给用户，它承载了一些需要用户进行确认的消息。对话框通常在应用程序开启时呈现，来提供一些关键信息，或者要求用户做出一种选择。例如，当你下载了一个新的 App，通常首次打开会有个对话框形式的使用教程，介绍该 App 的界面功能及使用方法，你可以选择跳过或者跟着步骤操作一遍。

Element UI 给我们提供了 `<el-dialog>` 组件来实现对话框，在其中，我们需要设置 `visible` 属性，它接收 `Boolean`，当为 `true` 时显示 Dialog。

我们来看代码例子吧！

新建一个 `src/views/Dialog.vue` 文件，并对 `App.vue` 文件做如下修改。

```html
<template>
  <div id="app">
    <dialog />
  </div>
</template>

<script>
  import Dialog from "./views/Dialog.vue";

  export default {
    name: "App",
    components: {
      Dialog,
    },
  };
</script>

<style></style>
```

在 `Dialog.vue` 文件中写入以下内容。

```html
<template>
  <div>
    <el-button @click="visible = true">快来点击我呀</el-button>
    <el-dialog
      title="猜一猜"
      :visible.sync="visible"
      width="30%"
      :before-close="handleClose"
    >
      <span>欢迎进入字谜游戏。</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="visible = false">取 消</el-button>
        <el-button type="primary" @click="visible = false">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        visible: false,
      };
    },

    methods: {
      handleClose() {
        alert("不能关闭");
      },
    },
  };
</script>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/0af9ac24d24edc3fc46caad0e6881b82-0)

代码说明如下：

- 在上面代码中，我们设置了 `visible` 属性为 false，当点击按钮时被置为 true，显示 Dialog。
- 在 `<el-dialog>` 中，使用 `title` 属性设置了对话框的标题为“猜一猜”。
- `:visible.sync` 中，`:visible` 是属性绑定，表示弹框的隐藏和显示，当 `:visible` 值为 true 时，表示显示弹框，反之为隐藏弹框；`.sync` 是表示同步的修改 `visible` 的值。
- `before-close` 是关闭前的回调函数，会暂停 Dialog 的关闭行为，这里我们的回调函数 `handleClose` 只是弹出一个警告框。

## 自定义内容

除了上面这种包含标题、内容、取消和确定按钮的 Dialog 对话框外，我们还可以自定义对话框的内容，比如在对话框中嵌套一个表单。

我们来看看代码是如何实现的。

对 `Dialog.vue` 文件做如下修改。

```html
<template>
  <div>
    <el-button @click="dialogFormVisible = true">点击我</el-button>
    <el-dialog
      title="个人信息登记"
      :visible.sync="dialogFormVisible"
      width="500px"
    >
      <el-form :model="form">
        <el-form-item label="姓名" :label-width="formLabelWidth">
          <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="电话" :label-width="formLabelWidth">
          <el-input v-model="form.tel" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogFormVisible = false"
          >确 定</el-button
        >
      </div>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        dialogFormVisible: false,
        form: {
          name: "",
          tel: "",
        },
        formLabelWidth: "50px",
      };
    },
  };
</script>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/a79636b792ca2b4f9ee133e097e404a2-0)

从上面的代码可以看出，把表单组件放入 Dialog 组件中，对话框的内容就变成了一个表单。

## 嵌套的 Dialog

在 Dialog 组件中有个 `append-body` 属性，可以实现一个 Dialog 对话框的内部嵌套一个 Dialog 对话框。

其使用格式为：

```html
<el-dialog>
  <el-dialog append-to-body></el-dialog>
</el-dialog>
```

我们来看看具体是如何实现的。

对 `Dialog.vue` 文件做如下修改。

```html
<template>
  <div>
    <el-button @click="outerVisible = true">点击我</el-button>
    <el-dialog title="外层 Dialog" :visible.sync="outerVisible">
      <el-dialog
        width="30%"
        title="内层 Dialog"
        :visible.sync="innerVisible"
        append-to-body
      >
      </el-dialog>
      <div slot="footer" class="dialog-footer">
        <el-button @click="outerVisible = false">取 消</el-button>
        <el-button type="primary" @click="innerVisible = true"
          >打开内层 Dialog</el-button
        >
      </div>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        outerVisible: false,
        innerVisible: false,
      };
    },
  };
</script>
```

显示效果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/c273cce8da222432cce4f31fd919e14a-0)

> 需要同学们注意一下，这里只是告诉大家 `append-to-body` 属性的用法，但实际应用中，不推荐大家使用嵌套的 Dialog。

## 居中布局

在上面我们讲的例子中，Dialog 对话框中的内容都没有居中显示，我们可以使用 `center` 属性让**标题**和**底部按钮**居中显示。

> 注意：若想让内容居中显示，请使用 CSS 样式。

我们来看看代码～

对 `Dialog.vue` 文件做如下修改。

```html
<template>
  <div>
    <el-button type="text" @click="centerDialogVisible = true"
      >点击打开 Dialog</el-button
    >
    <el-dialog
      title="提示"
      :visible.sync="centerDialogVisible"
      width="30%"
      center
    >
      <span class="content">Hello！我是蓝桥云课的小喵喵</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="centerDialogVisible = false" size="small"
          >取 消</el-button
        >
        <el-button
          type="primary"
          @click="centerDialogVisible = false"
          size="small"
          >确 定</el-button
        >
      </span>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        centerDialogVisible: false,
      };
    },
  };
</script>
<style>
  .content {
    color: #a2d2ff;
    margin-left: 20%;
  }
</style>
```

显示效果如下：

![图片描述](https://doc.shiyanlou.com/courses/5246/1347963/75f8c28ca39fdd1c93dfa02a6dcf1946-0)

在上面代码中我们给 `<el-dialog>` 添加了 `center` 属性，使得 Dialog 对话框的标题和底部按钮居中，另外给对话框内容的 `<span>` 标签添加了 `margin` 属性，使其居中显示。

> 需要大家注意的是：`Dialog` 的内容是懒渲染，也就是说在第一次被打开之前，传入的默认 slot 不会被渲染到 DOM 上。因此，若需要执行 DOM 操作，或通过 ref 获取相应组件，请在 open 事件回调中进行。

要使用 open 回调函数，我们需要在 Dialog 组件中绑定 open 事件，例如：

```html
<template>
  <el-dialog @open="open()">
</template>
<script>
  export default {
    methods: {
      open() {

      }
    }
  };
</script>
```

OK，Dialog 组件就为大家介绍到这里。

## 实验总结

本节实验带大家学习了 Dialog 组件的使用，并给大家介绍了 `append-to-body` 和 `center` 属性的作用。实验中只为大家讲了 Dialog 对话框的基础用法，在官方文档中，为大家提供了很多属性，使用方法都是相同的，请学有余力的同学自行扩展吧！