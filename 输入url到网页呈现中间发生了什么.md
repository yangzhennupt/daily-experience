## 从输入url到页面呈现，这个过程发生了什么？##
### 1.输入url，浏览器进行解析操作，并开辟新的网络线程去请求 ###
输入url之后，浏览器会进行解析url操作，开辟新的网络线程去请求资源。

首先，进行DNS查询，先检查浏览器缓存，再检查本机与host是否有域名对应的ip，否则就会想DNS域名服务器查询，这里牵扯到dns-prefetch，即DNS预读取。其实在网络资源的请求中，DNS查询占了挺长的时间。我们可以设置如下代码开启dns预读取。
	
	<meat http-equiv="x-dns-prefetch-control" content="on"> <link rel="dns-prefetch" href="www.zhihu.com">

然后，查询到域名对应的IP之后，发起TCP/IP请求，这里主要包括三次握手四次挥手。即建立连接需要三次握手，例如：C代表客户端，S代表服务端;C说：你好，你是S吗？S说：我是S，你是C吗？C说：是的，我是C；然后连接就建立成功，接下来就开始数据传输。

断开连接需要四次挥手，分为主动方与被动方；

主：我已经关闭了向你发送数据的通道了只能被动接受。
从：收到了关闭的消息。
从：那我告诉你我也关闭了。
主：最后收到消息，之后双方无法通信。

#### TCP/IP的并发限制 ####

浏览器对同一域名并发tcp/ip连接是有限制的（2-10个不等）
而在http1.0中，一个资源下载就是一个tpc/ip请求。所以针对这个瓶颈，又有了很多优化方案（图片合并，代码压缩，小图片base64编码，http2.0）；
#### GET与POST的请求区别 ####
本质均为tcp/ip，但是get只会传输一个tcp/ip包，post有两个。

get请求时，浏览器会把headers和data一起发送过去，服务器响应200.
post请求时，浏览器先发送headers，服务器响应100 continue，然后浏览器再发送data，服务器响应200.

#### http报文结构 ####

通用头部，请求/响应头部，请求/响应体；

通用头部：

Request Url：请求的web服务器地址，
Request Method:请求方式(GET,POST,OPTIONS,PUT,HEAD,DELETE,CONNECT,TRACE)，
Status Code：请求的返回状态码
Remote Address：请求的远程服务器地址（会转为IP）


Method分为两个归属：

http1.0  GET,POST,HEAD

http1.1 OPTIONS,PUT,DELETE,CONNECT,TRACE.

常见状态码:
200-请求成功，资源返回给客户端。
304-上次请求之后，请求的网页没有修改，请客户端使用本地缓存。
400-客户端请求有错
401-请求未经授权
403-禁止访问
404-资源未找到
500-服务器内部错误
503-服务不可用
504-服务器超时


1xx-指示信息，表示请求已接收，继续处理
2xx-成功，请求已被接受
3xx-重定向，完成请求需要进一步操作
4xx-客户端错误
5xx-服务器错误

#### 请求/响应头部 ####

 请求头部

    Accept: 接收类型，表示浏览器支持的MIME类型
    （对标服务端返回的Content-Type）
    Accept-Encoding：浏览器支持的压缩类型,如gzip等,超出类型不能接收
    Content-Type：客户端发送出去实体内容的类型
    Cache-Control: 指定请求和响应遵循的缓存机制，如no-cache（强缓存）
    If-Modified-Since：对应服务端的Last-Modified，用来匹配看文件是否变动，只能精确到1s之内，http1.0中）（协商缓存）
    Expires：缓存控制，在这个时间内不会请求，直接使用缓存，http1.0，而且是服务端时间（强缓存）
    Max-age：代表资源在本地缓存多少秒，有效时间内不会请求，而是使用缓存，http1.1中
    If-None-Match：对应服务端的ETag，用来匹配文件内容是否改变（非常精确），http1.1中
    Cookie: 有cookie并且同域访问时会自动带上
    Connection: 当浏览器与服务器通信时对于长连接如何进行处理,如keep-alive
    Host：请求的服务器URL
    Origin：最初的请求是从哪里发起的（只会精确到端口）,Origin比Referer更尊重隐私
    Referer：该页面的来源URL(适用于所有类型的请求，会精确到详细页面地址，csrf拦截常用到这个字段)
    User-Agent：用户客户端的一些必要信息，如UA头部等

