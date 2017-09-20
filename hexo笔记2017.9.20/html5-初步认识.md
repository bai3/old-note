---
title: html5 初步认识
date: 2017-06-03 19:18:14
tags: 
	- HTML5
categories: note
---

# HTML5简介

## 什么是HTML5？

- HTML5是下一代HTML标准
- HTML，HTML4.01的上一个版本诞生于1999年。自从那以后，WEB世界已经经历了巨变、
- HTML5仍处于完善中，然而，大部分现代浏览器已经具备了某些HTML5支持<!--more-->

## HTML5是如何起步的

HTML5的一些有趣的特性:

- 用于绘画的canvas元素
- 用于媒介回访的video和audio元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素,不如article、footer、header、nav、section
- 新的表单控件，比如calendar、date、time、email、url、search

## HTML5 &lt; !DOCTYPE>

&lt;!doctype>声明必须位于HTML5文档中的第一行，使用非常简单

```
<!DOCTYPE html>
```

## HTML5的改进

- 新元素
- 新属性
- 完全支持CSS3
- Video和Audio
- 2D/3D制图
- 本地存储
- 本地SQL数据
- Web应用

## HTML5 多媒体

使用HTML5你可以简单的在网页中播放视频（video）与音频（audio）。

- HTML5 &lt;video>
- HTML5 &lt;audio>

## HTML5 应用

使用HTML5你可以简单地开发应用

- 本地数据存储
- 访问本地文件
- 本地SQL数据
- 缓存引用
- JavaScript工作者
- XHTMLHttpRequest2

## HTML5 使用CSS3

- 新选择器
- 新属性
- 动画
- 2D/3D转换
- 圆角
- 阴影效果
- 可下载的字体

## 语义元素

| 标签              | 描述                        |
| --------------- | ------------------------- |
| &lt;article>    | 定义页面独立的内容区域               |
| &lt;aside>      | 定义页面的侧边栏内容                |
| &lt;bdi>        | 允许你设置一段文本，使其脱离其父元素的文本方法设置 |
| &lt;command>    | 定义命令按钮，比如单选按钮、复选框或按钮      |
| &lt;dialog>     | 定义对话框，比如提示框               |
| &lt;summary>    | 标签包含details元素的标题          |
| &lt;figure>     | 规定独立的流内容（图像、图表、照片、代码等）    |
| &lt;figcaption> | 规定&lt;figure>元素的标题        |
| &lt;footer>     | 规定section或document的页脚     |
| &lt;header>     | 规定了文档的头部区域                |
| &lt;mark>       | 定义带有记号的文本                 |
| &lt;meter>      | 定义度量衡。仅用于已知最大和最小值的度量      |
| &lt;nav>        | 定义导航链接的部分                 |
| &lt;progress>   | 定义任何类型的任务的进度              |
| &lt;ruby>       | 定义ruby注释                  |
| &lt;rt>         | 定义字符的解释或发音                |
| &lt;section>    | 定义文档中的节                   |
| &lt;time>       | 定义日期或时间                   |
| &lt;wbr>        | 规定在文本中的何处适合添加换行符          |

## HTML5表单

新表单元素，新属性，新输入类型，自动验证

## 将HTML5元素定义为块元素

HTML5定义8个新的HTML语义元素。所有这些元素都是块级元素

为了能让旧版本的浏览器正确显示这些元素，你可以设置CSS的display属性值为block

```
header,section,footer,aside,nav,main,article,figure{
  display:block;
}

```

# HTML5新元素

## canvas新元素

标签定义图形，比如图表和其他图像。该标签基于JavaScript的绘图API

## 新多媒体元素

| 标签          | 描述                                      |
| ----------- | --------------------------------------- |
| &lt;audio>  | 定义音频内容                                  |
| &lt;video>  | 定义视频                                    |
| &lt;source> | 定义多媒体资源&lt;video>和&lt;audio>            |
| &lt;embed>  | 定义嵌入的内容，比如插件                            |
| &lt;track>  | 位诸如&lt;video>和&lt;audio>元素之类的媒介规定外部文本轨道 |

