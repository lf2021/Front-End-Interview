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

## react生命周期(><16.3)

- react < 16.3
  (挂载生命周期)
    `constructor(props)`: 初始化props和state
    `componentWillMount()`: Dom被渲染之前触发，在此方法中触发setstate方法，在组件初次渲染之前修改组件的state。如果组件渲染渲染完毕后调用，setstate方法就会启动新的生命周期。
    `render()`: 渲染，只要父组件 render 被调用，其所有子组件的 render 都会被调用
    `componentDidMount()`: 组件渲染完毕后触发，在此阶段中可以获取DOM，调用setState方会触发重新渲染
    `componentWillUnMount()`: 组件被卸载之前触发，可以在这里清除后台的一些进程，清除timer，取消网络请求等
  (更新生命周期)
    当组件的state发生变化或者父组件接收到新的属性的变化，会触发一系列的饿更新生命周期
    `componentWillReceiveProps(nextProps)`: 仅当新的属性被传递给了组件后才会调用。这也是唯一可以调用 setState 方法的地方。
    `shouldComponentUpdate(nextProps, nextState)`:这个生命周期函数是用来提升速度的，它是在重新渲染组件开始前触发的，默认返回 true，可以比较 this.props 和 nextProps ，this.state 和 nextState 值是否变化，来确认返回 true 或者 false。当返回 false 时，组件的更新过程停止，后续的 render、componentDidUpdate 也不会被调用。在进行新旧对比的时候，是浅对比， 也就是说如果比较的数据时引用数据类型，只要数据的引用的地址没变，即使内容变了，也会被判定为true。主要是针对一下两个场景的优化：setState 函数在任何情况下都会导致组件重新渲染吗（会）？如果没有调用 setState，props 值也没有变化，是不是组件就不会重新渲染（父组件重新渲染时，不管传入的 props 有没有变化，都会引起子组件的重新渲染）？
    `componentWillUpdate(nextProps, nextState)`: 组件更新之前触发
    `componentDidUpdate(prevProps, prevState)`: 更新操作发生后，调用render之后触发。

- react >= 16.3
  (挂载生命周期)
  `constructor(props)`
  `getDerivedStateFromProps(props, state)`：static getDerivedStateFromProps(props, state)，这是个静态方法，所以不能在这个函数里使用 this，它应返回一个对象来更新 state，如果返回 null 则不更新任何内容。
  `render()`
  `componentDidMount()`
  `componentWillUnMount()`
  (更新生命周期)
  当组件的 props 改变了，或组件内部调用了 setState/forceUpdate，会触发更新重新渲染。
  `getDerivedStateFromProps(props, state)`
  `shouldComponentUpdate(nextProps, nextState)`
  `render`
  `getSnapshotBeforeUpdate(prevProps, prevState)`:参数表示更新之前的props和state，最近一次渲染输出（提交到 DOM 节点）之前调用，它使得组件能在发生更改之前从 DOM 中捕获一些信息（例如，滚动位置）。此生命周期方法的任何返回值将作为参数传递给 componentDidUpdate()。在最终确定的render执行之前执行，也就是能保证其获取到的元素状态与didUpdate中获取到的元素状态相同。
  `componentDidUpdate()`

getDerivedStateFromProps代码讲解：
 getDerivedStateFromProps接收到新的 props 或者调用了 setState 和 forceUpdate 时被调用。如当接收到新的属性想修改 state ，就可以使用。

  ```json
    // 当 props.counter 变化时，赋值给 state 
  class App extends React.Component {
    constructor(props) {
      super(props)
      this.state = {
        counter: 0
      }
    }
    static getDerivedStateFromProps(props, state) {
      if (props.counter !== state.counter) {
        return {
          counter: props.counter
        }
      }
      return null
    }

    handleClick = () => {
      this.setState({
        counter: this.state.counter + 1
      })
    }
    render() {
      return (
        <div>
          <h1 onClick={this.handleClick}>Hello, world!{this.state.counter}</h1>
        </div>
      )
    }
  }
  ```

