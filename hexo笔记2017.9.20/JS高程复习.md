---
title: JS高程复习
date: 2017-05-25 19:04:38
tags:
     - JavaScript
     - JavaScript高程
categories: note

---

  &ensp; 之前在学JS基础的时候已经刷过一次，只不过上次很多东西没错，最近忙于暑期实习，所以特意又将这本书再刷一遍，在仔细作一遍笔记，把之前遗落的知识点重新学习一下。主要记一点面试的知识点。

17/5/25

---

<!-- more -->

# 第一章 JavaScript简介

##  JavaScript实现

一个完整的JavaScript实现包括三个不同的部分组成

- 核心(ECMAScript)
- 文档对象模型(DOM)
- 浏览器对象（BOM）

>ECMAScript即是JS的标准，目前已经到ES6。

>DOM简单理解就是HTML内容

# 第二章 在HTML中使用JavaScript

##  <\script>元素

###  标签的位置

> html文件是自上而下的执行方式，但引入的css和javascript的顺序有所不同，css引入执行加载时，程序仍然往下执行，而执行到<\script>脚本是则中断线程，待该script脚本执行结束之后程序才继续往下执行。所以，一般将script放在body之后是因为避免长时间执行script脚本而延迟阻塞。而有一些页面的效果的实现，是需要预先动态的加载一些js脚本，所以这些脚本应该放在<\body>之前。**其次，不能将需要访问dom元素的js放在body之前，因为此时还没有开始生成dom，所以在body之前的访问dom元素的js会出错，或者无效**。就是因为这个，在dom没生成好时我就给它添加了方法，才导致这样

###  延迟脚本

defer只能适用外部脚本文件

defer属性的用于是表明脚本在执行的时候不会影响页面的构造。也就是说，脚本会被延迟到整个页面都解析完毕后在运行。因此在<\script>元素中设置defer属性，想当于告诉浏览器立即下载，但延迟执行。

### 异步脚本

HTML5为<\script>开始设置一个async属性，这个属性与defer属性相似，都用于改变处理脚本的行为。同样只是适用脚本文件。



defer与async的差异

```javascript
<script src="myscript.js"></script>
<script async src="myscript.js"></script>
<script defer src="myscript.js"></script>
```

下面是stackoverflow上的回答，可以参考一下：

1. Without `async` or `defer`, browser will run your script immediately, before rendering the elements that's below your script tag.
2. With `async` (asynchronous), browser will continue to load the HTML page and render it while the browser load and execute the script at the same time.
3. With `defer`, browser will run your script when the page finished parsing. (not necessary finishing downloading all image files. This is good.)
  ![imag1](JS高程复习\imag1.jpg)

**蓝色线代表网络读取，红色线代表执行时间，这俩都是针对脚本的；绿色线代表 HTML 解析。**

高程中解释：

> 使用defer属性可以让脚本在文档中完全呈现之后再执行，**延迟脚本总是按照指定他们的顺序执行**。
>
> 使用async属性可以表示当前脚本不必等待其他脚本，也不必阻塞文档呈现。不能保证异步脚本按照他们在页面中出现的顺序。



# 第三章 基本概念

##  语法
ECMAScript是明确区分大小写的

##  变量

> 虽然省略var操作符可以定义全局变量，但这也不是我们推荐的做法。因为在局部作用域中定义的全局变量很难维护，而且如果有意地省略var操作符，也会由于相应变量不会马上就有定义而导致不必要的混乱。给未经声明的变量赋值在严格模式下回导致抛出ReferenceError错误。

##  数据类型

ES有5种基本数据类型:Undefined、Null、Boolean、Number和String，还有一种复杂数据类型Object。

> 对未初始化的变量执行typeof操作符会返回undefined值，而对未声明的变量执行typeof操作符同样也会返回undefined值。

##  操作符

###  加性操作符

如果两个操作数都是字符串，则将第二个操作数与第一个操作数拼接起来。

如果只有一个操作数是字符串，则将另一个操作数转换成字符串，然后再将两个字符串拼接起来。

###  相等操作符

W3的说明：

| Operator | Description                       |
| -------- | --------------------------------- |
| ==       | equal to                          |
| ===      | equal value andequal type         |
| ！=       | not equal                         |
| ！==      | not equal value or not equal type |

![imag2](JS高程复习\imag2.PNG)