## 新表单元素

| 标签            | 描述                                   |
| ------------- | ------------------------------------ |
| &lt;datalist> | 定义选项列表。请与input元素配合使用该元素，来定义input可能的值 |
| &lt;keygen>   | 规定用于表单的密钥对生成器字段                      |
| &lt;output>   | 定义不同类型的输出，比如脚本的输出                    |

## 已经移除的元素

- &lt;acronym>
- &lt;applet>
- &lt;basefont>
- &lt;big>
- &lt;center>
- &lt;dir>
- &lt;font>
- &lt;frame>
- &lt;frameset>
- &lt;noframes>
- &lt;strike>
- &lt;tt>

# HTML5 Canvas

> &lt;canvas>标签定义图形，比如图表和其他图像，你必须使用脚本来绘制图形

## 创建一个画布（Canvas）

简单实例：

```
<canvas id="myCanvas" width="200" height="100"></canvas>

```

**注意：标签通常需要制定一个id属性（脚本中经常）,width和height属性定义的画布的大小**

## 使用JavaScript来绘制图像

canvas元素本身是没有绘图能力的。所有的绘制工作必须在JavaScript内部完成。

实例：

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="#FF0000"；
ctx.fillRect(0,0,150,75);

```

分析

首先，找到&lt;canvas>元素

然后创建context对象

getContext("2d")对象是内建的HTML5对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

设置fillStyle属性可以是CSS颜色，渐变、或图案。fillStyle默认设置是#000000(黑色)

fillRect(x,y,width,height)方法定义了矩形当前的填充方式

## Canvas 坐标

canvas的左上角坐标为（0,0）

上面的fillRect方法拥有参数(0,0,150,75).

意思是：在画布上绘制150×75的矩形，从左上角(0,0)开始。

## Canvas-路径

在Canvas上画直线，可以使用以下两种方法：

- moveTo(x,y)定义线条开始坐标
- lineTo(x,y)定义线条结束坐标

**绘制线条我们必须使用“ink”方法，就像stroke()方法来绘制线条**

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();


```

在canvas绘制圆形

- arc(x,y,r,start,stop)

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();


```

## Canvas-文本

使用canvas绘制文本，重要的属性和方法如下：

- font-定义字体
- fillText(text,x,y)-在canvas上绘制实心的文本
- strokeText(text,x,y)- 在canvas上绘制空心的文本

## Canvas-渐变

渐变可以填充周期矩形，圆形，线条，文本等等，各种形状可以自己定义不同的颜色。

以下有两种不同的方式来设置Canvas渐变： 

- createLinearGradient(x,y,x1,y1)-创建线条渐变
- createRadialGradient(x,y,r,x1,y1,r1)-创建一个径向/圆渐变

当我们使用渐变对象，必须使用两种或两种以上的停止颜色。

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以使0至1

使用渐变，设置fillStyle或strokeStyle的值为渐变，然后绘制形状，如矩形，文本，或一条直线。

```
var c=document.getElementById("myCanvas");
var context=c.getContext("2d");
var grd=context.createLinearGradient(0, 0, 200, 0);
grd.addColorStop(0, 'red');
grd.addColorStop(1, 'blue');
context.fillStyle=grd;
context.fillRect(10,10,150,80);


