[toc]

## js 脚本 defer 和 async 的区别

1. defer 属性表示延迟执行引入的 JavaScript，即这段 JavaScript 加载时 HTML 并未停止解析，这两个过程是并行的。当整个 document 解析完毕后再执行脚本文件，在 DOMContentLoaded 事件触发之前完成。多个脚本按顺序执行。
2. async 属性表示异步执行引入的 JavaScript，与 defer 的区别在于，如果已经加载好，就会开始执行，也就是说它的执行仍然会阻塞文档的解析，只是它的加载过程不会阻塞。多个脚本的执行顺序无法保证。

## JS 跨域怎么做？

<a href="https://segmentfault.com/a/1190000011145364">参考链接</a>

1. JSONP (JSON with Padding)
   通过动态创建 script，再请求一个带参网址实现跨域通信。
2. window.postMessage
   现代浏览器中多窗口通信使用 HTML5 规范的 targetWindow.postMessage(data, origin);其中 data 是需要发送的对象，origin 是目标窗口的 origin。window.addEventListener('message', handler, false);handler 的 event.data 是 postMessage 发送来的数据，event.origin 是发送窗口的 origin，event.source 是发送消息的窗口引用
3. CORS (跨域资源共享)
   普通跨域请求：只服务端设置 Access-Control-Allow-Origin 即可，前端无须设置，若要带 cookie 请求：前后端都需要设置。目前，所有浏览器都支持该功能(IE8+；IE8/9 需要使用 XDomainRequest 对象来支持 CORS）)，CORS 也已经成为主流的跨域解决方案。
4. 服务器代理
   内部服务器代理请求跨域 url，然后返回数据

## JOSNP 有什么优缺点缺点？

缺点：

1. 它只支持 GET 请求而不支持 POST 等其它类型的 HTTP 请求
2. 它只支持跨域 HTTP 请求这种情况，不能解决不同域的两个页面之间如何进行 JavaScript 调用的问题。
3. JSONP 在调用失败的时候不会返回各种 HTTP 状态码。
4. 安全性。假如提供 JSONP 的服务存在页面注入漏洞，即它返回的 JavaScript 的内容被人控制的。那么结果是什么？所有调用这个 JSONP。于是无法把危险控制在一个域名下…所以在使用 JSONP 的时候必须要保证使用的 JSONP 服务必须是安全可信的。

优点：

1. 它不像 XMLHttpRequest 对象实现的 Ajax 请求那样受到同源策略的限制，JSONP 可以跨越同源策略；
2. 它的兼容性更好，在更加古老的浏览器中都可以运行，不需要 XMLHttpRequest 或 ActiveX 的支持
3. 在请求完毕后可以通过调用 callback 的方式回传结果。

## new 运算符的过程

1. 创建一个空对象{}；
2. 构造函数中的 this 指向该空对象
3. 执行构造函数为这个空对象添加属性后返回这个对象

## 数组的 push() 和 pop() 方法的返回值是什么？

- `push()`将一个或多个元素添加到数组的末尾，并返回该数组的新长度
- `pop()`方法从数组中删除最后一个元素，并返回该元素的值

## JS 作用域

ES5 只有全局作用域和函数作用域

- 全局作用域：代码在程序的任何地方都能被访问，window 对象的内置属性都存在全局作用域
- 函数作用域：在固定的代码片段才能被访问

ES6 有块级作用域

## let 和 var 的区别

- let 是块级作用域，var 是函数作用域
- var 存在变量提升，而 let 没有
- 在代码块内，使用 let 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区” (TDZ)

```js
if (true) {
  // TDZ开始
  tmp = 'abc' // ReferenceError
  console.log(tmp) // ReferenceError

  let tmp // TDZ结束
  console.log(tmp) // undefined

  tmp = 123
  console.log(tmp) // 123
}
```

上面代码中，在 let 命令声明变量 tmp 之前，都属于变量 tmp 的“死区”。

## ES6 中箭头函数 VS 普通函数的 this 指向
```
普通函数中 this

1.  总是代表着它的直接调用者，如 obj.fn，fn 里的最外层 this 就是指向 obj
2.  默认情况下，没有直接调用者，this 指向 window
3.  严格模式下（设置了'use strict'），this 为 undefined
4.  当使用 call，apply，bind（ES5 新增）绑定的，this 指向绑定对象
```
```
ES6 箭头函数中 this

1.  默认指向定义它时，所处上下文的对象的 this 指向；
    即 ES6 箭头函数里 this 的指向就是上下文里对象 this 指向，偶尔没有上下文对象，this 就指向 window
2.  即使是 call，apply，bind 等方法也不能改变箭头函数 this 的指向
```
下面使用例子来加深一下印象：

