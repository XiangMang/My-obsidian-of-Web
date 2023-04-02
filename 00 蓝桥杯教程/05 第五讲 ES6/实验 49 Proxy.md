## 实验介绍

欢迎来到本章节～

![图片描述](https://static.shiyanlou.com/lanqiao/frontend/dist/img/kiss.3eb189b.png)

本节实验我们要学习操作对象的 API---Proxy（代理）。

快跟我一起去探索 Proxy 的世界吧！

#### 知识点

- 什么是 Proxy
- Proxy 的实例方法

## 什么是 Proxy

Proxy 可以对目标对象的读取、函数调用等操作进行拦截，然后通过对象的代理对象进行操作。也可以理解为在外界与对象之间建立了一道门，外界要访问该对象必须先打开这道门，如果想要获得打开该门的钥匙，就要遵守一个访问“条约”，允许对来访人员进行改造（**提供一种机制：可以对外界的访问进行过滤和改写**）。

用 Proxy 创建代理需要传入两个参数：目标对象（target）和处理程序（handler）。语法格式如下：

```js
var proxy = new Proxy(target, handler);
```

参数说明如下：

- target：要拦截的目标对象。
- handler：制定拦截行为的对象。

清楚了 Proxy 的概念之后，我们一起来创建一个简单的代理吧～

新建一个 `index.html` 文件。

```js
let target = {};
let proxy = new Proxy(target, {});
proxy.name = "闷墩儿";
console.log(proxy.name);
console.log(target.name);

target.name = "憨憨";
console.log(proxy.name);
console.log(target.name);
```

在控制台输出结果如下所示：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/85e9c3a8180ad52b086ab5bd8d984074-0)

在上面的例子中 `proxy` 的所有操作都转发给了 `target` 对象，当在 `proxy` 上创建了 `name` 属性之后，相应的 `target` 上也会创建 `name` 属性。由于 `target.name` 和 `proxy.name` 都是引用的 `target.name`，所以当修改了 `target.name` 的值后，`proxy.name` 的值也会修改。

## Proxy 的实例方法

Proxy 的代理拦截方法如下表所示：

| 拦截方法                                  | 方法说明                                                     |
| ----------------------------------------- | ------------------------------------------------------------ |
| get(target, propKey, receiver)            | 拦截对象属性的读取。                                         |
| set(target, propKey, value, receiver)     | 拦截对象属性的设置。                                         |
| has(target, propKey)                      | 拦截 propKey in proxy 的操作。                               |
| deleteProperty(target, propKey)           | 拦截 delete proxy[propKey]的操作。                           |
| ownKeys(target)                           | 拦截 Object.getOwnPropertyNames(proxy)、Object.getOwnPropertySymbols(proxy)、Object.keys(proxy)、for...in 循环，返回一个数组。 |
| getOwnPropertyDescriptor(target, propKey) | 拦截 Object.getOwnPropertyDescriptor(proxy, propKey)，返回属性的描述对象。 |
| defineProperty(target, propKey, propDesc) | 拦截 Object.defineProperty(proxy, propKey, propDesc）、Object.defineProperties(proxy, propDescs)，返回一个布尔值。 |
| preventExtensions(target)                 | 拦截 Object.preventExtensions(proxy)，返回一个布尔值。       |
| getPrototypeOf(target)                    | 拦截 Object.getPrototypeOf(proxy)，返回一个对象。            |
| isExtensible(target)                      | 拦截 Object.isExtensible(proxy)，返回一个布尔值。            |
| setPrototypeOf(target, proto)             | 拦截 Object.setPrototypeOf(proxy, proto)，返回一个布尔值。   |
| apply(target, object, args)               | 拦截 Proxy 实例作为函数调用的操作。                          |
| construct(target, args)                   | 拦截 Proxy 实例作为构造函数调用的操作。                      |

如此多的拦截操作方法！在本文中我们就不一一举例了，只给大家介绍最常用的四种拦截方法：

- get(target, propKey, receiver)
- set(target, propKey, value, receiver)
- has(target, propKey)
- ownKeys(target)

下面我们一一来学习吧～

## get(target, propKey, receiver)

在 JavaScript 中，当我们去访问一个对象中不存在的属性时，不会报错，而是返回一个 undefined。如下例所示：

```js
let dog = {};
console.log(dog.name);
```

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/4089d4935cc8e953d9b4c63a833a691a-0)

这样的模式在大型的代码库中可能会导致严重的问题。ES6 中为我们提供了 get 方法，在访问对象之前检验一下是否存在你要访问的属性，该方法接受三个参数，具体说明如下：

- target：被读取属性的目标对象。
- propKey：要读取的属性键值。
- receiver：操作发生的对象。

