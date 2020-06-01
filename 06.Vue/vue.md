# Vue

- [Vue](#vue)
  - [vue 的优点](#vue-的优点)
  - [vue 的响应式原理](#vue-的响应式原理)
  - [vue 双向数据绑定原理](#vue-双向数据绑定原理)
  - [Object.defineProperty 介绍](#objectdefineproperty-介绍)
  - [v-if 和 v-show 的区别](#v-if-和-v-show-的区别)
  - [为什么 vue 组件中的 data 必须是函数](#为什么-vue-组件中的-data-必须是函数)
  - [vue 的生命周期函数](#vue-的生命周期函数)
  - [vue 的 activated 和 deactivated 钩子函数](#vue-的-activated-和-deactivated-钩子函数)
  - [nextTick 用法](#nexttick-用法)
  - [移动端适配的方法](#移动端适配的方法)
  - [rem 原理](#rem-原理)
  - [rem 和 em 的区别](#rem-和-em-的区别)
  - [移动端 300ms 延迟的原因以及解决方案](#移动端-300ms-延迟的原因以及解决方案)
  - [Vue 和 React 数据驱动的区别](#vue-和-react-数据驱动的区别)

## vue 的优点

- 轻量级框架
- 简单易学
- 双向数据绑定
- 组件化
- 视图，数据，结构分离
- 虚拟 DOM
- 运行速度更快

## vue 的响应式原理

数据发生变化后，会重新对页面渲染，这就是 Vue 响应式
想完成这个过程，我们需要：

侦测数据的变化
收集视图依赖了哪些数据
数据变化时，自动“通知”需要更新的视图部分，并进行更新

对应专业俗语分别是：

数据劫持 / 数据代理
依赖收集
发布订阅模式

## vue 双向数据绑定原理

> vue 通过使用双向数据绑定，来实现了 View 和 Model 的同步更新。vue 的双向数据绑定主要是通过使用数据劫持和发布订阅者模式来实现的。
>
> 首先我们通过 Object.defineProperty() 方法来对 Model 数据各个属性添加访问器属性，以此来实现数据的劫持，因此当 Model 中的数据发生变化的时候，我们可以通过配置的 setter 和 getter 方法来实现对 View 层数据更新的通知。
>
> 数据在 html 模板中一共有两种绑定情况，一种是使用 v-model 来对 value 值进行绑定，一种是作为文本绑定，在对模板引擎进行解析的过程中。
>
> 如果遇到元素节点，并且属性值包含 v-model 的话，我们就从 Model 中去获取 v-model 所对应的属性的值，并赋值给元素的 value 值。然后给这个元素设置一个监听事件，当 View 中元素的数据发生变化的时候触发该事件，通知 Model 中的对应的属性的值进行更新。
>
> 如果遇到了绑定的文本节点，我们使用 Model 中对应的属性的值来替换这个文本。对于文本节点的更新，我们使用了发布订阅者模式，属性作为一个主题，我们为这个节点设置一个订阅者对象，将这个订阅者对象加入这个属性主题的订阅者列表中。当 Model 层数据发生改变的时候，Model 作为发布者向主题发出通知，主题收到通知再向它的所有订阅者推送，订阅者收到通知后更改自己的数据。

## Object.defineProperty 介绍

> Object.defineProperty 函数一共有三个参数，第一个参数是需要定义属性的对象，第二个参数是需要定义的属性，第三个是该属性描述符。
>
> 一个属性的描述符有四个属性，分别是 value 属性的值，writable 属性是否可写，enumerable 属性是否可枚举，configurable 属性是否可配置修改。

## v-if 和 v-show 的区别

- v-if：每次都会重新删除或创建元素来控制 DOM 结点的存在与否

- v-show:是切换了元素的样式 display:none，display: block

因而 v-if 有较高的切换性能消耗，v-show 有较高的初始渲染消耗

## 为什么 vue 组件中的 data 必须是函数

当一个组件被定义，data 必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例。如果 data 仍然是一个纯粹的对象，则所有的实例将共享引用同一个数据对象！通过提供 data 函数，每次创建一个新实例后，我们能够调用 data 函数，从而返回初始数据的一个全新副本数据对象。

简而言之，就是 data 中数据可能会被复用，要保证不同组件调用的时候数据是相同的。

## vue 的生命周期函数

- beforeCreate:
  > 在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用。
- created:
  > 在实例创建完成后被立即调用。在这一步，实例已完成以下的配置：数据观测 (data observer)，property 和方法的运算，watch/event 事件回调。然而，挂载阶段还没开始，\$el property 目前尚不可用。
- beforeMount:
  > 在挂载开始之前被调用：相关的 render 函数首次被调用。
- mounted:
  > 实例被挂载后调用，这时 el 被新创建的 vm.\$el 替换了。如果根实例挂载到了一个文档内的元素上，当 mounted 被调用时 vm.\$el 也在文档内。
- beforeUpdate:
  > 组件更新之前
- updated:
  > 组件更新之后
- beforeDestroy:
  > 组件销毁前调用
- destroyed:
  > 组件销毁后调用
- activated:
  > 被 `keep-alive` 缓存的组件激活时调用。
- deactivated:
  > 被 `keep-alive` 缓存的组件停用时调用。

## vue 的 activated 和 deactivated 钩子函数

```html
<keep-alive>
  <component :is="view"></component>
</keep-alive>
```

`keep-alive`包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。

当组件在 `<keep-alive>` 内被切换，它的 `activated` 和 `deactivated` 这两个生命周期钩子函数将会被对应执行。

- `activated`在`keep-alive`组件激活时调用，该钩子函数在服务器端渲染期间不被调用。
- `deactivated`在`keep-alive`组件停用时调用，该钩子函数在服务端渲染期间不被调用。

## nextTick 用法

官网解释：
> 将回调延迟到下次 DOM 更新循环之后执行。在修改数据之后立即使用它，然后等待 DOM 更新。

```html
<div class="app">
  <div ref="msgDiv">{{msg}}</div>
  <div v-if="msg1">Message got outside $nextTick: {{msg1}}</div>
  <div v-if="msg2">Message got inside $nextTick: {{msg2}}</div>
  <div v-if="msg3">Message got outside $nextTick: {{msg3}}</div>
  <button @click="changeMsg">
    Change the Message
  </button>
</div>
```

```vue
new Vue({
  el: '.app',
  data: {
    msg: 'Hello Vue.',
    msg1: '',
    msg2: '',
    msg3: ''
  },
  methods: {
    changeMsg() {
      this.msg = "Hello world."
      this.msg1 = this.$refs.msgDiv.innerHTML
      this.$nextTick(() => {
        this.msg2 = this.$refs.msgDiv.innerHTML
      })
      this.msg3 = this.$refs.msgDiv.innerHTML
    }
  }
})
```

## 移动端适配的方法

1. flex 弹性布局
2. rem 弹性布局
3. rem + viewport 缩放

> 这也是淘宝使用的方案，根据屏幕宽度设定 rem 值，需要适配的元素都使用 rem 为单位，不需要适配的元素还是使用 px 为单位。（1em = 16px）

## rem 原理

rem 布局的本质是等比缩放

rem 是（根）字体大小相对单位，也就是说跟当前元素的 font-size 没有关系，而是跟整个 body 的 font-size 有关系。

## rem 和 em 的区别

> 一句话概括：em相对于父元素，rem相对于根元素。

- em

  ```css
  子元素字体大小的 em 是相对于父元素字体大小
  元素的width/height/padding/margin用em的话是相对于该元素的font-size
  ```

- rem

  ```js
  rem 是全部的长度都相对于根元素，根元素是谁？<html>元素。
  通常做法是给html元素设置一个字体大小，然后其他元素的长度单位就为rem。
  ```

## 移动端 300ms 延迟的原因以及解决方案

[移动端 300ms 点击延迟和点击穿透](https://juejin.im/post/5b3cc9836fb9a04f9a5cb0e0)

> 移动端点击有 300ms 的延迟是因为移动端会有双击缩放的这个操作，因此浏览器在 click 之后要等待 300ms，看用户有没有下一次点击，来判断这次操作是不是双击。

有三种办法来解决这个问题：

1. 通过 meta 标签禁用网页的缩放。

    ```html
    <meta name="viewport" content="user-scalable=no">
    ```

2. 更改默认的视口宽度

    ```html
    <meta name="viewport" content="width=device-width">
    ```

3. 调用一些 js 库，比如 FastClick

    > FastClick 是 FT Labs 专门为解决移动端浏览器 300 毫秒点击延迟问题所开发的一个轻量级的库。FastClick 的实现原理是在检测到 touchend 事件的时候，会通过 DOM 自定义事件立即出发模拟一个 click 事件，并把浏览器在 300ms 之后的 click 事件阻止掉。

## Vue 和 React 数据驱动的区别

在数据绑定上来说，vue的特色是双向数据绑定，而在react中是单向数据绑定。

vue中实现数据绑定靠的是数据劫持（Object.defineProperty()）+发布-订阅模式

vue中实现双向绑定

```html
<input v-model="msg" />
```

react中实现双向绑定

```html
<input value={this.state.msg} onChange={() => this.handleInputChange()} />
```
