- doctype(文档类型) 的作用是什么？
   说明web设计中所用的html或xhtml的类型，指出浏览器或者其他阅读程序应该以什么样的规则来渲染（没有声明则一般用混杂模式或者兼容模式，其他一般是严格模式或标准模式，总之，加上doctype声明，让浏览器使用标准模式，引用DTD）

- 浏览器标准模式 (standards mode) 、几乎标准模式（almost 

- standards mode）和混杂模式 (quirks mode) 之间的区别是什么？
	标准模式：浏览器根据规则渲染并呈现页面
	混杂模式：页面以比较宽松的兼容方式现实
	几乎标准：很多特性符合标准，但不是全部（例如图片间隙）
	区别：对于盒模型的解析。
      标准模式：Width是内容宽度，
	  混杂模式:width就是元素的宽度（包含margin、padding、border）

- HTML 和 XHTML 有什么区别？
	XHTML中的标签都必须被正确地嵌套,HTML中的某些标签可以彼此不正确的嵌套。
	XHTML中的所有标签必须要关闭。
	XHTML中规范定义：标签名和属性对大小写敏感,所有XHTML标签名必须用小写字母。
	XHTML文档必须拥有根元素。
	XHTML中标签的属性值要使用双引号"。

- 如果页面使用 'application/xhtml+xml' 会有什么问题吗？


- 如果网页内容需要支持多语言，你会怎么做？


- 在设计和开发多语言网站时，有哪些问题你必须要考虑？


- 使用 data- 属性的好处是什么？


- 如果把 HTML5 看作做一个开放平台，那它的构建模块有哪些？


- 请描述 cookies、sessionStorage 和 localStorage 的区别。
	cokkie数据始终在同源的http请求中携带，大小不超过4k
	sessionStorage和localStorage不会自动把数据发送给服务器，仅保存在本地，存储数量比cookie大得多。sessionStorage在浏览器关闭后失效，localStorage持久有效，cookie可以设置过期时间。

- 请解释 `<script>、<script async> 和 <script defer> `的区别。
	当浏览器渲染时，碰到script标签会被阻塞，然后解析script标签内的脚本，在解析完成之前，一直处于阻塞状态。
	有async属性，表示该脚本处于异步，不会影响渲染，但不保证执行的先后顺序
	defer是延迟脚本，文档完全呈现后执行，有先后顺序
- 为什么通常推荐将 CSS <link> 放置在 <head></head> 之间，而将 JS `<script> 放置在 </body> `之前？你知道有哪些例外吗？
 	阻塞，单线程

- 什么是渐进式渲染 (progressive rendering)？


- 你用过哪些不同的 HTML 模板语言？