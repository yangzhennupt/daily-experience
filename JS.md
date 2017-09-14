1. 请解释事件代理 (event delegation)。
    事件代理利用了事件冒泡的机制，把事件绑定到某个父类元素上，这样就能只用一个事件处理程序就能管理一个类型的所有事件，通过event.target来判断点击的元素是哪个，然后针对特定元素进行处理。
1. 请解释 JavaScript 中 this 是如何工作的。
	this的指向是被调用的时候才确定的
1. 请解释原型继承 (prototypal inheritance) 的原理。
1. 你怎么看 AMD vs. CommonJS？
	AMD与CommonJS区别在于模块加载，AMD是异步的，CommonJs是同步的
1. 请解释为什么接下来这段代码不是 IIFE (立即调用的函数表达式)：function foo(){ }();要做哪些改动使它变成 IIFE?
1. 描述以下变量的区别：null，undefined 或 undeclared？该如何检测它们？
1. 什么是闭包 (closure)，如何使用它，为什么要使用它？
1. 请举出一个匿名函数的典型用例？
1. 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？
1. 请指出 JavaScript 宿主对象 (host objects) 和原生对象 (native objects) 的区别？
1. 请指出以下代码的区别：function Person(){}、var person = Person()、var person = new Person()？
1. .call 和 .apply 的区别是什么？
	传递的参数不一致，call(obj,arg1,arg2,arg3) apply(obj,[arg1,arg2...])
1. 请解释Function.prototype.bind？
	bind是改变this的指向的，它不会立即执行某个函数，而是返回修改后的函数
1. 在什么时候你会使用 document.write()？
1. 请指出浏览器特性检测，特性推断和浏览器 UA 字符串嗅探的区别？
1. 请尽可能详尽的解释 Ajax 的工作原理。
	异步请求基于XMLHttpRequest对象，
1. 使用 Ajax 都有哪些优劣？
1. 请解释 JSONP 的工作原理，以及它为什么不是真正的 Ajax。
	由于同源安全策略，跨域请求是被禁止的，为了解决这个问题，jsonp利用了script标签的src可以访问其他不同源脚本的特性，动态的添加了一个script标签，然后传给服务器一个回调函数名称，当数据返回时，便会触发这个回调函数，以此来实现跨域请求。这中间并没有设计XMLHttpRequest对象，所以说它不是真正的Ajax.
1. 你使用过 JavaScript 模板系统吗？如有使用过，请谈谈你都使用过哪些库？
	vm、artTemplate
1. 请解释变量声明提升 (hoisting)。
	当我们是使用函数声明式来定义函数时，会发现一个现象，就是我们可以把函数的定义写在代码的最下面，然后在定义的上面直接调用这个函数，这是因为JS引擎在解析代码时，会先确定有那些变量、函数需要提前定义，然后再执行。
1. 请描述事件冒泡机制 (event bubbling)。
	事件冒泡机制是从元素被点击开始，从这一层级、事件一直被传播到document。
1. "attribute" 和 "property" 的区别是什么？
1. 为什么扩展 JavaScript 内置对象不是好的做法？
1. 请指出 document load 和 document DOMContentLoaded 两个事件的区别。
1. == 和 === 有什么不同？
	==会隐式的进行类型转换，比如‘123’==123 true   ===是不进行类型转换，数值与类型必须完全相同才返回true
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

## 原型 ##
在js中，每一个对象都会与另一个对象相关联，从另一个对象继承属性，这里的另一个对象就是 **原型**。原型本身也是一个对象，其他对象可以通过它实现属性继承，也可以将任何一个对象作为自身对象的原型。js的任何对象都有原型，除了原型链顶端的对象：Object.prototype
## 原型链 ##
有原型就会出现原型的访问链，一个JS对象原型指向其父类，而父类对象又指向这个父类的原型，这种原型层层连接起来的关系就是原型链，获取原型对象的方法：var a={};a._proto_或者a.constructor.prototype;
## 闭包 ##
闭包就是指能够访问另一个函数作用域变量的函数就是闭包。

