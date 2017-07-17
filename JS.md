1. 请解释事件代理 (event delegation)。
1. 请解释 JavaScript 中 this 是如何工作的。
1. 请解释原型继承 (prototypal inheritance) 的原理。
1. 你怎么看 AMD vs. CommonJS？
	AMD与CommonJS区别在于模块加载，AMD是同步的，CommonJs是异步的
1. 请解释为什么接下来这段代码不是 IIFE (立即调用的函数表达式)：function foo(){ }();要做哪些改动使它变成 IIFE?
1. 描述以下变量的区别：null，undefined 或 undeclared？该如何检测它们？
1. 什么是闭包 (closure)，如何使用它，为什么要使用它？
1. 请举出一个匿名函数的典型用例？
1. 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？
1. 请指出 JavaScript 宿主对象 (host objects) 和原生对象 (native objects) 的区别？
1. 请指出以下代码的区别：function Person(){}、var person = Person()、var person = new Person()？
1. .call 和 .apply 的区别是什么？
	传递的参数不一致，call(obj,arg1,arg2,arg3) apply(obj,[arg1,arg2...])
1. 请解释 Function.prototype.bind？
1. 在什么时候你会使用 document.write()？
1. 请指出浏览器特性检测，特性推断和浏览器 UA 字符串嗅探的区别？
1. 请尽可能详尽的解释 Ajax 的工作原理。
1. 使用 Ajax 都有哪些优劣？
1. 请解释 JSONP 的工作原理，以及它为什么不是真正的 Ajax。
1. 你使用过 JavaScript 模板系统吗？
1. 如有使用过，请谈谈你都使用过哪些库？
1. 请解释变量声明提升 (hoisting)。
1. 请描述事件冒泡机制 (event bubbling)。
1. "attribute" 和 "property" 的区别是什么？
1. 为什么扩展 JavaScript 内置对象不是好的做法？
1. 请指出 document load 和 document DOMContentLoaded 两个事件的区别。
1. == 和 === 有什么不同？
1. 请解释 JavaScript 的同源策略 (same-origin policy)。
1. 如何实现下列代码：
1. [1,2,3,4,5].duplicator(); // [1,2,3,4,5,1,2,3,4,5]
		Array.prototype.duplicator=function(){
		 var origin=this.concat(),
		  	 res=this.concat(origin);
		 return res;
		}
1. 什么是三元表达式 (Ternary expression)？“三元 (Ternary)” 表示什么意思？
1. 什么是 "use strict"; ? 使用它的好处和坏处分别是什么？
1. 请实现一个遍历至 100 的 for loop 循环，在能被 3 整除时输出 "fizz"，在能被 5 整除时输出 "buzz"，在能同时被 3 和 5 整除时输出 "fizzbuzz"。
1. 为何通常会认为保留网站现有的全局作用域 (global scope) 不去改变它，是较好的选择？
1. 为何你会使用 load 之类的事件 (event)？此事件有缺点吗？你是否知道其他替代品，以及为何使用它们？
1. 请解释什么是单页应用 (single page app), 以及如何使其对搜索引擎友好 (SEO-friendly)。
1. 使用 Promises 而非回调 (callbacks) 优缺点是什么？
1. 使用一种可以编译成 JavaScript 的语言来写 JavaScript 代码有哪些优缺点？
1. 你使用哪些工具和技术来调试 JavaScript 代码？
1. 你会使用怎样的语言结构来遍历对象属性 (object properties) 和数组内容？
1. 请解释可变 (mutable) 和不变 (immutable) 对象的区别。
1. 请举出 JavaScript 中一个不变性对象 (immutable object) 的例子？
1. 不变性 (immutability) 有哪些优缺点？如何用你自己的代码来实现不变性 (immutability)？
1. 请解释同步 (synchronous) 和异步 (asynchronous) 函数的区别。
1. 什么是事件循环 (event loop)？
1. 请问调用栈 (call stack) 和任务队列 (task queue) 的区别是什么？
1. 解释 function foo() {} 与 var foo = function() {} 用法的区别	
	函数声明式，程序运行前就已经存在了；变量声明式，会有先后顺序