响应头部
	
	Access-Control-Allow-Headers: 服务器端允许的请求Headers
	Access-Control-Allow-Methods: 服务器端允许的请求方法
	Access-Control-Allow-Origin: 服务器端允许的请求Origin头部（譬如为*）（实现CROS时必须设定的）
	Content-Type：服务端返回的实体内容的类型
	Date：数据从服务器发送的时间
	Cache-Control：告诉浏览器或其他客户，什么环境可以安全的缓存文档
	Last-Modified：请求资源的最后修改时间
	Expires：应该在什么时候认为文档已经过期,从而不再缓存它
	Max-age：客户端的本地资源应该缓存多少秒，开启了Cache-Control后有效
	ETag：请求变量的实体标签的当前值
	Set-Cookie：设置和页面关联的cookie，服务器通过这个头部把cookie传给客户端
	Keep-Alive：如果客户端有keep-alive，服务端也会有响应（如timeout=38）
	Server：服务器的一些相关信息

#### http2.0 ####

http2.0与http1.1显著不同的点


- 多路复用（一个tcp/ip连接可以请求多个资源）
- 首部压缩(http头部压缩，减少体积)
- 二进制分帧(应用层与传送层之间加了一层二进制分帧层，改进传输性能)
- 服务器端推送(服务器可以对一个请求发出多个响应，可以主动通知客户端)
- 请求优先级 

#### http缓存 ####
缓存可以分为**强缓存200(from  cache)**与**协商缓存304**
- 强缓存时，浏览器如果判断缓存未过期，则直接使用，无需发起http请求。
- 协商缓存，浏览器会向服务端发起请求,服务器告诉浏览器资源未改变，让浏览器使用本地缓存。

#### 缓存头部简介 ####

强缓存：（http1.1）Cache-Control/Max-Age  （http1.0）Pragma/Expires
ps：Max-Age不是一个头部，而是Cache-Control头部的值

Expires:服务端配置，强缓存，一般对应服务器的事件

Cache-Control:缓存控制头部，有no-cache,max-age等取值，max-age的值一般是绝对时间

协商缓存：（http1.1）If-None-Match/E-tag  （http1.0）If-Modified-Since/Last-Modified

If-None-Match/E-tag 成对出现，属于协商缓存，其中浏览器头部的是If-None-Match，服务端是E-tag，请求发出后如果If-None-Match和E-tag匹配，代表内容未变，通知浏览器使用本地缓存，与Last-Modified相比，更精准，没有1s精准度限制。

If-Modified-Since/Last-Modified 这两个成对出现，浏览器头部是If-Modified-Since,服务端是Last-Modified，如果匹配则加载缓存，指的是文件最后修改事件，只能精准到1s以内。

### 2.解析页面流程 ###

浏览器内核拿到内容后，渲染步骤大致可以分为以下几步：
	
	1. 解析HTML，构建DOM树
	
	2. 解析CSS，生成CSS规则树
	
	3. 合并DOM树和CSS规则树，生成render树
	
	4. 布局render树（Layout/reflow），负责各元素尺寸、位置的计算
	
	5. 绘制render树（paint），绘制页面像素信息
	
	6. 浏览器会将各层的信息发送给GPU，GPU会将各层合成（composite），显示在屏幕上


解析HTML构建DOM：Bytes → characters → tokens → nodes → DOM

列举其中的一些重点过程：
	
	1. Conversion转换：浏览器将获得的HTML内容（Bytes）基于他的编码转换为单个字符
	
	2. Tokenizing分词：浏览器按照HTML规范标准将这些字符转换为不同的标记token。每个token都有自己独特的含义以及规则集
	
	3. Lexing词法分析：分词的结果是得到一堆的token，此时把他们转换为对象，这些对象分别定义他们的属性和规则
	
	4. DOM构建：因为HTML标记定义的就是不同标签之间的关系，这个关系就像是一个树形结构一样

CSS规则树也是类似的解析过程，这里就不再描述了。

当DOM树和CSSOM都有了后，就要开始构建渲染树了

一般来说，渲染树和DOM树相对应的，但不是严格意义上的一一对应

因为有一些不可见的DOM元素不会插入到渲染树中，如head这种不可见的标签或者display: none等

Reflow，即回流。一般意味着元素的内容、结构、位置或尺寸发生了变化，需要重新计算样式和渲染树。
Repaint，即重绘。意味着元素发生的改变只是影响了元素的一些外观之类的时候（例如，背景色，边框颜色，文字颜色等），此时只需要应用新样式绘制这个元素就可以了。
