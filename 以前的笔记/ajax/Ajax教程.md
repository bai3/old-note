# Ajax教程

- AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。
- AJAX 不是新的编程语言，而是一种使用现有标准的新方法。
- AJAX 最大的优点是在不重新加载整个页面的情况下，可以与服务器交换数据并更新部分网页内容。
- AJAX 不需要任何浏览器插件，但需要用户允许JavaScript在浏览器上执行。


## Ajax应用

- 运用XHTML+CSS来表达资讯；

- 运用JavaScript操作DOM（Document Object Model）来执行动态效果；

- 运用XML和XSLT操作资料;

- 运用XMLHttpRequest或新的Fetch API与网页服务器进行异步资料交换；

- 注意：AJAX与Flash、Silverlight和Java Applet等RIA技术是有区分的。

##Ajax工作原理

![ajax](F:\白\桌面文件\note\ajax\ajax.png)

## Ajax创建对象

> XMLHttpRequest是Ajax的基础

### XMLHTTPRequest 对象

XMLHTTPRequest用于在后台与服务器交换数据。这意味着可以再不重新加载整个网页情况下，对网页的某部分进行更新。

### 创建XMLHTTPRequest

```javascript
variable = new　XMLHTTPRequest();
```

老版本的IE浏览器使用ActiveX对象

```javascript
variable = new ActiveXObject("Microsoft.XMLHTTP");
```

为了应对所有浏览器，故采用下列写法

```javascript
var xmlhttp;
if (window.XMLHttpRequest)
{
    //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
}
else
{
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
```

## Ajax 向服务器发送请求

> XMLHttPRequest对象用于和服务器交换数据

### 向服务器发送请求

如需将强求发送服务器，我们使用XMLHttpRequest对象的open()和send()方法

```javascript
xmlhttp.open("GET","ajax_info.txt",true);
xmlhttp.send();
```

| 方法                     | 描述                    |
| ---------------------- | --------------------- |
| open（method,url,async) | 规定请求的类型、URL以及是否异步处理请求 |
| send(string)           | 将请求发送到服务器 !仅用于POST请求  |

### GET和POST的区别

与POST相比，GET更简单也更快

然而，在以下情况中，请使用POST请求

- 无法使用缓存文件（更新服务器的文件或数据）
- 向服务器发送大量数据（POST没有数据量限制）
- 发送包含未知字符的用户输入时，POST比GET更稳定也更可靠


### GET请求

一个简单的GET请求

```javascript
xmlhttp.open("GET","/try/ajax/demo_get.php",true);
xmlhttp.send();
```

可是上面的例子你可能得到的是缓存的结果，为了避免这种情况，向URL添加一个唯一的ID

例如：

```javascript
xmlhttp.open("GET","/try/ajax/demo_get.php?t="+Math.random(),true);
xmlhttp.send();
```

> Math.random()是数学随机数的意思

### POST请求

例子

```javascript
xmlhttp.open("POST","/try/ajax/demo_post.php",true);
xmlhttp.send();
```

POST也可以像HTML表单那样POST数据，请使用setRequestHeader()来添加HTTP头。然后在send()方法中规定你希望发送的数据

实例：

```javascript
xmlhttp.open("POST","/try/ajax/demo_post2.php",true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send("fname=Henry&lname=Ford");
```

| way                            | description                             |
| ------------------------------ | --------------------------------------- |
| setRequestHeader(header,value) | 向请求添加HTTP头。- header：规定头的名称- value：规定头的值 |

### url-服务器上的文件

open()方法的url参数是服务器上文件的地址

```javascript
xmlhttp.open("GET","ajax_test.html",true);
```

### 异步 True或False？

通过AJAX，JavaScript无需等待服务器的响应，而是：

- 在等待服务器响应时执行其他的脚本
- 当响应就绪后响应进行处理
###Async=true

当使用async=true的时候，规定在响应处于onreadystatechange事件中的就绪状态时执行的函数

###Async=false
如果需要async=false，请将open()方法中的第三个参数改为false。
>我们不推荐使用async=false，但对于一些小型的请求也是可以的。
>
>请记住，JavaScript会等到服务器响应就绪才继续执行。如果服务器繁忙或者缓慢，应用程序会挂机或停止



## Ajax-服务器 响应

### 服务器响应

如需获得来自服务器的响应，请使用XMLHttpRequest对象的responseText或responseXML属性。

| 属性           | 描述           |
| ------------ | ------------ |
| responseText | 获得字符串形式的响应数据 |
| responseXML  | 获得XML形式的响应数据 |

responseText的实例响应不是XML

```javascript
document.getElementById("myDiv").innerHTML=xmlhttp.resposeText;
```

响应是XML，则采用respondText属性，实例

```javascript
xmlDoc=xmlhttp.responseXML;
txt="";
x=xmlDoc.getElementsByTagName("ARTIST");
for (i=0;i<x.length;i++)
{
    txt=txt + x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("myDiv").innerHTML=txt;
```

## Ajax - onreadystatechange事件

当请求被发送到服务器时，我们需要执行一些基于响应的任务

每单readyState改变时，就会触发onreadystatechange事件.

readyState 属性存在XMLHttpRequest的状态信息。

下面是XMLHttpRequest 对象的三个重要属性

| 属性                 | 描述                                       |
| ------------------ | ---------------------------------------- |
| onreadystatechange | 存储函数（或函数名），每readyState属性改变时，就会调用该函数      |
| readyState         | 存在XMLHttpRequest的状态，从0到4发生变化。0：请求未初始化1：服务器连接已建立 2：请求已接受 3：请求处理中 4：请求已完成，且响应已就绪 |
| status             | 200：“OK”      404：没有找到页面                 |

在onreadystatechange时间中，我们规定当服务器响应已做好被处理的准备时所执行的任务

当readyState等于4且状态为200时，表示响应已就绪。

具体例子

```javascript
xmlhttp.onreadystatechange=function(){
  if(xmlhttp.readyState==4&&xmlhttp.status==200)
    {
      document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
}
```

### 使用回调函数

如果你的网站上有多个AJAX任务，那么你应该创建XMLHTTPRequest对象编写出一个标准的函数，并为每个AJAX任务调用该函数。