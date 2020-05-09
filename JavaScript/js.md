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