新建一个 `index1.html` 文件，在文件中写入以下内容：

```js
let dog = {
  name: "闷墩儿",
};
var proxy = new Proxy(dog, {
  get(target, propKey) {
    // 遍历目标对象的属性键值
    if (propKey in target) {
      return target[propKey]; // 返回相应的属性值
    } else {
      throw new ReferenceError(propKey + " 属性不存在");
    }
  },
});
console.log("访问 dog 对象中的 name 属性值为：" + proxy.name);
console.log("访问不存在的 age 属性：" + proxy.age);
```

在控制台可以看见访问 `age` 属性就报错了。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/6992e1b2b45b2f78462d93c6748efab5-0)

## set(target, propKey, value, receiver)

如果要创建一个只接受数字作为属性值的对象，那么在创建属性时，必须判断该值是否是数字，若不是数字应该报错。我们使用 set 方法就可以实现这个需求。

set 方法接受四个参数，具体说明如下：

- target：用于接收属性的目标对象。
- propKey：要写入的属性键值。
- value：要写入的属性值。
- receiver：操作发生的对象。

新建一个 `index2.html` 文件，在文件中写入以下内容：

```js
let validator = {
  set(target, propKey, value) {
    if (propKey === "age") {
      // 判断 age 属性值是否时数字
      if (!Number.isInteger(value)) {
        throw new TypeError("狗狗的年龄只能是整型哦！");
      }
    }
    target[propKey] = value;
    return true;
  },
};

let dog = new Proxy({}, validator);
console.log((dog.age = "22"));
```

从控制台的输出结果可以看出，当 age 属性值设为字符串时，抛出错误。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/d32b77bb49fc40a1e2b8ad4cd8157d26-0)

## has(target, propKey)

在 ES6 之前如果我们要判断某个属性是否在该对象中，可以使用 `in` 来判断。例如：

```js
let dog = {
  name: "闷墩儿",
};
console.log("name" in dog);
console.log("valueOf" in dog);
```

在控制台你会看到两个都输出了 `true`。

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/73d36b12dc209ae951aafa1759c36303-0)

这时候同学们可能有疑问了，明明上面的 `dog` 对象中只有 `name` 属性，为什么 `valueOf` 会被判为 `true` 呢？🤔️

这是因为 valueOf 是一个继承自 object 的[原型属性](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/Object_prototypes)。

而在 has 方法中可以拦截这些操作，返回不一样的值。

has 方法接收两个参数，具体说明如下：

- target：读取属性的目标对象。
- propKey：要检查的属性键值。

新建一个 `index3.html` 文件，在文件中写入以下内容：

```js
let dog = {
  name: "闷墩儿",
  age: 2,
};
let handler = {
  has(target, propKey) {
    if (propKey == "age" && target[propKey] < 5) {
      console.log(`${target.name}的年龄小于 5 岁哦！`);
      return true;
    }
  },
};
let proxy = new Proxy(dog, handler);

console.log("age" in proxy);
```

在控制台可以看到以下输出：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/599d67450e64f10f8181386677fde048-0)

## ownKeys(target)

ownKeys 方法用于拦截对象自身属性的读取操作，具体可以拦截以下四种操作：

- Object.getOwnPropertyNames()
- Object.getOwnPropertySymbols()
- Object.keys()
- for...in

下面我们举一个拦截 for...in 的例子吧～

新建一个 `index4.html` 文件，在文件中写入以下内容：

```js
let dog = {
  name: "闷墩儿",
  age: 2,
  food: "狗罐头",
};
const proxy = new Proxy(dog, {
  ownKeys() {
    return ["name", "color"];
  },
});

for (let key in proxy) {
  console.log(key); // 输出 name
}
```

在控制台的输出如下：

![图片描述](https://doc.shiyanlou.com/courses/10532/1347963/6fcc5c4d254b11e20eeebe3f379fdac7-0)

从上图我们可以看到只输出了 `name` 属性，这是因为在 `dog` 对象中不包含 `color` 属性。

## 实验总结

本节实验给大家介绍了用于对象拦截操作的 Proxy，并给大家介绍了它的拦截方法。在实验最后我们对常用的四种拦截方法进行了练习。这里我们可以来回顾一下这四种方法：

- get(target, propKey, receiver)：拦截对象属性的读取。
- set(target, propKey, value, receiver)：拦截对象属性的设置。
- has(target, propKey)：拦截 propKey in proxy 的操作。
- ownKeys(target)：拦截 Object.getOwnPropertyNames(proxy)、Object.getOwnPropertySymbols(proxy)、Object.keys(proxy)、for...in 循环。