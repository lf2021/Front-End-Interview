# HTML

- [HTML](#html)
  - [HTML5 的新特性](#html5-的新特性)

## HTML5 的新特性

[参考链接](https://www.cnblogs.com/ainyi/p/9777841.html)

1. 语义化标签:header、footer、section、nav、aside、article
2. 增强型表单：input的多个type(color, date, datetime, email, month, number, range, search, tel, time, url, week)
3. 新增表单元素：datalist、keygen、output
4. 新增表单属性：placehoder, required, min和max, step, height 和 width, autofocus, multiple
5. 音频视频：audio、video
6. canvas
7. 地理定位：
8. 拖拽：drag
9. 本地存储：localStorage、sessionStorage
10. 新事件：onresize、ondrag、onscroll、onmousewheel、onerror、onplay、onpause
11. WebSocket

## localStorage，sessionStorage，cookie 的区别

```js
共同点：都是保存在浏览器端。
区别：
(1) cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递
    sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存
(2) 存储大小限制也不同
    cookie数据不能超过4k
    sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大
(3) 数据有效期不同
    sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；
    localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；
    cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭;
(4) 作用域不同
    sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；
    localStorage 在所有同源窗口中都是共享的；
    cookie也是在所有同源窗口中都是共享的
```