```

## Canvas-图像

把一幅图像放置到画布上，使用以下方法：

- drawImage（image,x,y)

# HTML5 内联SVG

## 什么是SVG

- SVG指可伸缩矢量图形
- SVG用于定义用于网络的基于矢量的图形
- SVG使用XML格式定义图形
- SVG图像在放大或改变尺寸的情况下其图形质量不会有损失
- SVG是万维网联盟的标准

## SVG的优势

与其他图像格式相比，使用SVG的优势：

- SVG图像可以通过文本编辑器来创建和修改
- SVG图像可被搜索、索引、脚本化或压缩
- SVG是可伸缩的
- SVG图像可在任何的分辨率下被高质量地打印
- SVG可在图像质量不下降的情况下被放大

## SVG与Canvas的区别

- SVG是一种使用XML描述2D图形的语言。
- Canvas通过JavaScript来绘制2D图形
- SVG基于XML，这意味着SVG DOM中的每个元素都是可用的。你可以为某个元素附加JavaScript事件处理器
- 在SVG中每个被绘制的图形均被视为对象。如果SVG对象的属性发火说呢过变化，那么浏览器能够自动重现图形
- Canvas是逐像素进行渲染的。在canvas中，一旦图形被绘制完成，它就不会继续得到浏览器关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或已被图形覆盖的对象

| Canvas                    | SVG                      |
| ------------------------- | ------------------------ |
| 依赖分辨率                     | 不依赖分辨率                   |
| 不支持事件处理器                  | 支持事件处理器                  |
| 弱的文本渲染能力                  | 最适合带有大型渲染区域的应用程序（比如谷歌地图） |
| 能够以.png或。jpg格式保存结果图形      | 复杂度高会减慢渲染速度              |
| 最适合图像密集型的游戏，其中的许多对象会被频繁重绘 | 不适合游戏应用                  |

# HTML5 MathML

HTML5可以再文档中时MathML元素，对应的标签是\<math>

MathML是数学标记语言，是一种基于XML的标准，用来在互联网上书写数学符号和公式的置标语言

**Chrome浏览器不能用，火狐可以**

# HTML5 拖放

拖放(Drag和Drop)是HTML5标准的组成部分

## 拖放

拖放是一种常见的特性，即抓取对象以后拖到另一个位置

在HTML5中，拖放是标准的一部分，任何元素都能够拖放。

实例:

```
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title>
<style type="text/css">
#div1 {width:350px;height:70px;padding:10px;border:1px solid #aaaaaa;}
</style>
<script>
function allowDrop(ev)
{
    ev.preventDefault();
}
 
function drag(ev)
{
    ev.dataTransfer.setData("Text",ev.target.id);
}
 
function drop(ev)
{
    ev.preventDefault();
    var data=ev.dataTransfer.getData("Text");
    ev.target.appendChild(document.getElementById(data));
}
</script>
</head>
<body>
 
<p>拖动 RUNOOB.COM 图片到矩形框中:</p>
 
<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
<br>
<img id="drag1" src="/images/logo.png" draggable="true" ondragstart="drag(event)" width="336" height="69">
 
</body>
</html>

```

解析：

## 设置元素为可拖放

首先，为了使元素可拖动，把draggable属性设置为true：

```
<img draggable="true">

```

## 拖动什么-ondragstart和setDate()

然后，规定元素被拖动时，会发生什么。

在上面例子上，ondragstart属性调用一个函数，drag(event),规定了被拖动的数据。dataTransfer.setDate()方法设置被拖数据的数据类型和值：

```
function drag(ev){
  ev.dataTransfer.setData("Text",ev.target.id);
}

```

这个例子中，数据类型是“Text”,值是可拖动元素的id("drag1")

## 放在何处- ondragover

ondragover事件规定在何处放置被拖动的数据，

默认地，无法将数据/元素放置到其他元素中。如果需要设置允许放置，我们必须阻止对元素的默认处理方式。

这要通过调用ondragover事件的event.preventDefault()方法：

```
event.preventDefault()

```

## 进行放置- ondrop

当放置被拖数据时，会发生drop事件

在上面例子中，ondrop属性调用一个函数，drop(event):

```
function drop(ev){
  ev.preventDefault();
  var data=ev.dataTransfer.getData("Text");
  ev.target.appendChild(document.getElementById(data));
}