但是这里有个问题，如果想要通过点击实现 state.counter 的增加，但这时会发现值不会发生任何变化，一直保持 props 传进来的值。这是由于在 React 16.4^ 的版本中 setState 和 forceUpdate 也会触发这个生命周期，所以当组件内部 state 变化后，就会重新走这个方法，同时会把 state 值赋值为 props 的值。因此需要多加一个字段来记录之前的 props 值，这样就会解决上述问题。

```json
  // 这里只列出需要变化的地方
class App extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      // 增加一个 preCounter 来记录之前的 props 传来的值
      preCounter: 0,
      counter: 0
    }
  }
  static getDerivedStateFromProps(props, state) {
    // 跟 state.preCounter 进行比较
    if (props.counter !== state.preCounter) {
      return {
        counter: props.counter,
        preCounter: props.counter
      }
    }
    return null
  }
  handleClick = () => {
    this.setState({
      counter: this.state.counter + 1
    })
  }
  render() {
    return (
      <div>
        <h1 onClick={this.handleClick}>Hello, world!{this.state.counter}</h1>
      </div>
    )
  }
}
```

getDerivedStateFromProps代码讲解：
最终确定的render执行之前执行，也就是能保证其获取到的元素状态与didUpdate中获取到的元素状态相同

```json
class ScrollingList extends React.Component {
  constructor(props) {
    super(props);
    this.listRef = React.createRef();
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    // 我们是否在 list 中添加新的 items ？
    // 捕获滚动​​位置以便我们稍后调整滚动位置。
    if (prevProps.list.length < this.props.list.length) {
      const list = this.listRef.current;
      return list.scrollHeight - list.scrollTop;
    }
    return null;
  }

  componentDidUpdate(prevProps, prevState, snapshot) {
    // 如果我们 snapshot 有值，说明我们刚刚添加了新的 items，
    // 调整滚动位置使得这些新 items 不会将旧的 items 推出视图。
    //（这里的 snapshot 是 getSnapshotBeforeUpdate 的返回值）
    if (snapshot !== null) {
      const list = this.listRef.current;
      list.scrollTop = list.scrollHeight - snapshot;
    }
  }

  render() {
    return (
      <div ref={this.listRef}>{/* ...contents... */}</div>
    );
  }
}

```

## react中发起网络请求应该在哪个生命周期中进行？为什么？

- 对于异步请求，最好放在componentDidMount中；同步的状态改变，可以放在componentWillMount中，一般用的比较少

## state 和 props 触发更新的生命周期分别？

区别：更新props和state触发的生命周期相同
但是 getDerivedStateFromProps shouldComponentUpdate、getSnapshotBeforeUpdate这几个周期中
如果是更新state，参数prevState会有值，nextProps是一个空对象；
如果是更新props，参数nextProps会有值，prevState是一个空对象。

## 虚拟dom、更新原理

- 为什么需要虚拟dom
  我们知道在前端性能优化中，有一个很重要的一项就是尽可能少的操作 DOM，不仅仅是 DOM 操作相对较慢，更是因为频繁的 DOM 操作会造成浏览器的回流或者重绘，这些都会对我们的性能造成影响。
- 虚拟dom是什么
  虚拟dom是页面中真实的dom元素的js表示形式，每当DOM发生更改时，浏览器都需要重新计算CSS、进行布局并重新绘制web页面，使用VirtualDOM有效地重建DOM。
- 虚拟dom更新原理
  每当有更新发生时，Reconciler（协调器）会做如下工作：
    1.调用函数组件、或class组件的render方法，将返回的JSX转化为虚拟DOM（整个DOM副本保存为虚拟DOM）
    2.将虚拟DOM和上次更新时的虚拟DOM对比
    3.通过对比找出本次更新中变化的虚拟DOM
    4。通知Renderer（渲染器）将变化的虚拟DOM渲染到页面上

## 虚拟DOM是怎么对比的、diff原理

## 什么是jsx、渲染原理

JSX，是一个 JavaScript 的语法扩展，JSX 可以生成 React “元素”，在JSX中，结合了javascript和HTML，并生成了可以在DOM中呈现的react元素。JSX在编译时会被Babel编译为React.createElement方法。

