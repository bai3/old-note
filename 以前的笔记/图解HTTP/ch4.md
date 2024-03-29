# 第4章 返回结果的HTTP状态码

> HTTP状态码负责表示客户端HTTP请求的返回结果、标记服务器端的处理是否正常、通知出现的错误等工作。

## 4.1 状态码告知从服务器端返回的请求结果

> 状态码的职责是当客户端向服务器端发送请求时，描述返回的请求结果。借助状态码，用户可以知道服务器端是正常处理了请求，还是出现了错误。

**状态码的类别**

|      | 类别                     | 原因短语          |
| ---- | :--------------------- | ------------- |
| 1XX  | Informational(信息性状态码)  | 接收的请求正在处理     |
| 2XX  | Success(成功状态码)         | 请求正常处理完毕      |
| 3XX  | Redirection(重定向状态码)    | 需要进行附加操作以完成请求 |
| 4XX  | Client Error(客户端错误状态码) | 服务器无法处理请求     |
| 5XX  | Server Error(服务器错误状态码) | 服务器处理请求失败     |

## 4.2 2XX成功

> 2XX的响应结果表明请求被正常处理

### 4.2.1 200OK

表示从客户端发来的请求在服务器端被正常处理。

在响应报文内，随状态码一起返回的信息会因为方法的不同而发生改变。

比如，使用GET方法时，对应请求的资源的实体会作为响应返回；而使用HEAD方法时，对应请求资源的实体部分不随着报文主体作为响应返回。

### 4.2.2 204 No Content

该状态码代表服务器接收的请求已成功处理，但在返回的响应报文中不含实体的主体部分。另外，也不允许返回任何实体的主体。比如，当浏览器发出请求处理后，返回204响应，那么浏览器显示的页面不发生更新。

### 4.2.3 206 Partial Content

该状态码表示客户端进行了范围请求，而服务器成功执行了这部分的GET请求。响应报文中包含有Content-Range指定范围的实体内容。

## 4.3 3XX 重定向

### 4.3.1 301 Moved Permanently

永久性重定向。该状态吗表示请求的资源已被分配了新的URI，以后应使用资源现在所指的URI。

### 4.3.2 302 Found

临时性重定向。该状态码表示请求的资源已被分配了新的URI，希望用户（本次）能使用新的URI访问。

**与状态码301类似，但是302代表的资源不是被永久移动，只是临时性质**

### 4.3.3 303 See Other

该状态码表示由于请求对应的资源粗存在另一个URI，应使用GET方法定向获取请求的资源

303状态码和302状态码有着相同的功能，但303状态码明确表示客户端应采用GET方法获取资源，这点与302不同



> 当301、301、302响应状态码返回时，几乎所有的浏览器都会把POST改成GET，并删除请求报文内的主体，之后请求会自动再次发送。
>
> 301、302标准是禁止将POST方法改变成GET方法的，但实际使用时大家都会这么做。

### 4.3.4 304 Not Modified

该状态码表示客户端发送附加条件请求的时候，服务器端允许请求访问资源，但未满足条件的情况

### 4.3.5 307 Temporary Redirect

临时重定位。该状态码与302Found有着相同的含义

## 4.4 4XX客户端错误

> 4XX的响应结果表明客户端是发生错误的原因所在。

### 4.4.1  400 Bad Request

该状态码表示请求报文中存在语法错误。当错误发生时，需要修改请求的内容后再次发送请求。

### 4.4.2 401 Unauthorized

该状态码表示发送的请求需要有通过HTTP认证的仁政信息。

### 4.4.3 403 Forbidden

该状态码表明对请求资源的访问被服务器拒绝了。

### 4.4.4 404 Not Found

该状态码表明服务器上无法找到请求的资源。

## 4.5 5XX 服务器错误

> 5XX的响应结果表明服务器本身发生错误

### 4.5.1 500 Internal Server Error

该状态码表明服务器端在执行请求时发生了错误。也有可能是Web应用存在的bug或某些临时的故障

### 4.5.2 503 Service Unavailable

该状态码表明服务器暂时处于超负载或正在进行停机维护，现在无法处理请求。