```

解释：

- 调用preventDefault()来避免浏览器对数据的默认处理
- 通过dataTransfer.getData("Text")方法获得被拖数据。该方法将返回在setData()方法中设置为相同类型的任何数据。
- 被拖数据是被拖元素的id("drag1")
- 把被拖元素追加到放置元素中

# HTML5 Geolocation(地理定位)

HTML5 Geolocation用于定位用户的位置。

## HTML5-使用地理定位

使用getCurrentPosition()方法来获取用户的位置

实例

```
var x=document.getElementById("demo");
function getLocation(){
  if(navigator.geolocation){
    navigator.geolocation.getCurrentPosition(showPosition);
  }
  else{
    x.innnerHTML="该浏览器不支持获取地理位置"
  }
}
function showPosition(position){
  x.innerHTML="维度："+position.coords.latitude+"<br>经度："+position.coords.longitude;
}


```

- 检测是否支持地理定位
- 如果支持，则运行getCurrentPosition()方法，如果不支持，则向用户显示一段消息。
- 如果getCurrentPosition()运行成功，则向参数showPosition中规定的函数返回一个coordinates对象。
- showPosition()函数获得并显示经度和纬度

上面例子是一个非常基础的地理位置定位脚本，不含有错误处理

## 处理错误和拒绝

getCurrentPosition()方法第二个参数用于处理错误，：

```
function showError(error)
{
  switch(error.code)
    {
      case error.PERMISSION_DENIED：
        x.innerHTML="用户拒绝获取地理位置的请求。"
        break;
      case error.POSITION_UNAVAILABLE:
        x.innerHTML="位置信息不可用的。"
        break;
      case error.TIMEOUT:
        x.innerHTML="请求用户地理位置超时"
        break;
      case error.INKNOWN_ERROR:
        x.innerHTML="未知错误"
        break;
    }
}


```

# HTML5 Video

HTML5 提供了播放音频文件的标准。

## HTML5 Audio - 如何工作

实例：

```
<audio controls>
    <source src="horse.ogg" type="audio/ogg">
    <source src="horse.mp3" type="audio/mpeg">
  你的浏览器不支持audio元素
</audio>