## props和state

（1）props
props是一个从外部传进组件的参数，主要作为就是从父组件向子组件传递数据，它具有可读性和不变性，只能通过外部组件主动传入新的props来重新渲染子组件，否则子组件的props以及展现形式不会改变。
（2）state
state的主要作用是用于组件保存、控制以及修改自己的状态，它只能在constructor中初始化，它算是组件的私有属性，不可通过外部访问和修改，只能通过组件内部的this.setState来修改，修改state属性会导致组件的重新渲染。
（3）区别
props 是传递给组件的（类似于函数的形参），而state 是在组件内被组件自己管理的（类似于在一个函数内声明的变量）。
props 是不可修改的，所有 React 组件都必须像纯函数一样保护它们的 props 不被更改。
state 是在组件中创建的，一般在 constructor中初始化 state。state 是多变的、可以修改，每次setState都异步更新的。

## props为什么是只读的

this.props是组件之间沟通的一个接口，原则上来讲，它只能从父组件流向子组件。React具有浓重的函数式编程的思想。提到函数式编程就要提一个概念：纯函数。它有几个特点：

- 给定相同的输入，总是返回相同的输出。
- 过程没有副作用。
- 不依赖外部状态。
this.props就是汲取了纯函数的思想。props的不可以变性就保证的相同的输入，页面显示的内容是一样的，并且不会产生副作用

## react中怎么检验props？验证props的目的是什么

react为我们提供了PropsTypes以供验证使用，当传入的props传入的数据无效，数据类型不符合时，就会在控制台发出警告信息。避免随着应用越来复杂而出现的问题，并且可以让程序变得易读。
如果项目汇中使用了TypeScript，那么就可以不用PropTypes来校验，而使用TypeScript定义接口来校验props。

```json
import PropTypes from 'prop-types';

class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string
};
```

## react单向数据流是什么

单向数据流是指数据的流向只能由父组件通过props将数据传递给子组件，不能由子组件向父组件传递数据，要想实现数据的双向绑定，只能由子组件接收父组件props传过来的方法去改变父组件的数据，而不是直接将子组件的数据传递给父组件。

## react组件之间的通信

- 父组件向子组件通信
  父级通过props向子组件传递需要的信息

  ```json
  const Child = props => {
    return <p>{props.name}</p>
  }
  const Parent = () => {
    return <Child name='react'></Child>
  }
  ```

- 子组件向父组件通信
  通过props加回调函数的方式

  ```json
  const Child = props => {
    const test = (params) => {
      props.deal(msg)
    }
    return (
    <button onclick={test('你好)}></button>)
  }

  const Parent = () => {
    const deal = (msg) => {
      console.log(msg)
    }
    render(){
      return <Child deal={this.deal.bind(this)}></Child>
    }
  }
  ```

- 跨级组件通信
  
  父组件向子组件的子组件通信，以及向更深层的子组件通信
  （1）props层层传递，但是如果父级的结构较深，那么需要一层曾的去传递，增加了复杂度，并且，这些props并不是中间组件需要的
  （2）context，相当是一个大容器，可以把要通信的内容放在这个容器中，不管嵌套多深，都可使用。对于跨域多层的全局数据可以使用context实现

 ```json
 const BatContext = createContext();
 // 父组件
 class Parent extends Component {
   render() {
     const {color} = this.state
     return (
      <BatContext.Provider value={color}>
        <Child></Child>
      </BatContext.Provide>
     )
   }
 }
 // 子组件
 const Child = () => {
   return (
   <GrandChild />)
 }
// 子组件的子组件
class GrandChild extends Component {
  render(){
    return (
      <BatContext.Consumer>
        {color => <h1 style={{"color": color}}>我是彩色的</h1>}
      </BatContext.Consumer>
    )
  }
 }
 ```

- 非嵌套关系的组件通信
  没有任何包含关系的组件，包括兄弟组件以及不在同一父级中的非兄弟组件
 （1）发布订阅者
 （2）全局状态管理器，dva,redux等
 （3）如果是兄弟组件通信，可以找到两个兄弟节点的共同父级节点，结合父子间通信方式进行通信

