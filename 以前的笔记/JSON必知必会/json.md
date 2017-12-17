---
title: 《JSON必知必会》读书笔记
date: 2017-05-25 20:49:54
tags:
	- json
	- js
categories: note

---

&ensp; 将之前写在onenote的关于json的简要知识点改写成md。

<!-- more -->

---

## 第一章 什么是JSON

- JSON指的是JavaScript对象表示法（JavaScript Object Notation）
- JSON是轻量级的文本数据交换格式
- JSON独立于语言
- JSON具有自我描述性，更易理解
>JSON使用JavaScript语法来描述数据对象，但是JSON独立于语言和平台。JSON解析器和JSON库之处许多不同的编程语言。目前非常多的动态（PHP、JSP、.NET）编程语言都支持JSON。

## 第二章 JSON的语法

**JSON中的名称—值对的名称如果被系统作为对象装入内存的话，将会成为”属性“，不同于名称，值并不是总是需要被双引号包裹。当值是字符串时，必须使用双引号。而在JSON中，数字、布尔值、数组、对象、null等其他类型，这些都不应该被双引号包裹。**

例如：

```json
{
  title："this is my title"
}//不合法
{
  'title':'this is my title'
}//同样不合法
{
  "title":"this is my title"
}//合法的书写
{
  "value":12
  "result":true
}//这些都不加双引号
```

**JSON的名称始终被双引号包裹**

**JSON文件使用.json扩展名**

## 第三章 JSON的数据结构

JSON的数据类型：

- 对象
- 字符串
- 数字
- 布尔值
- null
- 数组

基本嵌套格式

```json
{
  "person":{
    "name":"Lindasy Bassett",
    "heightInInches":66,
    "head":{
      "hair":{
        "color":"light blood",
        "length":"short",
        "style":"A-line"
      },
      "eyes":"green"
    }
  }
}
```

注意事项：

- 遇到双引号、反斜线、\/（正斜线）、\b、\f、\t、\n、\r都需要进行转义（加\）
- 在JSON中布尔值仅能用true和false表示，任何其他形式的写法都会报错（所有字母必须要小写）。
- 对象和数组很关键的一个区别就是，对象是名称-值对构成的列表或者集合，数组是值构成的列表或者集合。
- 对象和数组另一个关键的区别是，数组中所有的值应具有相同的的数据类型。  


##第四章 JSON Schema

基础概念

>jsonschema是描述你的JSON数据格式；JSON模式（应用程序/模式+ JSON）有多种用途，其中之一就是实例验证。验证过程可以是交互式或非交互式的。例如，应用程序可以使用JSON模式来构建用户界面使互动的内容生成除了用户输入检查或验证各种来源获取的数据。

基本格式

```json
{
  "schema":"http://json-schame.org/draft-04/shema",
  "title":"Cat",//文件标题
  "properties":{
    "name":{
      "type":"string"
    },
    "age":{
      "tyep":"number",
      "description":"Your cat's age in year"
    },
    "declawd":{
      "type":"boolean"
    }
  }
}
```

** "required"，值为一个数组，数组中含必填的字段。如果你的JSON Schema中不含”required“名称--值对，那么将不必有必填项。**

总结：

1. JSON Schema是数据交换中的一种虚拟的”合同“

2. JSON验证器负责验证语法错误，JSON Schema负责提供一致性检验

3. JSON Schema可以解决下列有关一致性检验的问题。

   ——值的数据类型是否正确？

   ​          可以具体规定一个值是数字、字符串等类型

   ——是否包含所需要的数据

   可以具体规定哪些数据是需要的，哪些是不需要的

   ——值的形式是否是我需要的？

   可以指定范围、最小值、最大值。



## 第六章 JavaScript中的XMLHTTPRequest与Web API

基本格式

```javascript
var xml=new XMLHTTPRequest();
var url="#";
xml.onreadystatechange=function(){
  if(xml.readyState===4 && xml.state===200){
    var myObject = JSON.parse(xml.responseText);
  	var myJSON = JSON.stringify(myObject);
  }
}
xml.open("GET",url,true);
xml.send();
```

- JSON.parse:反序列化操作，JSON解析成JavaScript对象
- JSON.stringify:序列化操作，将JavaScript对象解析成JSON
- JavaScript中的XMLHttpRequest负责在客户端发起请求，而web API负责在服务端返回响应

XMLHTTPRequest主要属性含义

- onreadystatechange

  可以在代码中给它赋值为一个函数

- readyState

  返回一个0~4的值，用来表示状态码

- status

  返回Http状态码（如200请求表示成功）

- responseText

  当请求成功时，该属性会包含作为文本的响应体

  ​
