[toc]

## vue 的优点

- 轻量级框架
- 简单易学
- 双向数据绑定
- 组件化
- 视图，数据，结构分离
- 虚拟 DOM
- 运行速度更快

## 移动端适配的方法

1.  flex 弹性布局
2.  rem 弹性布局
3.  rem + viewport 缩放
    >     这也是淘宝使用的方案，根据屏幕宽度设定 rem 值，需要适配的元素都使用 rem 为单位，不需要适配的元素还是使用 px 为单位。（1em = 16px）

## rem 原理

rem 布局的本质是等比缩放

rem 是（根）字体大小相对单位，也就是说跟当前元素的 font-size 没有关系，而是跟整个 body 的 font-size 有关系。

## 为什么 vue 组件中的 data 必须是函数？

当一个组件被定义，data 必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例。如果 data 仍然是一个纯粹的对象，则所有的实例将共享引用同一个数据对象！通过提供 data 函数，每次创建一个新实例后，我们能够调用 data 函数，从而返回初始数据的一个全新副本数据对象。

简而言之，就是 data 中数据可能会被复用，要保证不同组件调用的时候数据是相同的。

## vue 的 activated 和 deactivated 钩子函数

```html
<keep-alive>
  <component :is="activeCom"></component>
</keep-alive>
```

`keep-alive`主要用于保留组件状态或避免重新渲染。

用`keep-alive`标签包裹 component 组件标签，将需要缓存的组件缓存在内存当中，下次再次访问的时候，直接从缓存中读取，而不是重新创建或者销毁，提高了性能。

`keep-alive`对应两个生命周期:`activated` `deactivated`

- `activated`在`keep-alive`组件激活时调用，该钩子函数在服务器端渲染期间不被调用。
- `deactivated`在`keep-alive`组件停用时调用，该钩子函数在服务端渲染期间不被调用。