## setstate是同步还是异步、setstate之后的流程、setState和replaceState的区别

- 参考链接：<https://zhuanlan.zhihu.com/p/65627731>
（1）同步or异步
如果所有的setstate是同步的, 那么就意味着每执行一次setstate时，都会重新的执行虚拟dom diff更新以及DOM渲染流程，效率极低；
如果是异步，可以把一个同步代码中的多次setstate合并成一次组件的更新。当我们在设置setState后，立即通过this.state是获取最新状态是获取不到的。如果要获取最新的状态可以在setState回调中获取.
所以setState 并不是单纯同步/异步的，它的表现会因调用场景的不同而不同。默认情况下，我们认为他是异步的。
（2）setstate之后的流程
  - 首先，调用了setState 入口函数，根据入参的不同，将其分发到不同的功能函数中去；
  - enqueueSetState 方法将新的 state 放进组件的状态队列里，并调用 enqueueUpdate 来处理将要更新的实例对象；
  
    ```json
    ReactComponent.prototype.setState = function (partialState, callback) {
    this.updater.enqueueSetState(this, partialState);
    if (callback) {
      this.updater.enqueueCallback(this, callback, 'setState');
    }
    };

    
    ```

    ```json
    enqueueSetState: function (publicInstance, partialState) {
    // 根据 this 拿到对应的组件实例
    var internalInstance = getInternalInstanceReadyForUpdate(publicInstance, 'setState');
    // 这个 queue 对应的就是一个组件实例的 state 数组
    var queue = internalInstance._pendingStateQueue || (internalInstance._pendingStateQueue = []);
    queue.push(partialState);
    //  enqueueUpdate 用来处理当前的组件实例
    enqueueUpdate(internalInstance);
    }
    ```

    ```json
    function enqueueUpdate(component) {
      // 注意这一句是问题的关键，isBatchingUpdates标识着当前是否处于批量创建/更新组件的阶段,如果没有处于批量创建/更新组件的阶段，则处理update state事务
      if (!batchingStrategy.isBatchingUpdates) {
        // 若当前没有处于批量创建/更新组件的阶段，则立即更新组件
        batchingStrategy.batchedUpdates(enqueueUpdate, component);
        return;
      }
      // 如果正处于批量创建/更新组件的过程，将当前的组件放在dirtyComponents数组中
      dirtyComponents.push(component);
    }
    ```

  代码中，通过isBatchingUpdates 来判断setState 是先存进 state 队列还是直接更新，如果值为 true 则执行异步操作，为 false 则直接更新。
  当前如果正处于创建/更新组件的过程，就不会立刻去更新组件，而是先把当前的组件放在dirtyComponent里，所以不是每一次的setState都会更新组件。
  这段代码就解释了我们常常听说的：setState是一个异步的过程，它会集齐一批需要更新的组件然后一起更新。

  那么，batchingStrategy是什么呢？

  ```json
  var ReactDefaultBatchingStrategy = {
    // 用于标记当前是否出于批量更新
    isBatchingUpdates: false,
    // 当调用这个方法时，正式开始批量更新
    batchedUpdates: function (callback, a, b, c, d, e) {
      var alreadyBatchingUpdates = ReactDefaultBatchingStrategy.isBatchingUpdates;

      ReactDefaultBatchingStrategy.isBatchingUpdates = true;

      // 如果当前事务正在更新过程在中，则调用callback，既enqueueUpdate
      if (alreadyBatchingUpdates) {
        return callback(a, b, c, d, e);
      } else {
      // 否则执行更新事务
        return transaction.perform(callback, null, a, b, c, d, e);
      }
    }
  };
  ```

  注意两点： 1、如果当前事务正在更新过程中，则使用enqueueUpdate将当前组件放在dirtyComponent里。 2、如果当前不在更新过程的话，则执行更新事务。
