### WebSocket ###

> 什么是WebSocket?

以往我们在页面中要实现一个实时更新的业务，必须采用轮询的方法向服务器发送ajax请求，这样无疑提高了服务器的负荷。

WebSocket的目标是在一个持久连接上提供全双工、双向通信,服务器可以主动向我们推送消息，我们就无需去轮询结果。

在JavaScirpt中创建了WebSocket之后，会有一个HTTP请求发送到浏览器以发起链接。在取得服务器响应后，建立的连接会使HTTP升级协议交换为Web Scoket协议。

WebSocket使用了**自定义的协议**，所以URL是ws://;加密的协议则是wss://。

WebSocket 采用了自定义协议而非HTTP协议，能够在客户端和服务器之间发送非常少的数据量，而不必担心HTTP那样字节级的开销。

> WebSocket API 

要创建webSocket，必须先实例一个WebSocket对象并传入要连接的URL；

	var socket = new WebSocket("ws://www.demo.com/a.action");

必须给构造函数传入一个绝对路径的URL，WebSocket无同源策略，因此可以通过它打开任意站点的连接，至于是否通信，则是服务器决定的。
实例化WebSocket之后，浏览器马上会尝试建立连接，与XmlHttpRequest对象一样，webSocket也有一个表示当前状态的readyState属性：

- WebSocket.OPENING(0):正在建立连接；
- WebSocket.OPEN(1):已经建立连接；
- WebSocket.CLOSING(2):正在关闭连接；
- WebSocket.CLOSE(3):已经关闭连接；

WebSocket并没有readystatechange事件，不过它有其他事件对应着不同的状态；

> 发送和接收数据

WebSocket打开后，就可以通过send()方法向服务器发送数据，参数必须为字符串。例如：

	var socket = new WebSocket("ws://www.demo.com/a,action");

	socket.send('hello socket');

因为WebSocket只能发送纯文本数据，因此对于复杂的数据结构，必须进行序列化，例如JSON，则必须调用JSON.stringify()；

当服务器推送数据时，则会触发message事件，这个message事件与其他消息传递的协议类似，把数据放在evnet.data里面；

	socket.onmessage = function(event){
		console.log(event.data);
	}
同传递字符串一样，服务器返回的也是字符串。



> 其他事件与关闭方法

WebSocket关闭时，需要调用close()方法，这样连接就被关闭了。
	
	socket.close();

webSocket还有以下三个事件，在连接生命周期不同阶段触发：

- open:在成功建立连接时触发。
- error:在发生错误时触发，连接不能持续。
- close:在连接关闭时触发。

WebSokcet不支持DOM2级事件监听器，因此必须使用DOM0级语法分别定义；

	var socket = new Socket('ws://www.demo.com/a.action');
	
	socket.onopen = function(){
		//连接建立时触发
	};
	socket.onerror = function(){
		//连接错误时触发
	};
	socket.onclose = function(event){
		//连接关闭时触发
	};

在这三个事件中，只有close事件的evnet对象有额外的信息，里面有三个属性值：wasClean、code、reason;其中,wasClean是一个布尔值，表示连接是否已经明确的关闭；code是服务器返回的数值状态码;reason是一个字符串，包括服务器返回的信息。可以把这些信息现实给用户或作为其他用。