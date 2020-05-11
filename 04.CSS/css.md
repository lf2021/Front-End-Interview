[toc]
##  CSS3 新特性
[参考链接](https://www.cnblogs.com/xkweb/p/5862612.html)
1.  伪类和伪元素选择器：
:first-child, :last-child, :nth-child(1), :link, :visited, :hover, :active
::before, ::after, :first-letter, :first-line, ::selection
1.  背景和边框：
background-size, background-origin, border-radius
box-shadow, border-image
3.  文字效果：text-shadow, word-wrap 
4.  2D转换和3D转换：
transform, translate(), rotate(), scale(), skew(), matrix()
rotateX(), rotateY(), perspective
5.  动画、过渡：animation, transition
6.  多列：column-count, column-gap, column-rule
7.  用户界面：resize, box-sizing, outline-offset

## link 和 @import 的区别

1. link 是 HTML 标签，不仅可以加载 CSS 文件，还可以定义 RSS、rel 连接属性等；@import 是 CSS 提供的语法，只有导入样式表的作用。
2. 加载页面时，link 标签引入的 CSS 被同时加载；@import 引入的 CSS 将在页面加载完毕后被加载。
3. @import 是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；link 标签作为 HTML 元素，不存在兼容性问题。
4. 可以通过 JS 操作 DOM ，插入 link 标签来改变样式；由于 DOM 方法是基于文档的，无法使用@import 的方式插入样式。
5. link 引入的样式权重大于@import 引入的样式。

## CSS 选择器的解析规则

从右向左，这样会提高查找选择器所对应的元素的效率

## CSS 选择器优先级

选择器按优先级先后排列：!important>内联>id>class = 属性 = 伪类 >标签 = 伪元素 > 通配符 \*

- important 声明 1,0,0,0
- ID 选择器 0,1,0,0
- 类选择器 0,0,1,0
- 伪类选择器 0,0,1,0
- 属性选择器 0,0,1,0
- 标签选择器 0,0,0,1
- 伪元素选择器 0,0,0,1
- 通配符选择器 0,0,0,0

## CSS 清除浮动的方式

1.  额外标签法
    > 在需要清除浮动的元素后面添加一个空白标签，设置类名 clear，设置`clear: both;`即可
2.  父级元素添加`overflow: hidden;`
3.  伪元素清除浮动
    >     对需要清除浮动的元素添加一个clearfix类名，设置

```css
.clearfix:after {
  /*正常浏览器 清除浮动*/
  content: '';
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;
}
.clearfix {
  *zoom: 1;
  /*zoom 1 就是ie6 清除浮动方式  * ie7以下的版本才能识别 其他浏览器都不执行(略过)*/
}
```

## CSS 垂直居中

1. 定位 + 负边距
2. display: flex 弹性布局

```css
.outer {
  display: flex;
  align-items: center;
  justify-content: center;
}
.inner {
  width: 400px;
  height: 400px;
  background-color: red;
}
```

```html
<div class="outer">
  <div class="inner"></div>
</div>
```

3. display: table
4. 绝对居中

```css
div {
  width: 300px;
  height: 300px;
  background-color: red;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
```
