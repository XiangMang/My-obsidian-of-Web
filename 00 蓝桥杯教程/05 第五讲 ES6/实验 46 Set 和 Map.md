## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验会给大家介绍 Set 和 Map 对象。

#### 知识点

- Set 对象
- Map 对象

## Set 对象

[Set](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set) 是 ES6 提供的一种新的数据结构，其结构与数组类似，但与数组不同的是 Set 里面不允许存放相同的元素，也就是说 Set 中的每个值都是独一无二的。

概念清楚了，我们来看看如何创建 Set 对象。

Set 对象有两种创建形式：

- 不带参数的 Set。

```js
let s = new Set();
```

- 带参数的 Set。

```js
let s = new Set(argument1, argument1,...);
```

接下来我们一一举例。

#### 创建不带参数的 Set

新建一个 `index.html` 文件。

首先，创建一个空的 Set 对象。

```js
let s = new Set();
```

然后，我们使用 `add()` 方法往 Set 对象里加入一些元素。

```js
s.add(1);
s.add(2);
s.add(2);
s.add(3);
s.add(3);
console.log(s);
```

在控制台输出，你会发现，重复的元素只保留了一个。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/86b1c3e9b28dc1f889346a2eb4223cb8-0)

其执行过程原理如下动图所示：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/679924e8cc0970aad71a1817e949915e-0)

如果我们想知道 Set 中的元素个数，可以用 `size` 属性。在上面代码中添加：

```js
console.log(s.size);
```

在控制台可以看到如下输出：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/7def8aad0411dc3529511d0b54b93079-0)

#### 创建带参数的 Set

我们再来看看，如何创建带参数的 Set 对象。

有同学做了大胆猜想，这还不简单，把元素写进去用逗号分隔开就可以了，我们来试一试。

新建一个 `index1.html` 文件，在文件中写入以下内容。

```js
let colors = new Set("Green", "Red", "Orange");
console.log(colors);
```

控制台的输出如下所示：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/75f53c1f3cde6c1f9d9dec20f7e8dccd-0)

哈哈 😄，这一次猜错了吧！Set 可不是这样创建元素的。在`（）`里还需要一对 `[]`。

我们修改一下上面的代码。

```js
let colors = new Set(["Green", "Red", "Orange"]);
console.log(colors);
```

再去控制台看一下，发现是我们想要的结果了。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/078923cd61d955ca586c3c365cb54f31-0)

同学们又会想了，我们是不是也可以像数组那样使用索引去访问元素呢？答案是**不可以**。

我们来验证一下～

```js
console.log(colors[1]);
```

可以看到控制台显示的是 undefined。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/c22d7752752bae05be5ff31688bebbfd-0)

关于 Set 中元素的访问，我们会在后面有专门的介绍，请大家稍安勿躁，紧跟我的步伐往深处去探索吧～ 🤩

## Set 相关的方法

我们已经知道了使用 `add()` 方法可以往 Set 中添加元素。我们还可以对 Set 进行删除等操作。

在 Set 中使用 `delete()` 方法来移除指定元素。其使用格式为：

```js
Set.delete(element);
```

需要注意的是，`delete()` 里面的参数是要删除的元素，而不是其索引。

我们举个例子看看具体是怎么用的。

新建一个 `index2.html` 文件，在文件中写入以下内容：

```js
let dogs = new Set(["柯基", "博美", "秋田犬", "藏獒"]);
dogs.delete("秋田犬");
console.log(dogs);
```

在控制台可以看到「秋田犬」不在 Set 中了：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/b15ee448a2bc5363b2070684f58f3b5c-0)

我们还可以使用 `has()` 方法来检查某个元素是否存在于 Set 中。修改代码如下：

```js
let dogs = new Set(["柯基", "博美", "秋田犬", "藏獒"]);
dogs.delete("秋田犬");
console.log(dogs.has("柯基"));
console.log(dogs.has("秋田犬"));
```

在控制台可以看到如下输出：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/c641ef1e7c8a3943c90d0f60bd4a3c12-0)

若我们想删除 Set 中的所有数据，可以使用 `clear()` 方法。

```js
let dogs = new Set(["柯基", "博美", "秋田犬", "藏獒"]);
dogs.clear();
console.log(dogs);
```

在控制台可以看到如下输出：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/36ff55cb5c76a2c8ed6aca717f7d58c6-0)

可以看到 Set 已经空了。

如果我们还想遍历一下 Set 中的元素，该怎么做呢？🤔

来跟着我继续学习吧！

## Set 的遍历

我们使用 [forEach()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set/forEach) 方法可以遍历 Set 中的元素。

其使用格式为：

```js
Set.prototype.forEach(callback[,thisArg])
```

参数说明如下：

- `callback` 是 Set 中每个元素要执行的回调函数。
- `thisArg` 是回调函数执行过程中的 this 值。

话不多说，我们来看一看实际的用法吧！

新建一个 `index3.html` 文件，在该文件中写入以下内容。

```js
let dogs = new Set(["柯基", "博美", "比熊"]);
dogs.forEach(function details(values) {
  console.log(`Hello，我是一只小${values}`);
});
```

