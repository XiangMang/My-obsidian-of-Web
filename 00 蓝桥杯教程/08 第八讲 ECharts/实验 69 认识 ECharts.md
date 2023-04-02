## 实验介绍

嗨！欢迎来到 ECharts 的课堂～

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/97cd015004f8651f5fbec1054486ae88-0)

[ECharts](https://echarts.apache.org/) 是一个使用 JavaScript 实现的开源可视化库。它可以在 PC 端和移动设备上运行，目前兼容的浏览器有 IE8/9/10/11，Chrome，Firefox，Safari 等，其底层依赖于矢量图形库 [ZRender](https://github.com/ecomfe/zrender)，为开发者提供了直观，交互丰富，可高度个性化定制的数据可视化图表。

事不宜迟，那我们快快走进实验来认识一下这个新朋友吧！👻

#### 知识点

- 什么是 ECharts
- 获取 ECharts 的方式
- 从 CDN 获取
- ECharts 初体验

## 什么是 ECharts

在没有 ECharts 的年代，对于公司业务的图表需求是用 flash 去实现的，当时的前端工程师并不负责做图表，而是由专门做表的同事来完成，这就造成了大量的沟通成本，因为在数据接口的设计上，前端工程师需要和做图表的同事进行沟通。

基于这样的问题，百度团队在 2012 年 8 月立项，开发一款数据可视化工具，所以 ECharts 的诞生最初是为了满足公司的各种业务报表的需求。

在 2013 年 6 月，ECharts 发布了 1.0 版本随着不断地迭代更新，截止本实验发布（2021 年 12 月）为止，ECharts 的最新版本是 5.2.0。

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/57f3ab026e09e18dbf46ed50e3f96945-0)

ECharts 提供了常规的折线图、柱状图、散点图、饼图等，用于统计的盒形图，用于地理数据可视化的地图、热力图、线图，用于关系数据可视化的关系图、treemap、旭日图，多维数据可视化的平行坐标，还有用于 BI 的漏斗图，仪表盘，并且支持图与图之间的混搭。

除了已经内置的包含了丰富功能的图表，ECharts 还提供了自定义系列，只需要传入一个 `renderItem` 函数，就可以从数据映射到任何你想要的图形，更棒的是这些都还能和已有的交互组件结合使用而不需要操心其它事情。

在官网上还为大家提供了许多不同类型的可视化图表以及炫酷的数据可视化[示例](https://echarts.apache.org/examples/zh/index.html)，如下所示。

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/88c450c1e7d9dcb87955e118db90942f-0)

最有益于大家的地方是它提供了简单的操作、直观的结构、内置的数据源。你能够轻松的找到你想要的图表然后修改它，以此做出一个成品。

比如，下图所示这种一周的收入和支出比例表，不管是修改数据和还是切换主题都非常简单。

![图片描述](https://doc.shiyanlou.com/courses/3121/1226977/68b5b9021fc126b708ed7ed48477fdb3-0)

总之，ECharts 好处多多，主要有以下六种特性：

- 丰富的图表类型。
- 专业的数据分析。
- 健康的开源社区。
- 强劲的渲染引擎。
- 优雅的可视化设计。
- 友好的无障碍访问。

下面我们看看如何获取 ECharts ～

## 获取 ECharts 的方式

我们想要使用 ECharts，毫无疑问，肯定是要先获取它吧～

那么我们去哪里获取呢？学到这个阶段，如果还有同学问这个问题的话，我只能用下面这个表情来回答你。

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/4487b79654c8f2f3aed24b55e152f14e-0)

在官方文档中，为我们提供了四种 [ECharts 安装方式](https://echarts.apache.org/handbook/zh/basics/download/)。

- 从 GitHub 获取
- 从 npm 获取
- 从 CDN 获取
- 在线定制

为了方便大家学习，实验中我们采用 CDN 的方式来教学，所以这里我只给大家介绍 CDN 获取，另外三种，感兴趣的同学们请自行阅读官方文档。

## 从 CDN 获取

首先，我们需要在 https://www.jsdelivr.com/package/npm/echarts 选择 `dist/echarts.js`，点击保存为 `echarts.js` 文件。

为了方便大家学习，我已经下载好了该文件，大家可以通过命令行进行下载。打开线上环境，在终端输入以下命令：

```bash
wget https://labfile.oss.aliyuncs.com/courses/5788/echarts.js
```

然后，新建一个 `index.html` 文件，在文件中引入 `echarts.js`。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="echarts.js"></script>
    <title>ECharts 快速上手</title>
  </head>
  <body></body>
</html>
```

到这里 ECharts 就引入成功了。

那么下面我们基于上面搭建好的环境来体验一下 ECharts 吧！

## ECharts 初体验

现在，我们来绘制一个简单的图表。

绘制之前我们需要定义一个具有宽高的 DOM 容器，在 `index.html` 文件中写入以下内容。

```html
...
<body>
  <!-- 为 ECharts 准备一个宽为 600px，高为 400px 的 DOM -->
  <div id="main" style="width: 600px;height:400px;"></div>
</body>
...
```

然后，通过 [echarts.init](https://echarts.apache.org/zh/api.html#echarts.init) 方法初始化一个 echarts 实例，并通过 [setOption](https://echarts.apache.org/zh/api.html#echartsInstance.setOption) 方法生成一个简单的折线图。

在 `index.html` 文件中写入内容。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="echarts.js"></script>
    <title>ECharts 快速上手</title>
  </head>
  <style>
    * {
      margin: 0;
      padding: 0;
    }
    #main {
      margin: 20px;
      background-color: rgb(228, 255, 192);
    }
  </style>
  <body>
    <!-- 为 ECharts 准备一个宽为 600px，高为 400px 的 DOM -->
    <div id="main" style="width:600px;height:400px;"></div>
  </body>

  <script>
    var chartDom = document.getElementById("main");
    // 初始化实例对象 echarts.init(dom) 容器;
    var myChart = echarts.init(chartDom);
    // 指定配置项和数据
    var option = {
      xAxis: {
        type: "category",
        data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
      },
      yAxis: {
        type: "value",
      },
      series: [
        {
          data: [150, 230, 224, 218, 135, 147, 260],
          type: "line",
        },
      ],
    };
    // 将配置项设置给 echarts 实例对象。
    myChart.setOption(option);
  </script>
</html>
```

在 `index.html` 文件上右击选择 Open with Live Server 打开 8080 端口。

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/9ee35b12b87dd656ca1e59f4ce737e80-0)

打开 Web 服务即可看到如下效果。

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/b741f606f5625281074efdb279ca0767-0)

> 关于代码中的配置项现在不明白没关系，后续课程会为大家讲解，这里只是让同学们体验一下 ECharts。

以上就是本节实验的全部内容～

## 实验总结

本节实验给大家介绍了 ECharts 的几种获取方式，并详细讲解了如何使用 CDN 的方式导入，最后带大家体验了一下绘制折线图。

同学们现在还不清楚上面的代码意思没关系，在课程后续内容中会为大家详细讲解。