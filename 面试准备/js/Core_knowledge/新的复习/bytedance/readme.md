1. HTTP请求的类型有哪些？
A: get(发出请求) post(上传信息，发出表单，会创建新资源或者修改原有资源) options(返回服务器可以支持的HTTP请求方法，可用于  CORS跨域) put(上传指定内容) delete(删除资源) trace(测试一个请求，当一个请求发生时，服务器返回请求的内容)
   HEAD(与get类似，但只返回请求的头部) connect(建立一个对资源的连接，连接后会返回状态码200)

2. HTTP报文组成部分
A: HTTP报文分为请求报文和响应报文，细分又为请求头和请求体   响应头和响应体
 即：起始行 + 头部 + 空行 + 实体
- 起始行
请求报文是 方法 + 路径 + HTTP版本
 类似于接口对接，需要请求方法 + 路径 + 版本 api.get('/home')
响应报文是 HTTP版本 + 状态码 + 原因
 类似于接口返回的值： 返回请求后的状态码和原因
```js
// 请求报文
GET /home HTTP/1.1
// 响应报文
HTTP/1.1 200 ok
```
- 头部 描述浏览器，服务器的一些信息
通用首部字段，请求首部字段，响应首部字段，实体首部字段

- 空行 很重要，用来区分头部和实体
如果在头部后面加一个空行，那么它后面的会被视为实体

- 实体 具体的数据 分为请求体和响应体

3. HTTP常见header
1. 通用头部 
cache-control 缓存机制 强缓存
Connection： keep-alive 是否持久化连接
Date：描述服务器发送消息的时间
2. 请求头部
expires 告诉客户端缓存的过期时间，存在于http1.0，描述的是过期的具体时间
**弊端**：服务器和客户端的时间可能不一样，所以过期时间可能不准确，在HTTP1.1被cache-control代替
cookie 
Content-Type 请求体的MIME类型
if-None-Match 协商缓存相关
Origin 发起一个针对跨域资源共享的请求
3. 响应头部
Etag 将资源(文件)以字符串的形式给文件生成唯一标识
Content-Type
Access-Control-Allow-Origin 针对跨域的


3. 