在控制台可以看到如下输出：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/634778d0fceae8d9f0938e4dd34c39c2-0)

在上面代码中，我们遍历了 `dogs`，在 `forEach` 方法里，给回调函数命名为 `details`，该回调函数接收一个参数 `values`，就是 Set 对象中的值，我们遍历 Set 中的值并在控制台中输出。

我们还可以改写成下面这个样子～

```js
let dogs = new Set(["柯基", "博美", "比熊"]);
// 回调函数
function details(values) {
  console.log(`Hello，我是一只小${values}`);
}
dogs.forEach(details);
```

## WeakSet

Set 实例和变量在存储数据方面的内存分配和垃圾回收机制是一样的。这么说未免有些抽象不太好理解，接下来我们结合例子去看。

如果 Set 实例中的引用一直存在，垃圾回收就不能释放该对象的存储空间，即使你并没有用到它。例如：

```js
let s = new Set();
let obj1 = {};
let obj2 = {};
s.add(obj1);
s.add(obj2);
console.log(s.size); // 2
obj1 = null;
console.log(s.size); // 2
```

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/e523f4e4fe7dc07e23944d9aafc1d1e1-0)

上面代码中，先声明了一个空的 `Set` 对象 `s`，然后调用 `add` 方法向 `s` 中添加两个空对象元素，控制台打印 `s` 的元素个数为 2，证明 `Set` 对象中给空对象也分配了内存；接着把对象 `obj1` 设为 null，再次打印 `s` 的元素个数，仍然为 2，证明 `Set` 实例 `s` 中元素 1 占用的内存并没有被释放掉。

> 小 tips：同学们知道什么垃圾回收吗？这里简单的说一下。在 JavaScript 中，当你创建了一个值，分配给你相应的内存空间，值不需要了，就释放掉分配的空间，这就是垃圾回收了。

针对这个缺陷，ES6 又给我们提供了另一种 Set，叫做 [WeakSet](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)。

WeakSet 也叫做弱引用 Set，如果将其存储的对象设为了 null，相当于是删除了该对象，当垃圾回收机运行时，会释放掉被删除对象占用的空间。

我们来看看 WeakSet 是怎样使用的。

新建一个 `index4.html` 文件，在文件中写入以下内容：

```js
let s = new WeakSet();
let obj = { msg: "同学们好！" };
s.add(obj);
console.log(s.has(obj));
s.delete(obj);
console.log(s.has(obj));
```

在控制台显示如下：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/99ec98edf3d0849d88092b2fc10eb61f-0)

如果你打印出定义的实例对象，会发现输出为 undefined。

我们针对前面举的 ”Set 中 null 元素占用的内存无法被释放“的小例子做如下修改。

```js
let s = new WeakSet();
let obj1 = {};
let obj2 = {};
s.add(obj1);
s.add(obj2);
console.log(s.size);
obj1 = null;
console.log(s.size);
```

此时的输出都为 undefined 的了。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/c67e4ccc436be234a9858bc070735c74-0)

下面给大家说一说，Set 与 WeakSet 的区别：

- WeakSet 的成员只能是对象且都是弱引用。

  > 在 WeakSet 中，add() 方法中不能传入非对象参数，若传入会报错。

- 在 WeakSet 中，给 has() 和 delete() 方法传入非对象参数，虽然不会报错，但是会返回 false。

- WeakSet 对象没有 size 属性，不能被遍历。

  > 由于 WeakSet 里面存储的都是弱引用，内部有多少个成员，取决于垃圾回收机制有没有运行。运行前后很可能成员个数是不一样的，而垃圾回收机制何时运行是不可预测的，因此 ES6 规定 WeakSet 不可遍历。

## Map 对象

对象，我们不陌生吧！在 ES6 之前，对象是创建键值对数据结构的主要方式，但对象在使用上有一些局限性。

1. 在对象中的键名只能是字符串、数字或者 Symbol。
2. 对象不可以直接使用 forEach 方法遍历。

而 [Map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map) 的出现就解决了上述问题。

Map 是 ES6 中一种存储许多键值对的有序列表，其键值对可以是任意数据类型。Map 是有序的，它会按照键值插入的顺序来排列。

我们先来看看如何来创建 Map 对象。

其语法格式为：

```js
let map = new Map([iterable]);
```

Map 对象可以接收一个由键值对组成的可叠对象。

我们来举个例子～ 👻

打开我们的线上环境，新建一个 `index5.html` 文件，创建一个 Map 类型的变量 `bookstore`。

```js
let bookstore = new Map();
```

#### set 方法添加数据

使用 `set()` 方法可以向对象中添加数据。其使用格式为：

```js
map.set(key:value);
```

在 `index5.html` 文件中增加以下代码：

```js
bookstore.set([1, 2, 3], "书籍");
bookstore.set(false, "日用品");
bookstore.set(3, "化妆品");
console.log(bookstore);
```

