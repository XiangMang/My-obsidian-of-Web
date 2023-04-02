## 实验介绍

嗨！欢迎来到 Node.js 的课堂～

![图片描述](https://doc.shiyanlou.com/courses/5788/1347963/97cd015004f8651f5fbec1054486ae88-0)

本节实验我们开始学习 Node.js。

[Node.js](https://nodejs.org/zh-cn/) 是一门服务器编程语言，它也遵循了 ECMAScript 语法规范，在此规范的基础上加入了 Node.js API，包含处理 http 请求、处理文件、socket 编程等。Node.js API 和 ECMAScript 两者结合组成了 Node.js，完成 Server 端的任何操作，为客户端浏览器进行服务。

我们快一起去探索 Node.js 的世界吧～

#### 知识点

- Node.js 的介绍
- 下载和安装 Node.js

## Node.js 的介绍

在实验介绍中说了，Node.js 是一门服务器编程语言。它发布于 2009 年 5 月，由 Ryan Dahl 开发，也是一个基于 Chrome V8 引擎的 JavaScript 运行环境，使用了一个事件驱动、非阻塞式 I/O 模型，让 JavaScript 运行在服务端的开发平台，它让 JavaScript 成为与 PHP、Python、Perl、Ruby 等服务端语言平起平坐的脚本语言。

Node.js 有如下特点和优势：

- 它是一个 JavaScript 运行环境
- 依赖于 Chrome V8 引擎进行代码解析
- 事件驱动（event-driven）
- 非阻塞 I/O(non-blocking I/O)
- 轻量、可伸缩，适于实时数据交互应用
- 单进程，单线程

学到这里有的同学可能有些疑惑，这么多特点都是什么意思呢？Node.js 相对于其他服务器语言，例如 Ruby、Java 又有什么区别和优势呢？别着急，老师马上为大家解答。

传统的服务器开发语言（例如 java）是多线程的，例如我们在淘宝商城购物，如果只有一个顾客发送请求，那显然是没问题的。但是当有成百上千万的用户同时访问的时候，我们肯定不希望别人买完以后才能轮到自己购买，这显然要等待很长时间。但是如果 CPU 只有一个核心的时候或者 CPU 只有一个线程的时候，确实要等待别人购买完毕以后才能购买。这就像在饭馆吃饭，如果只有一个厨师的话，同一时间只能给一个顾客做菜，这样必须要等待这一个厨师为别人做完菜以后才能为自己做菜。

为了解决这个问题，我们可以多增加几个厨师来同时为这些顾客做菜，这就是 java 语言的处理方式：使用多线程并发执行，但是这种方式势必会增加聘请厨师的成本和消耗更大的厨房空间，这无疑是一个资源的浪费，而且这种多线程模型，CPU（厨师） 在为客户服务的时候不能做其他的事，例如使用 I/O 读取文件的时候，只能等待文件系统读取文件完毕以后，才能继续做其他事。

为了解决上述问题 Node.js 应运而生。Node.js 是单线程模型、非阻塞 I/O、采用事件循环机制的原理进行处理。如下图：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/e2c490ca43b43dc1f55b2c6ef47d7429-0)

非阻塞 I/O 的意思就是，文件系统在进行 I/O 操作的时候，Node.js 这个线程还可以做其他的事，当文件系统读取文件完毕时，通过事件的回调函数告诉 Node.js 线程，然后 Node.js 把读取的内容响应给用户。

Node.js 中的 I/O 操作可以理解成生活中的一个幕后工作者，就像在餐馆点餐这个场景中，饭馆可以直接去把点餐的任务派发给外部擅长做菜、煮饭、酿酒的厂家，这些厂家都是非常擅长这些工作的，Node 中也有各种擅长做某件事的模块。这样当这些幕后的厂家完成这些做菜、饭、酒的事件以后，把做完的饭菜酒等食品交给厨师，然后由厨师统一的让服务员把饭菜交给顾客。这样就大大提高了整个餐馆的运营速度。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/8b8028b60e05e3ec467290bbec7477e6-0)

如果大家还不明白的话，我们再看下一个例子，Node.js 就像国王，国王每天都在写任务清单，然后派发给大臣。大臣把任务清单交给下面的官员去做，而这个时候国王还是可以继续写任务清单的。当官员完成任务这个事件后，统一的任务结果交给国王（以事件回调函数的形式通知 Node.js）。此事件反复进行，这便是事件循环。所以说除了国王（Node.js）线程以外，每件事都是并行发生的，这便是 Node.js 单线程和事件循环能同时处理多个请求的原理。

## 在 Window 和 Mac 中下载和安装 Node.js

#### 下载 Node.js

点击 [Node 官网](https://nodejs.org/en/) 进入 `Node` 官方网站，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/7eead8f389dd5f557b66787b934d3112-0)

网站自动识别系统为 `Windows`，默认给出了 `Windows` 的 `Node` 下载地址，如果使用 `Mac` 电脑访问则自动识别系统为 `Mac` 系统，自动给出 Mac 版下载地址。这里给出了两个版本的下载地址：

一.14.17.3 LTS 版（左侧）

即 Long Time Support 版（长时间支持版），即稳定版。

二.16.4.2 Current （右侧）

即最新版，包含最新的特性，但不稳定。

这里推荐下载 LTS 长时间支持版，点击 14.17.3 LTS 进行下载，下载后的文件如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/51fd59895b50127c1d1c38e5c056ff98-0)