```js
// 例1
function hello() {
  console.log(this) // window
}
hello()

// 例2
function hello() {
  'use strict'
  console.log(this) // undefined
}
hello()

// 例3
const obj = {
  num: 10,
  hello: function () {
    console.log(this) // obj
    setTimeout(function () {
      console.log(this) // window
    })
  },
}
obj.hello()

// 例4
const obj = {
  num: 10,
  hello: function () {
    console.log(this) // obj
    setTimeout(() => {
      console.log(this) // obj
    })
  },
}
obj.hello()

// 例5
/*
diameter是普通函数，里面的this指向直接调用它的对象obj。
perimeter是箭头函数，this应该指向上下文函数this的指向，
这里上下文没有函数对象，就默认为window，而window里面没有radius这个属性，就返回为NaN。
*/
const obj = {
  radius: 10,
  diameter() {
    return this.radius * 2
  },
  perimeter: () => 2 * Math.PI * this.radius,
}
console.log(obj.diameter()) // 20
console.log(obj.perimeter()) // NaN
```

## Ajax 基本流程

> 原生js代码实现与基于promise实现请传送至专栏：[面试高频手撕代码题](./../08.面试高频手撕代码题/面试高频手撕代码题.md)

我对 ajax 的理解是，它是一种异步通信的方法，通过直接由 js 脚本向服务器发起 http 通信，然后根据服务器返回的数据，更新网页的相应部分，而不用刷新整个页面的一种方法。

创建一个 ajax 有这样几个步骤:

- 首先是创建一个 XMLHttpRequest 对象。

- 然后在这个对象上使用 open 方法创建一个 http 请求，open 方法所需要的参数是请求的方法、请求的地址、是否异步和用户的认证信息。

- 在发起请求前，我们可以为这个对象添加一些信息和监听函数。比如说我们可以通过 setRequestHeader 方法来为请求添加头信息。我们还可以为这个对象添加一个状态监听函数。一个 XMLHttpRequest 对象一共有 5 个状态，当它的状态变化时会触发onreadystatechange 事件，我们可以通过设置监听函数，来处理请求成功后的结果。当对象的 readyState 变为 4 的时候，代表服务器返回的数据接收完成，这个时候我们可以通过判断请求的状态，如果状态是 2xx 或者 304 的话则代表返回正常。这个时候我们就可以通过 response 中的数据来对页面进行更新了。

- 当对象的属性和监听函数设置完成后，最后我们调用 sent 方法来向服务器发起请求，可以传入参数作为发送的数据体。

##  Ajax 的 readyState 的几种状态分别代表什么？
|状态值|含义|
|:--:|:--:|
|0 |请求未初始化
|1 |服务器连接已建立
|2 |请求已接收
|3 |请求处理中
|4 |请求已完成，且响应已就绪

## Ajax 禁用浏览器的缓存功能

> 项目中，一般提交请求都会通过 ajax 来提交，我们都知道 ajax 能提高页面载入的速度主要的原因是通过 ajax 减少了重复数据的载入，也就是说在载入数据的同时将数据缓存到内存中，一旦数据被加载其中，只要我们没有刷新页面，这些数据就会一直被缓存在内存中，当我们提交 的 URL 与历史的 URL 一致时，就不需要提交给服务器，也就是不需要从服务器上面去获取数据，虽然这样降低了服务器的负载提高了用户的体验，但是我们不能获取最新的数据。为了保证我们读取的信息都是最新的，我们就需要禁止他的缓存功能。

解决的方法有：
1.  在ajax发送请求前加上 `xhr.setRequestHeader("If-Modified-Since","0")`。 
2.  在ajax发送请求前加上 `xhr.setRequestHeader("Cache-Control","no-cache")`。 
3.  在URL后面加上一个随机数： `"fresh=" + Math.random()`;。 
4.  在URL后面加上时间搓：`"nowtime=" + new Date().getTime()`;。 
5.  如果是使用jQuery，直接这样就可以了`$.ajaxSetup({cache:false})`。这样页面的所有ajax都会执行这条语句就是不需要保存缓存记录。
