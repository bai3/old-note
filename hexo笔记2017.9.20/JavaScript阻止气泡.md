---
title: JavaScript阻止气泡
date: 2017-09-08 15:12:59
tags: JavaScript
categories: note

---

# 主要分析一下return false和stopPropagetion的区别
<!-- more -->


## event.stopPropagetion

>抄录 w3 
>
>- 定义和用法
>
>  不在派发事件，终止事件在传播过程的捕获、目标处理或起泡阶段进一步传播，调用该方法后，该节点上处理该事件的处理程序将被调用，事件不再被分派到其他节点。
>
>- 语法
>
>  ```javascript
>  event.stopPropagation()
>  ```
>
>- 说明
>
>  该方法就停止事件的传播，阻止它被分派到其他Document节点。在事件传播的任何阶段都可以调用它的。注意，虽然该方法不能阻止同一个Document节点上的其他事件句柄被调用，但是他可以阻止把事件分派到其他节点。



## return false

先回顾一下事件冒泡知识。

大部分事件都是现在初始DOM触发，然后再通过DOM树往上，在每一级父元素上触发。事件不会再兄弟节点或者子节点上冒泡(当事件向下冒泡时，我们叫事件捕获)。

每次调用return false 的时候，实际上做了三件事件:

- event.preventDefault();
- event.stopPropagation();
- 停止回调函数执行并立即返回。

三件事件中用来阻止浏览器继续执行默认行为只有preventDefault，**除非你想要停止事件冒泡，否则使用return false 会为代码埋下很大隐患。

## 具体比较

- event.stopPropagation()

  这个阻止事件的冒泡方法，不让事件向Document上蔓延，但是默认事件仍然会只想，例如当你调用这个方法的时候，如果点击一个链接，这个链接仍然会被打开。

- event.preventDefault()

  这是阻止默认事件的方法，调用这个方法，链接不会被打开。但是会发生冒泡，冒泡会传递到上一层的父元素。

- return false

  会同时阻止事件冒泡也会阻止默认事件。、

网上的一些例子

```html
<div class = "box1">
  <a href = "www.baidu.com"></a>
</div>	
```

js代码:

```javascript
//不阻止事件冒泡和默认事件
$('.box1').click(function(){
    console.log("1")//不阻止事件冒泡会打印，页面跳转
})
```

```javascript
//阻止冒泡
$('.box a').click(function(event){
  event.stopPropagation();//不会打印1，但是页面会跳转
});
$('.box').click(function(){
    console.log("1");
})
```

```javascript
$('.box a').click(function(event){
//阻止默认事件
  event.preventDefault();//页面不会跳转，但是会打印出1
})；
$('.box').click(function(){
    console.log("1");
})
```

```javascript
$('.box1').click(function(){
    console.log("1")
});
//阻止冒泡
$('.bix1 a').click(function(event){
   	event.stopPropagation();
    //阻止默认事件
  	event.preventDefault();//页面不会跳转，也不会打印出1
  //等同于 return false
})
```



