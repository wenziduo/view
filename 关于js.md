### require 和 import 的区别

> require 对应 module.export。在运行时加载，赋值操作。AMD Common.js  全引
> import 对应 export 或者 export default，是解构过程，编译过程，要放在顶部。es6.要 bable 转义实现。无法在运行时加载模块在语法上，条件加载就不可能实现。可以引入部分变量

### 3 个 ajax 请求链式调用，后一个依赖前一个结果，每个的返回值都是 promise 对象，如何实现

> promise 的 then 方法
> await 和 async

### Localstorage 的容量，超出了咋办

存不进去并报错（QuotaExceededError）

### await 和 async 翻译成 es5 你觉的是啥样的

### 快速排序

任意选取一个数作为关键数据，然后将比它小的都放左边，比它大的都放到右边，这个过程称为一趟快速排序。

### 深拷贝

### Event loop
处理异步得机制
宏任务：不停的询问，ajax，setTimeout，setInterval
微任务 .then
await后面得东西都放在then

### 从 js 切换到 ts 的障碍是什么？

### 跨域除了代理还可以怎么做
同源策略
为什么 产生跨域得原因 产生跨域得情况 解决方案
### let、const、var 的区别，块级作用域是什么？
块级作用域相对于let/const构成一个块级

var: 第一种场景，内层变量可能会覆盖外层变量。

```js
var tmp = new Date();

function f() {
  console.log(tmp);
  if (false) {
    var tmp = "hello world";
  }
}

f(); // undefined
```

第二种场景，用来计数的循环变量泄露为全局变量。

```js
var s = "hello";

for (var i = 0; i < s.length; i++) {
  console.log(s[i]);
}

console.log(i); // 5
```

```js
if（new Boolean(false)）
```
let 命令所声明的变量，只在 let 命令所在的代码块内有效。
不存在变量提升
不允许重复声明
暂时性死区

es5 函数作用域、全局作用域
es6 块级作用域（前提是用es6的let、const定义）


类型
es5： 5+1
es6： 6+1 symbol

typeof class 是function
class是function
js无类，类是面向对象的基础。
原型链


基本类型（5+1，6+1）-》
如何判断（typeof instanceof， 如何判段一个变量是不是数组。
 object.protoTyep.toString.call()）-》
 判断数组：Array.isAray(), instanceof Arrry

万物皆对象：基本类型，用放法时，变包装对象
除了基本类型以外所有变量 instansof（Object）都是true
所有对象都有的方法：tostring和valueof
为什么{}可以用方法：原型上方法


typeof null(Object):bug
typeof Nan(Number):自己不等于自己
null和undefined：函数没有return（自动返回一个undefined）
                变量没有赋值
null:比如dom取一个不存在得元素会得到null

隐式转换：
字符串拼接/四则运算/if


&&：返回值，遇到为假得返回值，全真则返回最后一个
||：
|:取整，二进制位元素


0.1 + 0.2很长很长得二进制，64位，转成二进制再转回10进制

var a = {
  add: (a,b) = > {
    console.log(this)
  }
}
a.add(1,2)


非纯函数：依赖了外部变量
函数声明：匿名函数/函数关键字声明/new Function
函数返回值确定： 调用时输入得参数/定义时的环境（比如外部变量a）
arguments实参，类数组
只要是函数就有的：
属性：name、length（形参的个数）
方法：call、bind、apply（显式this）

箭头函数里没有arguments（可以用...），内部没有this，相当于在外部定义了变量

函数this指向
显示/隐式


array = [
  function(a) {
    console.log(a)
  }
]
array[0]('')

```js
// windowsName
// inner window

```

```js
const o1 = {
  a: 1,
  fn () {
    console.log(this.a)
  }
}

const fn = o1.fn
({ a: 2, fn }).fn()
({ a: 2, fn }).fn.call(({ a: 2, fn }))
// 2
```

```js
const o1 = {
  a: 1,
  fn () {
    setTimeout(function () {
      console.log(this.a)
    }, 0);
  }
}
const fn = o1.fn
({ a: 2, fn }).fn()
({ a: 2, fn }).fn.call({ a: 2, fn })
// undefined
```
```js
const o1 = {
  a: 1,
  fn () {
    console.log(this.a)
    const fn1 = function () {
      console.log(this.a)
    }
    setTimeout(fn1, 0);
  }
}

const fn = o1.fn

({ a: 2, fn }).fn()
({ a: 2, fn }).fn.call({ a: 2, fn })
// 2 undefined
```

```js
obj.fn1.call(obj)
obj.fn.call(obj) //
//
```

```js
function fn () {
  this.a = 2
  console.log(this.a)  // 2  2
  setTimeout(() => {
    console.log(this.a) // 4  4
  }, 0);
  this.a++
  let fn1 = () => {
    this.a++
  }
  let fn2 = function () {
    this.a++
  }
  fn1();
  fn2();// fn2.call(undefined)
}

const obj = {
  a: 1,
  fn,
  fn1 () {
    const A = this.fn
    const t = new A ()
    this.fn()
    console.log(t.a) // 4
    console.log(this.a) // 4
  }
}

obj.fn1() obj.fn1.call(obj)
```