- 在 `bookstore.set([1,2,3],"书籍")` 中创建了数组类型的键值 `[1,2,3]`，其值为普通字符串“书籍”。
- 在 `bookstore.set(false,"日用品")` 中创建了布尔类型的键值 `false`，其值为普通字符串“日用品”。
- 在 `bookstore.set(3,"test");` 中创建了整数类型的键值 3，其值为普通的字符串“化妆品”。

在控制台可以看到 Map 对布尔类型和数组类型作为键值也是支持的。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/55b8dea08ee9697c056afd5b7623c404-0)

#### get 方法从集合中获取数据

我们要获取集合中的数据，使用 `get()` 方法即可。

其使用格式为：

```js
map.get(key);
```

我们来获取一下 `bookstore` 集合中的数据吧～

```js
console.log(bookstore.get(false));
```

在控制台可以输出 `false` 键值映射的数据。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/fb17ac7ab54c4d70fcee3f388cd216ad-0)

#### 其他常用方法

除了上方提到的 `set()` 和 `get()` 方法，在 Map 中，还有下面三种方法比较常用。

- `has()` 用来判断指定键名对应的数据是否存在于当前集合中。
- `delete()` 用来删除指定键名的数据。
- `clear()` 用来清空集合中的数据。

我们来举个例子～ 👻

```js
let bookstore = new Map();
bookstore.set("《活着》", "余华");
bookstore.set("《平凡的世界》", "路遥");
bookstore.set("《三体》", "刘欣慈");
bookstore.set("《猫和老鼠》", "电影");
console.log(`《活着》是否存在：${bookstore.has("《活着》")}`);
bookstore.delete("《猫和老鼠》");
console.log(`《猫和老鼠》是否存在：${bookstore.has("《猫和老鼠》")}`);
```

在控制台可以看到如下输出：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/04ec5a9b5135196119987508a018faed-0)

在上面代码中：

- 使用 `bookstore.has("《活着》")` 判断 `bookstore` 对象中是否存在键值为`《活着》` 的数据，很明显是存在的，所以输出为 true。
- 使用 `bookstore.delete("《猫和老鼠》")` 删除了电影 `《猫和老鼠》`，所以使用 `has()` 方法判断它是否存在输出为 false。

接着，我们再使用 `clear()` 方法将上面代码的 `bookstore` 对象的数据清空掉。

```js
bookstore.clear();
console.log(bookstore);
```

从控制台输出的结果，我们看到 `bookstore` 对象成了一个空对象。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/3696acd899f6851ad9a1e91bf3b2825c-0)

## Map 的遍历

与对象不同，Map 可以使用 `forEach()` 方法来遍历数据值。

在讲 `forEach()` 方法之前，先给大家说一说如何在创建 Map 时就为其赋初始值。在前面的例子中，我们都是创建了一个空的 Map，然后使用 `set()` 方法往里面添加的值。现在我们来创建并初始化一个带数据的 Map。

语法格式如下：

```js
let map = new Map([[key1,value1],[key2,value2]...]);
```

我们来举个例子～

新建一个 `index6.html` 文件，在文件中写入以下内容：

```js
let userName = new Map([
  [1, "小红"],
  [2, "小蓝"],
  [3, "小白"],
]);
console.log(userName);
```

在控制台可以看到创建成功了。

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/74d4f9173582adbf962659f1eefc1fca-0)

接下来我们遍历 `userName` 中的值。

此外，Map 还有一个 `forEach()` 方法，与数组的 `forEach()` 方法类似，可以实现对 Map 实例的遍历。

```js
map.forEach(callback(value, key, ownerMap));
```

`callback` 是一个回调函数，其函数包含三个参数：

- value：本次循环所读取的元素的数据。
- key：本次循环所读取的元素的键名。
- ownerMap：Map 集合本身。

我们将上面例子中的 `userName` 使用 `forEach` 遍历如下：

```js
let userName = new Map([
  [1, "小红"],
  [2, "小蓝"],
  [3, "小白"],
]);
userName.forEach(function (value, key, ownerMap) {
  console.log(`userName 中的值有： ${value}`);
  console.log(`userName 中的键有：${key}`);
  console.log(ownerMap);
});
```

控制台显示如下：

![图片描述](https://doc.shiyanlou.com/courses/4378/1347963/3888c59111ba03d13bae6ac3f406e3b1-0)

## 实验总结

本节实验给大家介绍了 Set 对象和 Map 对象相关的知识点。这里我们来总结一下～

Set 对象：

Set 与数组之间的区别：

- Set 是一个可以存储数据的对象，你可以在其中添加或者删除数据，并循环访问 Set。但是 Set 中没有索引，也不能存放重复的值，数组与之相反。

Set 与 WeakSet 的区别：

- Set 是强引用，创建的对象不能被垃圾回收，WeakSet 是弱引用，创建的对象可以被垃圾回收。

Map 对象：

- Map 可以创建任意数据类型的键值对，打破了对象键名类型限制的局限性。
- 我们可以使用 `forEach()` 方法来遍历 Map，而对象不能。
- 我们可以使用 `set()`、`get()`、`has()`、`delete()`、`clear()` 等方法来操作 Map。