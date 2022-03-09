# React

```txt
知识点参考链接

https://www.nowcoder.com/discuss/629644?type=all&order=recall&pos=&page=1&ncTraceId=&channel=-1&source_id=search_all_nctrack&gio_id=6F75134E4ACC8F86EF18014BC2C6C0D9-1646828193985

https://www.nowcoder.com/discuss/854671?type=post&order=recall&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=6F75134E4ACC8F86EF18014BC2C6C0D9-1646828462902
```

```txt
值得借鉴的面经

https://www.nowcoder.com/discuss/123161?type=post&order=jing&pos=&page=2&ncTraceId=&channel=-1&source_id=search_post_nctrack&subType=2&gio_id=6F75134E4ACC8F86EF18014BC2C6C0D9-1646830844478

https://blog.csdn.net/qq_32534855/article/details/**107484533**
```

## 虚拟dom、更新原理

虚拟dom是页面中真实的dom元素的js表示形式，每当DOM发生更改时，浏览器都需要重新计算CSS、进行布局并重新绘制web页面， 使用 Virtual DOM 有效地重建 DOM。
每当有更新发生时，Reconciler（协调器）会做如下工作：

1.调用函数组件、或class组件的render方法，将返回的JSX转化为虚拟DOM（整个DOM副本保存为虚拟DOM）
2.将虚拟DOM和上次更新时的虚拟DOM对比
3.通过对比找出本次更新中变化的虚拟DOM
4。通知Renderer（渲染器）将变化的虚拟DOM渲染到页面上

## 虚拟DOM是怎么对比的、diff原理

99

## 什么是jsx、渲染原理

JSX，是一个 JavaScript 的语法扩展，JSX 可以生成 React “元素”，在JSX中，结合了javascript和HTML，并生成了可以在DOM中呈现的react元素。JSX在编译时会被Babel编译为React.createElement方法。

## props和state

- state顾名思义就是状态，它只是用来控制这个组件本身自己的状态，我们可以用state来完成对行为的控制、数据的更新、界面的渲染，由于组件不能修改传入的props，所以需要记录自身的数据变化。
- props是只读属性，组件不能修改传入的props用于父组件向子组件传递数据和方法
区别：
- State是可变的，是一组用于反映组件UI变化的状态集合，私有的；
而Props对于使用它的组件来说，是只读的，要想修改Props，只能通过该组件的父组件修改。
在组件状态上移的场景中，父组件正是通过子组件的Props, 传递给子组件其所需要的状态

## react 单项数据流是什么

uu

## react组件之间的通信

- 父组件向子组件通信

- 子组件向父组件通信

- 跨级组件通信

- 非嵌套关系的组件通信

## react与vue的区别、为什么选择react、优点

<

## setstate是同步还是异步、setstate之后的流程

77

## React声明组件有哪几种方法，有什么不同？

-h

## react高阶组件、纯组件、和普通组件有什么区别，适用什么场景

```html
<
```

## React.Component 和 React.PureComponent 的区别

g

## 如何理解hooks、为什么要用hooks

官

## fiber架构的理解

一

## react性能优化的手段

t

## react路由

变的

## 如何解决react层级嵌套过深的问题

- 0

## react框架是mvvm框架还是mvc框架

-吧

## react中发起网络请求应该在哪个生命周期中进行？为什么？

>  

## react生命周期(><16.2)

rem

## 类组件与函数组件有什么异同？

- e
  
## 有状态组件和无状态组件的理解、使用场景

-吧
  
## refs、react中可以在render访问refs吗？为什么？

5

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
