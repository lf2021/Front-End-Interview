##	link 和 @import 的区别
##	CSS 选择器的解析规则
从右向左，这样会提高查找选择器所对应的元素的效率
##	CSS 选择器优先级
选择器按优先级先后排列：!important>内联>id>class = 属性 = 伪类 >标签 = 伪元素 > 通配符 * 
-	important声明 1,0,0,0
-	ID选择器 0,1,0,0
-	类选择器 0,0,1,0
-	伪类选择器 0,0,1,0
-	属性选择器 0,0,1,0
-	标签选择器 0,0,0,1
-	伪元素选择器 0,0,0,1
-	通配符选择器 0,0,0,0
##	CSS 清除浮动的方式
1. 额外标签法
> 在需要清除浮动的元素后面添加一个空白标签，设置类名clear，设置`clear: both;`即可
2. 父级元素添加`overflow: hidden;`
3. 伪元素清除浮动
>	对需要清除浮动的元素添加一个clearfix类名，设置
```css
.clearfix:after {
  /*正常浏览器 清除浮动*/
  content: "";
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

##	CSS 垂直居中
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