简单的demo:

	function outer(){
		var a=0;
		function inner(){
		console.log(a++);		
		}
		return inner;
	}
	var closeur=outer();
	closeur(); //1
	closeur();//2

闭包的特性：

1.函数返回嵌套的函数形成闭包；

2.闭包内部可以访问外部的参数和变量；

3.外部参数和变量在被闭包引用时不会被垃圾回收；

闭包的优点：

1.避免变量对全局的污染；

2.允许函数私有成员的存在；

3.允许变量常驻内存

应用场景：

1.采用函数引用方式的setTimeout调用

2.将函数关联到对象的实例方法

3.封装相关的功能集

## this的指向 ##
this的指向是函数被调用的时候才确定的。

this指向有以下四个场景：

1.如果一个函数中有this,且它没有以对方方法的形式调用，而是以函数名方式执行，那么this就是全局对象。

    function demo(){
     console.log(this)
    }
    demo()//window

2.如果一个函数中有this，且这个函数是以对象方法的形式调用，那么this指向就是调用这个方法的对象。

    var obj={
      test:function(){
         console.log(this);
      }
    }
    obj.test();//obj

3.如果一个函数中有this，并且包含该函数的对象也同时被另一个对象包含，尽管这个函数被最外层的对象调用，但它扔指向它的上级对象。
    
      var obj={
    
      test:{
     	fun:function(){
      			console.log(this)
    		}
    	}
    
    }
    obj.test.fun();//test


4.如果一个构造函数或者类方法中有this，那么它指向由该构造函数或 类创建出来的实例对象。

    class Test{
     constructor(){
       this.test="test"; //类实例
       
    }
    option(){
     console.log(this); //类实例
    }
    
    }
##JS数组遍历的几种方法##
 - forEach
 - map
 - filter
 - some
 - every
 - reduce
 - find/findIndex(ES6)
###forEach###
forEach是对数组里面的每一个元素都执行某个操作;

    var arr=[1,2,3];
    arr.forEach(function(element,index,array){
      console.log(element);
    })
兼容低版本方法

    Array.prototype.forEach=Array.prototype.forEach|| function(fn, context){     
      for (var k = 0, length = this.length; k < length; k++) {
    	if (typeof fn === "function" && Object.prototype.hasOwnProperty.call(this, k)) {
      			fn.call(context, this[k], k, this);
    		}
      	}
    }
###map###
map是将原来的数组按照一定的规则映射为新数据，**返回的是新数组**；
    
      var list=[1,2,3];
      var newList=list.map(function(element){
      return  element*2
    })
    console.log(newList)//2,4,6
兼容低版本方法

	Array.prototype.map=Array.prototype.map||function(fn,context){
		var arr=[];
		if(typeof fn ==="function"){
	 	 for(var k=0,length=this.length;k<length;k++){
			arr.push(fn.call(context,this[k],k,this))
			}
		}
	   return arr;
	}

###filter###
filter返回过滤后、符合条件的新书组，用法和map差不多。有区别的是，filter的回调函数需要返回弱等于true或false的值，如果为true,则通过。
    
    var arr = [0, 1, 2, 3];
    
    var newArr = arr.filter(function (element, index, array) {
      return e;
    })
    
    var newArr2 = arr.filter(function (element, index, array) {
      return e>=2; 
    })
    
    console.log(newArr); // [1, 2, 3]
    console.log(newArr2); // [2, 3]
兼容低版本方法

    Array.prototype.filter = Array.prototype.filter || function (fn, context) {
      var arr = [];
      if (typeof fn === "function") {
    	for (var k = 0, length = this.length; k < length; k++) {
      		fn.call(context, this[k], k, this) && arr.push(this[k]);
    		}
      	}
      return arr;
    };

###some###
只要数组中某个数值符合条件就返回true,否则返回false；

	var isGood=[1,2,3].some(function(element,index,array){
	     return element>=4
	})
	var isGood2=[1,2,4].some(function(element,index,array){
	     return element>=4
	})
	console.log(isGood) //false
	console.log(isGood2)//true
###every###
与some相对，每个元素都符合条件时返回true,否则返回false