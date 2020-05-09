[toc]

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

## v-if 和 v-show 的区别

- v-if：每次都会重新删除或创建元素来控制 DOM 结点的存在与否

- v-show:是切换了元素的样式 display:none，display: block

因而 v-if 有较高的切换性能消耗，v-show 有较高的初始渲染消耗

## 为什么 vue 组件中的 data 必须是函数？

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

当组件在 <keep-alive> 内被切换，它的 `activated` 和 `deactivated` 这两个生命周期钩子函数将会被对应执行。

- `activated`在`keep-alive`组件激活时调用，该钩子函数在服务器端渲染期间不被调用。
- `deactivated`在`keep-alive`组件停用时调用，该钩子函数在服务端渲染期间不被调用。

## 移动端适配的方法

1.  flex 弹性布局
2.  rem 弹性布局
3.  rem + viewport 缩放

> 这也是淘宝使用的方案，根据屏幕宽度设定 rem 值，需要适配的元素都使用 rem 为单位，不需要适配的元素还是使用 px 为单位。（1em = 16px）

## rem 原理

rem 布局的本质是等比缩放

rem 是（根）字体大小相对单位，也就是说跟当前元素的 font-size 没有关系，而是跟整个 body 的 font-size 有关系。
