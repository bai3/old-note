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

![ajax](ajax\ajax.png)

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

### url-服务器上的文件

open()方法的url参数是服务器上文件的地址

```javascript
xmlhttp.open("GET","ajax_test.html",true);
```