```

control属性供添加播放、暂停和音量控件

在&lt;audio>与&lt;/audio>之间你需要插入浏览器不支持的&lt;audio>元素的提示文本

HTML5 Audio 标签

| 标签          | 描述                                       |
| ----------- | ---------------------------------------- |
| &lt;audio>  | 定义了声音内容                                  |
| &lt;source> | 规定了多媒体资源，可以是多个，在&lt;video>与&lt;audio>之间使用 |

# HTML5 input类型

- color
- date
- datetime
- datetime-local
- email
- month
- number
- range
- search
- tel
- time
- url
- week

# HTML5 表单元素

HTML5新的表单元素

- &lt;datalist>
- &lt;keygen>
- &lt;output>

## HTML5&lt;datelist>元素

&lt;datelist>元素规定输入域的选项列表。

&lt;datelist>属性规定form或input域应该拥有自动完成功能。当用户在自动完成于域中开始输入时，浏览器应该在该域中显示填写的选项：

使用&lt;input>元素的列表属性与&lt;datalist>元素绑定

实例

```
<input list="browsers">
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```

## HTML5&lt;keygen>元素

&lt;keygen>元素的作用是提供一种验证用户的可靠方法。

规定用于表单的密钥对生成器字段

## HTML5&lt;output>元素

&lt;output>元素用于不同类型的输出，比如计算或脚本输出

# HTML5 表单属性

HTML5的&lt;form>和&lt;input>标签添加了几个新属性。

&lt;form>新属性

- autocomplete
- novalidate

&lt;input>新属性

- autocomplete
- autofocus
- form
- formaction
- formenctype
- formmethod
- formnovalidate
- formtarget
- height与width
- list
- min与max
- multiple
- pattern（regexp）
- placeholder
- required
- step

## form/input autocomplete属性

autocomplete属性规定form或input域应该拥有自动完成功能。

当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项。

**autocomplete适用于&lt;form>标签，以及以下类型的&lt;input>标签：text，search，url，telephone，email。passsword，datepickers，range以及color**

## novalidate属性

novalidate属性石一个boolean属性

novalidate属性规定在提交表单时不应该验证form或input域

## autofocus属性

autofocus属性是一个boolean属性。

autofocus属性规定在页面加载时，域自动地获得焦点

实例：

```
First name:<input type="text" name="fname" autofocus>
```

## form属性

form属性规定输入域所属的一个或多个表单

## formaction属性

The formaction属性用于描述表单提交的URL地址

The formaction属性会覆盖\<form>元素中的action属性

## formenctype属性

formenctype属性描述了表单提交到服务器的数据编码(只对form表单中method=“post”表单)

## formmethod属性

formmethod属性定义了表单提交的方式

formmethod属性覆盖&lt;form>元素的method属性

**该属性可以与type=“submit”和type=“image”配合**

## formnovalidate属性

novalidate属性石一个boolean属性

novalidate属性描述了&lt;input>元素在表单提交时无需被验证。

formnovalidate属性会覆盖&lt;form>元素的novalidate属性

**注意：formnovalidate属性与type=“submit”一起使用**

## formtarget属性

formtarget属性指定一个名称或一个关键字来指明表单提交数据接收后的展示。

formtarget属性会覆盖&lt;form>元素的target属性



## height和width属性

height和width属性规定用于image类型的&lt;input>标签的图像高度和宽度



## list属性

list属性规定输入域的datalist。datalist是输入域的选项列表



## min和max属性

min、max和step属性用于包含数字或日期的input类型规定限定

## pattern属性

pattern属性描述了一个正则表达式用于验证<&lt;input>元素的值

placeholder属性

placeholder属性提供了一宗提示，描述输入域所期待的值

## required属性

required属性是一个boolean属性

required属性规定必须在提交之前填写输入域（不能为空）

## step属性

step属性为输入域规定合法的数字间隔。



# HTML5的语义元素

什么是语义元素？

一个语义元素能够清楚的描述其意义给浏览器和开发者。

- section元素

  section标签定义文档中的节。比如章节、页眉、页脚或文档中其他部分

- article元素

  article标签定义独立的内容

- nav元素

  nav标签定义导航链接的部分

- aside元素

  aside标签定义页面主区域之外的内容(比如侧边栏)

- header元素

  header元素描述了文档的头部区域

  header元素注意用于定义内容的介绍展示区域

- footer元素

  footer元素描述了文档的底部区域



# HTML5 Web存储

## 什么是HTML5 Web存储

使用HTML5可以在本地存储用户的浏览数据



## localStorage和sessionStorage

客户端存储数据的两个对象为：

- localStorage -没有时间限制的数据存储
- sessionStorage -针对一个session的数据存储



## localStorage对象

localStorage对象存储的数据没有时间限制。

## sessionStorage对象

sessionStorage方法针对一个session进行数据存储。当用户关闭浏览器窗口后，数据会被删除



# HTML5 应用程序缓存

> 使用HTML5，通过创建cache manifest文件，可以轻松创建web应用的离线版本。



什么是应用程序缓存(Application Cache)

HTML5 引入了应用程序缓存，这意味着web应用可以进行缓存，并可在没有因特网连接时进行访问。应用程序缓存为应用带来三个优势：

- 离线浏览 用户可在应用离线时使用它们
- 速度 已缓存资源加载会很快
- 减少服务器负载 浏览器将只从服务器下载更新过或更改过的资源。

实例：

```html
<!DOCTYPE HTML>
<html manifest="demo.appcache">
<body>
  文档内容
