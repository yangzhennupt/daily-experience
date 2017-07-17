- CSS 中类 (classes) 和 ID 的区别。	
	类不是唯一的，而ID是唯一的，ID的优先级比类的高
- 请解释浮动 (Floats) 及其工作原理。	
	浮动漂浮于正常的文档流之上，且无论元素浮动之前是哪种元素，都会生成一个块级框，盒子的宽度不在延伸，根据内容确定
- 描述z-index和叠加上下文是如何形成的。
		margin、定位等都会引起元素的叠加，：z-index值可以控制定位元素在垂直于显示屏方向（Z 轴）上的堆叠顺序（stack order），值大的元素发生重叠时会在值小的元素上面。 使用相对性：z-index值只决定同一父元素中的同级子元素的堆叠顺序。父元素的z-index值（如果有）为子元素定义了堆叠顺序（css版堆叠“拼爹”）。向上追溯找不到含有z-index值的父元素的情况下，则可以视为自由的z-index元素，它可以与父元素的同级兄弟定位元素或其他自由的定位元素来比较z-index的值，决定其堆叠顺序
- 请描述 BFC(Block Formatting Context) 及其如何工作。
- 列举不同的清除浮动的技巧，并指出它们各自适用的使用场景。
	对于一个容器来说，里面的元素如果浮动了，是无法撑开这个容器的，清除浮动的方法：
    1添加一个新元素应用  clear:both;
	2父元素定义overflow:auto或hidden;zoom:1；不能定义height 必须有width或zoom:1
	3伪类 example:after{display:block;content:'';width:0;height:0;visibility:hidden;}
- 请解释 CSS sprites，以及你要如何在页面或网站中实现它。
	将所有的图片集中在一个图片上，减少http请求，通过background-position来改变位置
- 你最喜欢的图片替换方法是什么，你如何选择使用。
	text-indent  将文本移除到屏幕外 SEO更好
- 你会如何解决特定浏览器的样式问题？
- 如何为有功能限制的浏览器提供网页？
- 你会使用哪些技术和处理方法？
- 有哪些的隐藏内容的方法 (如果同时还要保证屏幕阅读器可用呢)？
- 你用过栅格系统 (grid system) 吗？如果使用过，你最喜欢哪种？
- 你用过媒体查询，或针对移动端的布局/CSS 吗？
- 你熟悉 SVG 样式的书写吗？
- 如何优化网页的打印样式？
	@media print
- 在书写高效 CSS 时会有哪些问题需要考虑？
	少用全局reset
	良好的命名
	代码缩写
	多重选择
	适当注释
	不要用@import
	使用外联CSS
	慎用css表达式
- 请描述你曾经使用过的 CSS 预处理器的优缺点。
	嵌套规则、函数、变量、浏览器兼容性
- 如果设计中使用了非标准的字体，你该如何去实现？
	使用图片、引入字体库、
- 请解释浏览器是如何判断元素是否匹配某个 CSS 选择器？
	浏览器首先会最外层的选择器包含在内维护一个数组，然后去这个数组里去掉不匹配的，直到最后一个匹配的
- 请描述伪元素 (pseudo-elements) 及其用途。
	伪元素
- 请解释你对盒模型的理解，以及如何在 CSS 中告诉浏览器使用不同的盒模型来渲染你的布局。
	盒模型由margin、border、padding、content来组成，分为W3C盒模型和IE盒模型，W3C盒模型的width是content的宽度,IE盒子则是包含margin、padding、border的。可以通过设置box-sizing:border-box/content-box来使用不同的盒模型
- 请解释 * { box-sizing: border-box; } 的作用, 并且说明使用它有什么好处？
	作用是所有元素都应用border-box的属性，好处是能够更快速的定义一个元素的宽高，而不是通过加法计算。
- 请罗列出你所知道的 display 属性的全部值
	none、inline、inline-block、block、table、flex、list-item
- 请解释 inline 和 inline-block 的区别？
	inline元素没有宽高，inline-block可以设置宽高 
- 请解释 relative、fixed、absolute 和 static 元素的区别
	static为默认值，对象遵循常规流
	relative 对象遵循常规流，可以使用top,left,right,bottom等偏移，不影响常规流的其他元素.
	fixed	脱离文档流，以窗口为参考点进行定位
	absolute 脱离文档流，margin不与其他任何margin折叠、定位的基准为离得最近的上级 非static的元素
- CSS 中字母 'C' 的意思是叠层 (Cascading)。请问在确定样式的过程中优先级是如何决定的 (请举例)？如何有效使用此系统？
	！important>内联>id>class
- 你在开发或生产环境中使用过哪些 CSS 框架？你觉得应该如何改善他们？
- 请问你有尝试过 CSS Flexbox 或者 Grid 标准规格吗？
- 为什么响应式设计 (responsive design) 和自适应设计 (adaptive design) 不同？
- 你有兼容 retina 屏幕的经历吗？如果有，在什么地方使用了何种技术？
- 请问为何要使用 translate() 而非 absolute positioning，或反之的理由？为什么？