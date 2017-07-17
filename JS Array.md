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