</body>    
</html>
```

##  Cache Manifest基础

如需启用应用程序缓存，请在文档的&lt;html>标签中包含manifest 属性；

每个指定了manifest的页面在用户对其访问时都会被缓存。如果未指定manifest属性，则页面不会被缓存。

manifest文件的建议的文件扩展名是：".appcache"。



## Manifest 文件

mainfest文件是简单的文本文件，它告知浏览器被缓存的内容(以及不缓存的内容)。

manifest文件可分为三个部分：

- CACHE MANIFEST -在此标题下列出的文件将在首次下载后进行缓存
- NETWORK -在此标题下列出的文件需要与服务器的连接，且不会被缓存
- FALLBACK -在此标题列出的文件规定在当前页面无法访问时的回退页面(比如404页面)



### CACHE MANIFEST

基本格式

>CHAHE MANIFEST
>
>/theme.css
>
>/logo.gif
>
>/main.js

上面的manifest文件列出三个资源：一个CSS文件，一个GIF图像，以及一个JavaScript文件。当manifest文件加载后，浏览器会从网站的根目录下载这三个文件。然后，无论用户何时与因特网断开连接，这些资源依然是可用的。

## NETWORK

下面的NETWORK小节规定文件"login.php"永远不会被缓存，且离线时不可用的：

> NETWORK:
>
> login.php

可以使用星号来指定所有资源/文件都需要因特网连接：

> NETWORK:
>
> *

### FALLBACK

下面的FALLBACK小节规定如果无法建立因特网连接，则用”offline.html“替代/html5/目录中的所有文件：

> FALLBACK：
>
> /html/offline.html

**注意：第一个URL是资源，第二个是替补。**

##  更新缓存

一旦应用被缓存，它就会保持缓存知道发生下列情况：

- 用户情况浏览器缓存
- manifest文件被修改
- 有程序来更新应用缓存



# HTML5 Web Workers

web worker是运行在后台的JavaScript，不会影响页面的性能。

## 计数器的创建工程：

### 创建web worker文件

首先，在一个外部JavaScript中创建我们的web worker。

在这里我们创建计数脚本，该脚本存储于"demo_worker.js"文件中：

```javascript
var i=0;
function timeCount(){
	i=i+1;
  	postMessage(i);
  	setTimeout("timeCount()",500);
}
timeCount();
```

postMessage()方法用于向HTML页面传回一段消息

### 创建Web Worker对象

我们已经有web worker文件，现在我们需要从HTML页面调用它。

下面的代码检测是否存在worker，如果不存在，它会创建一个新的web worker对象，然后运行"demo_worker.js"中的代码

```javascript
if(typeof(W)=="undefined")
  {
    w=new Work("demo_worker.js")
  }
```

然后我们就可以从web worker发生和接收消息了。

向web worker添加一个"onmesssage"事件监听器

```javascript
w.onmessage=function(event){
  document.getElementById("result").innerHTML=event.data;
};
```

### 终止Web Worker

当我们创建web worker对象后，它会继续监听消息知道其被终止为止。如需终止web worker，并释放浏览器/计算机资源，请使用terminate()方法：

```javascript
w.terminate();
```

## Web Worker和DOM

由于web worker位于外部文件中，它们无法访问下例JavaScript对象：

- window对象
- document对象
- parent对象



# HTML5 服务器发送事件

HTML5服务器发送事件允许网页获得来自服务器的更新

## Server-Sent事件 -单向消息传递

Server-Sent事件指的是网页自动获取来自服务器的更新

## 接收Server -Sent事件通知

EventSource对象用于接收服务器发送事件通知：

```javascript
var source=new EventSource("demo_see.php");
source.onmessage=function(event)
{
 	document.getElementById("result").innerHTML+="<br>" 
}
```

## EventSource对象

| 事件         | 描述           |
| ---------- | ------------ |
| onopen     | 当通往服务器的连接被打开 |
| onmessaged | 当接收到消息       |
| onerror    | 当发生错误        |



# HTML5 WebSocket

> 这个等下次认真搞一遍

WebSocket是HTML5开始提供的一种在单个TCP连接上进行全双工通讯的协议。