（3）setState和replaceState的区别

  ```json
    setState(object nextState[, function callback])
    // 将要设置的新状态（该状态会和当前的state合并）、回调函数（在setstate设置成功，并且组件重新渲染后调用）
    replaceState(object nextState[, function callback])
    // 将要设置的新状态（该状态会替换当前的state）、回调函数（在replaceState设置成功，且组件重新渲染后调用）
  ```
  
 总结：setstate修改其中的部分状态，只是覆盖，不会减少原来的状态；replaceState 是完全替换原来的状态，相当于赋值，将原来的 state 替换为另一个对象，如果新状态属性减少，那么 state 中就没有这个状态了。

## 如何理解hooks、为什么要用hooks

官

## fiber架构的理解

>主流浏览器的刷新频率是60HZ，每（1000ms / 60Hz）16.6ms浏览器刷新一次。
>我们知道，JS可以操作DOM，GUI渲染线程与JS线程是互斥的。所以JS脚本执行和浏览器布局、绘制不能同时执行。
>在每16.6ms时间内，需要完成如下工作：

```txt
JS脚本执行 -----  样式布局 ----- 样式绘制
```

>当JS执行时间过长，超出了16.6ms，这次刷新就没有时间执行样式布局和样式绘制了。从而会导致页面掉帧，导致用户感觉到卡顿。
>如何给用户制造很快的“假象”，解决一个任务长期霸占着资源的问题？
>答案是：通过Fiber 架构，让这个执行过程变成可被中断。“适时”地让出 CPU 执行权。
>具体的：fiber架构的在浏览器每一帧的时间中，预留一些时间给JS线程，React利用这部分时间更新组件（在源码中，预留的初始时间是5ms）。
>当预留的时间不够用时，React将线程控制权交还给浏览器使其有时间渲染UI，React则等待下一帧时间到来继续被中断的工作。

## react性能优化的手段，避免不必要的render

- 避免不必要的render，可以使用shouldComponentUpdate和PureComponent来减少因父组件更新而触发子组件的其中，purecomponent只做浅层的比较。
- React.memo来实现，缓存组件的渲染，避免不必要的更新
- 使用usememo或者usecallback缓存变量或者函数
- 使用suspense(react16.6新增组件)或者lazy进行组件的懒加载，suspense可以在组件请求数据时展示一个pending状态。请求成功后渲染数据。

