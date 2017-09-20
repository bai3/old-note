---
title: 跨域问题和jsonp
date: 2017-09-19 19:01:04
tags: note
categories : 浏览器

---

# 跨域问题和jsonp

了解浏览器跨域的相关知识和jsonp与json的不同

<!-- more -->

## 什么是跨域

概念:只要协议、域名、端口有任何一个不同，都被当作是不同的域。

简单的说，只有当协议，域名，端口相同的时候才算是同一域名，否则认为需要做跨域的处理
![跨域](跨域问题和jsonp\跨域.png)

跨域问题指的是浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对javascript施加的施加的安全政策。

- 主域名不同  跨域
- 子域名不同 跨域
- 端口不同 跨域
- 协议不同跨域
- localhost 和 127.0.0.1虽然都是本机地址，也算跨域



## 为什么浏览器要限制跨域访问

### 防止CSRF等攻击，防止恶意网站窃取数据，比如读取Cookie

### 限制范围

- Cookie、LocalStorage和IndexDB 无法读取
- DOM 无法获得
- AJAX请求不能发送

### CSRF只是普及

- 什么是CSRF？

  CSRF，中文名称:跨站请求伪造

- CSRF可以什么做什么

  可以这样理解，攻击者盗用你的身份，以你的名义发送恶意请求，个人隐私的泄露以及财产安全。

  原理图

  ![CSRF](跨域问题和jsonp\CSRF.png)

### XSS攻击

- 什么是XSS

  XSS攻击全称跨站脚本攻击，是web应用中的计算机安全漏洞，它允许恶意web用户将代码植入到提供给其他用户使用的页面中


##  跨域的解决方法

- Jsonp
- CORS
- Server Proxy(服务器代理)
- location.hash
- 通过修改document.domian 跨域
- 使用window.name 进行跨域
- 使用HTML5的window.postMessage方法跨域
- WebSocket


- CORS

### jsonp跨域

- 什么是Jsonp

  jsonp也叫做填充式JSON，是应用JSON的一种新方法，只不过是被包含在函数调用中的JSON

  ``` javascript
  callback({"name","trigkit4"})
  ```

  JSONP由两部分组成:回调函数和数据，回调函数式当响应到来时应该在页面中调用的函数，而数据就是传入回调函数中的JSON数据。

  在js中，我们直接用XMLHttpRequest请求不同域上的数据时，是不可以的。但是，在页面上引入不同域上的js脚本文件是可以的，jsonp正是利用这个特性实现的

  ```html
  <script>
    function dosomething(jsondata){
    //处理获取的json数据
    }
  </script>
  <script src="http://example.com/data.php?callback=dosomething"></script>

  ```

js文件载入成功后执行我们在url参数后指定的函数，并且会把我们需要的json数据作为参数传入。所以jsonp是需要服务器端的页面进行配合相应的配合的。

```php
$callback = $_GET['callback'];//获得回调函数名
$data = array('a','b','c');//要返回的数据
echo $callback.'(''json_encode($data)')'
```

jquery 封装jsonp

```javascript
$.getJSON('http://example.com/data.php?callback=?,function(jsondata)'){
    //处理获得的JSON数据
}
```

jquery的$.getJSON方法会自动判断是否跨域，不跨域的话，就调用普通的ajax方法；跨域的话，则会以异步加载js文件的形式来调用jsonp的回调函数

#### JSONP的缺点

JSONP的缺点它只支持GET请求而不支持POST等其他HTTP请求。它只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行javascript调用的问题

### window.name

window.name的不是一个普通的全局变量，而是当前窗口的名字，这里要注意的是每个iframe都有包裹它的window，而这个window是top window的子窗口，而它自然也有window.name 的属性，window.name属性的神奇之处在于name值在同的页面，加载依旧存在。并且可以支持非常长的name值(2M)

### postMessage

postMessage是HTML5新增的一项功能,跨文档消息传输。

### document.domian

对于主域相同而子域不同的情况下，可以通过设置document.domain的办法来解决。



### Server Proxy

服务器代理。当你需要有跨域的请求操作时发送请求给后端，让后端帮你代为请求，然后将获取的结果发送你

### WebSocket

WebSocket是一种通信协议，该协议不实行同源政策，只要服务器支持，就可以通过它进行跨域通信

### CORS

#### 介绍

CORS是跨域资源分享的缩写。它是W3C标准，是跨源AJAX请求根本方法，相比JSONP只能发送GET请求，CORS允许任何类型的请求

#### 原理

它允许浏览器像跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源的使用的限制。

#### 简介

CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。

整个CORS通信过程中，都是浏览器自动完成，不需要用户参与。对于开发者来说，CORS通信与同源的AJAX没有差别，代码完全一样。浏览器一旦发现AJAX请求跨源，就会自动添加一些附加的头信息，又是还会多出一次附加的请求。

因此，实现CORS通信的关键是服务器。只有服务器实现了CORS接口，就可以跨源通信。