另：`Mac` 下载相应 `Mac` 版本即可。

#### 安装

`windows` 和 `Mac` 下都是直接双击安装文件，一路下一步即可。

#### 查看是否安装成功

安装完成后，使用 `cmd` 进入到控制台，输入如下命令测试 `Node` 是否安装成功。

```js
node - v; // 查看 node 版本
npm - v; // 查看 npm 版本
```

如果看到如下版本信息，则表示 `Node` 安装成功。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/6799fd03de731b84a29811405cbdf3fa-0)

> 需要说明的是：本课程是基于 node v14+ 的版本，低于该版本，请自行更新至对应版本中。

安装 `Node` 的时候会同时帮我们安装 `npm (Node Package Manager)` 即 `Node` 包管理工具，用于下载依赖的 `node` 包。

## linux 版 Node 下载和安装

打开我们的实验环境，在右侧控制台中输入如下命令：

```bash
node -v
```

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/3ac19973d1f1395ce65d4b59d6b67084-0)

发现我们并没有安装 `Node` 就已经出现了 `Node` 版本，原因是我们的实验环境中已经默认安装了 `Node 14.15.1` 版。

下面给大家讲解一下 `linux` 下 `Node.js` 的下载和安装。

#### 下载

进入 [Node 官网](https://nodejs.org/en/) 点击下图中的 `Downloads`。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/013f008e90396db2866325a80042fd55-0)

在弹出的界面中显示的 Node 的全部下载版本，这里我们下载 `Linux Binaries（x64` 版。见下图：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/2c08f5b5c33acc5e2ac45e450aea3307-0)

同学们也可以使用下列命令直接下载我们云服务器上的 `Linux Node` 安装文件。

```bash
wget https://labfile.oss.aliyuncs.com/courses/4380/node-v14.17.3-linux-x64.tar.xz
```

使用上述命令下载后效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/b6959211e8ec4997f86874c2b2e92f9b-0)

然后使用如下命令进行解压缩：

```bash
tar -xvf node-v14.17.3-linux-x64.tar.xz
```

解压后效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/ad6c8dbf5f5fa3225379c807ece23571-0)

解压完毕后就可以把 `node-v14.17.3-linux-x64.tar.xz` 文件删除了。

然后使用如下命令对解压后的 node 文件夹进行改名：

```bash
mv node-v14.17.3-linux-x64 node
```

改名后效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/8be5f8e805352196c841324da05073d9-0)

这时再次输入 `node -v` 查看版本，发现版本仍然是 14.15.1。

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/3ac19973d1f1395ce65d4b59d6b67084-0)

说明我们的 `Node` 安装并没有完成，如果想使用最新安装的 14.17.3 版，需要使用以下命令。

```bash
cd node/bin
./node -v
```

注意这里是使用./node 来使用当前路径下的 `node` 命令，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/119fed4b78129dcc47ae5f6afa4cc5a6-0)

发现版本为 14.17.3 ，说明我们已经使用了自己下载的最新版本的 Node，但是每次都需要进入到 `Node` 安装路径的 `bin` 路径下才能使用 `Node` 命令，比较麻烦。如何能让我们在系统的任何地方都能使用最新安装的 `Node` 呢？这里需要修改我们的环境变量 `PATH`， 把 `node/bin` 这个路径添加到 `PATH` 下。

#### 修改环境变量 PATH

为了在全局使用最新安装的 `Node`，我们还需要修改一个配置文件 `~/.zshrc`。

`PATH` 作用：当我们在控制台输入命令的时候（例如 node -v），系统是去 `PATH` 环境变量下配置的路径中寻找这个命令是否存在，查找的路径顺序为从左到右依次查找（linux 路径分隔符为 ：）。如果发现对应的 `PATH` 路径下有 `node` 命令就会使用，否则就会报错。

首先使用下列命令查看我们的环境变量：

```bash
env | grep node
```

效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/1cc445fcd25adf8a6f719c4a4fc261bc-0)

发现 `PATH` 中有 `/usr/sbin/nodejs/bin`，这个路径就是我们实验环境默认安装的 `14.15.1` 的 Node 安装路径，如果想让我们新安装的 Node 优先执行的话，只需要把新版本 Node 的安装路径下的 bin 路径放到 `/usr/sbin/nodejs/bin` 路径前即可。

使用下列命令修改 `~/.zshrc`。

```bash
vim ~/.zshrc
```

使用 `i` 进入插入模式，在文件最后加入如下内容：

```bash
export PATH=/home/project/node/bin:$PATH
```

然后输入 ESC 回到普通模式，输入 `:` 进入命令模式，然后 输入 `wq` 进行保存。修改完成的文件并不会马上生效，需要使用如下命令让刚才配置的环境变量生效。

```bash
source ~/.zshrc
```

最后输入 `node -v` 重新查看 `node` 版本，效果如下：

![图片描述](https://doc.shiyanlou.com/courses/4380/1328821/eb17e5608a9bc9a44ace62ce818473ca-0)

发现现在全局使用的已经是我们最新安装的 `node` 了。

## 实验总结

在本节实验中介绍了什么是 `Node.js`，并讲解了在 `Windows` 和 `Mac` 下如何进行下载和安装，以及在 `linux` 环境中的下载和安装，在今后的课程中同学们不必每次都从新下载 `Node` 并进行配置，直接使用我们环境中默认的 `14.15.1` 版本即可，对于后续课程的学习并没有影响。