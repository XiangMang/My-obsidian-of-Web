## 实验介绍

Hi，大家好！欢迎来到 jQuery 的世界！

![图片描述](https://doc.shiyanlou.com/courses/3774/1328821/36d1943e5e7707475b0f9d832ded854c-0)

jQuery 是 JavaScript 的一个库，它提供了丰富的 API，简化了我们的代码。

#### 知识点

- jQuery 库的引入
- Hello jQuery

## Hello jQuery

首先请同学们打开右侧的环境。

![图片描述](https://doc.shiyanlou.com/courses/2759/1347963/7311d1373c82994172dda640870c7aa7-0)

然后在左侧项目栏新建一个 `index.html` 文件。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/ed0f8822a17796bcc35890b47cba590c-0)

接着打开 `index.html` 文件，并在右侧的编辑区域，输入一个英文 `!`，然后按下 `tab` 键来生成 HTML 模板。

![图片描述](https://doc.shiyanlou.com/courses/2841/1347963/bda7b4d8149669ae75ef7979d7bacaf8-0)

单单建立一个 HTML 文件我们还不能开始用 jQuery 语法来编写代码，我们需要获取 jQuery 库。

通常情况下，我们需要去 [jQuery 官方网站](https://jquery.com/)下载最新 jQuery 库的版本。在实验中，已经为大家准备好了，同学们使用以下命令即可下载该库到环境中。

```bash
wget https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js
```

获取库之后，我们使用 script 标签在 `index.html` 文件中引入 jQuery 库。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210413-1618295309533)

当然同学们也可以不下载 jQuery 文件，使用链接直接引入，使用方法如下所示：

```html
<script src="https://labfile.oss.aliyuncs.com/courses/3774/jquery-3.6.0.min.js"></script>
```

在往后的学习中，同学们可以选择自己喜欢的方式引入。

准备工作已经做好，那么我们使用 jQuery 语法在页面上输出一句话看看我们引入的 jQuery 库是否有效。

在 `index.html` 文件中，写入以下内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="jquery-3.6.0.min.js"></script>
    <title>Hello jQuery</title>
    <script>
      $(document).ready(function () {
        $("body").html("Hello jQuery!");
      });
    </script>
  </head>
  <body></body>
</html>
```

右击鼠标，选择 Open with Live Server 来开启 8080 端口。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210413-1618295454030)

开启后，点击左侧的 Web 服务。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210413-1618295609603)

页面打开，可看到如下实验效果。

![图片描述](https://doc.shiyanlou.com/courses/uid1347963-20210413-1618295658211)

> 注：这里只是为了让大家体验一下 jQuery，关于代码中的 jQuery 语法，这里不做解释。在后面的内容，我会给大家介绍 jQuery 的语法。

## 实验总结

在本节实验中，讲解了如何引入 jQuery 以及编写了第一个 jQuery 程序，到此为止我们已经正式进入到了 jQuery 的世界了。