```json
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
 
function MyComponent() {
  return (
    <div>
      // 组件加载阶段，显示一个loading...
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

## react组件中怎么做事件代理？它的原理是什么？SyntheticEvent层（合成事件层)

```json
https://juejin.cn/post/6844903502729183239
```

```json
<div onClick={this.handleClick.bind(this)}>点我</div>
```

- React并不是将click事件绑定到了div的真实DOM上，而是在document处监听了所有的事件，当事件发生并且冒泡到document处的时候，React将事件内容封装并交由真正的处理函数运行。这样的方式不仅仅减少了内存的消耗，还能在组件挂在销毁时统一订阅和移除事件。

- 除此之外，冒泡到document上的事件也不是原生的浏览器事件，而是由react自己实现的合成事件（SyntheticEvent）。因此如果不想要是事件冒泡的话应该调用event.preventDefault()方法，而不是调用event.stopProppagation()方法。

- 在React底层，主要对合成事件做了：事件委派和自动绑定。
事件委派： React会把所有的事件绑定到结构的最外层，使用统一的事件监听器，这个事件监听器上维持了一个映射来保存所有组件内部事件监听和处理函数。
自动绑定： React组件中，每个方法的上下文都会指向该组件的实例，即自动绑定this为当前组件。

- 为什么要有这个？
  如果DOM上绑定了过多的事件处理函数，整个页面响应以及内存占用可能都会受到影响。React为了避免这类DOM事件滥用，同时屏蔽底层不同浏览器之间的事件系统差异，实现了一个中间层——SyntheticEvent。

## react路由

变的

## 如何解决react层级嵌套过深的问题

- 0

## react框架是mvvm框架还是mvc框架

-吧

## React.Component 和 React.PureComponent 的区别

- pureComponent是纯组件，就是基于浅比较的方式，给每一个组件设置shouldComponentUpdate（如果自己设置了，以自己的为主），在里面把状态和属性都做对比，如果两者基于浅比较都没有发生任何的更改，则不再重新渲染组件
- 浅比较含义，就是只比较第一级，对于基本数据类型，只比较值；对于引用数据类型值，直接比较地址是否相同，不管里面内容变不变，只要地址一样，我们就认为没变。浅比较会忽略属性和或状态突变情况，其实也就是数据引用指针没有变化，而数据发生改变的时候render是不会执行的。如果需要重新渲染时，对于引用类型数据赋值的时候，我们尽可能把之前值拿过来克隆一份，赋给它新的地址就好。
- 优点：当组件更新时，优化React程序，省去虚拟DOM的生成和对比过程，减少render函数执行的次数，从而提高组件的性能。
- 注意：PureComponent不能乱用，只有那些状态和属性不经常的更新的组件我们用来做优化，对于经常更新的，这样处理后反而浪费性能，因为每一次浅比较也是要消耗时间的

## 类组件与函数组件有什么异同？

- 相同点
  组件是react可以复用的最小代码片段，最终返回在页面上渲染的react元素，无论是函数组件，还是类组件，在最终的呈现方式上是完全一致的。
  甚至可以将一个类组件改写成函数组件，或者把函数组件改写成一个类组件；
  从使用者的角度而言，很难从使用体验上区分两者，而且在现代浏览器中，闭包和类的性能只在极端场景下才会有明显的差别。
  
- 不同点
  (1)类组件是基于面向对象编程的，主要有继承、生命周期等概念；函数组件是函数式编程，主打的是没有副作用，引用透明，immutable等特点
  (2)之前，使用场景上，如果存在需要使用生命周期的组件，那么主推类组件；设计模式上，如果需要使用继承，那么主推类组件。
     但现在由于 React Hooks 的推出，生命周期概念的淡出，函数组件可以完全取代类组件。其次继承并不是组件最佳的设计模式，官方更推崇“组合优于继承”的设计概念，所以类组件在这方面的优势也在淡出。
  (3)性能优化上，类组件主要依靠 shouldComponentUpdate 阻断渲染来提升性能，而函数组件依靠 React.memo 缓存渲染结果来提升性能。
  (4)从上手程度而言，类组件更容易上手，从未来趋势上看，由于React Hooks 的推出，函数组件成了社区未来主推的方案。
  (5)从未来发展来看，由于生命周期带来的复杂度，并不易于优化；而函数组件本身轻量简单，更能适应 React 的未来发展。

## 有受控组件和不受控组件的理解
  
## 有状态组件和无状态组件的理解、使用场景

-吧

## React声明组件有哪几种方法，有什么不同？

-h

## react高阶组件、纯组件、和普通组件有什么区别，适用什么场景

```html
<
```
  
## refs、react中可以在render访问refs吗?

- react中refs的作用是什么? 用于访问在 render 方法中创建的 React 元素或 DOM 节点
  
- 使用场景？
  (1) 管理焦点，文本选择或者媒体播放
  (2) 触发强制动画
  (3) 集成第三方 DOM 库
  
- react中可以在render访问refs吗？为什么？
  不可以，render 阶段 DOM 还没有生成，无法获取 DOM

- 怎么用ref
  (1) React.createRef()，创建实例对象，绑定到dom节点（React16的方法）

  ```json
    class Co extends React.Component {
      constructor(props) {
        super(props)
        this.myref = React.creatRef()
      }
      render() {
        return <div ref = {this.myRef}></div>
      }
    }
  ```

  (2)函数回调 Refs：你会传递一个函数。这个函数中接受 React 组件实例或 HTML DOM 元素作为参数，以使它们能在其他地方被存储和访问。

  ```json
    function CustomTextInput(props) {
  // 这里必须声明 textInput，这样 ref 回调才可以引用它
      let textInput = null;
      function handleClick() {
        textInput.focus();
      }
      return (
        <div>
          <input
            type="text"
            ref={(input) => { textInput = input; }} />
          <input
            type="button"
            value="Focus the text input"
            onClick={handleClick}
          />
        </div>
      );  
    }
  ```

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

## react与vue的区别、为什么选择react、优点

相同点

## dispatch
