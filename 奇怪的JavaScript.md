1. typeof 检测一个为声明的值也会返回undefined,而不是抛出错误；

    	var message;
    
    	// var age;并未声明；
    
    	typeof(message);//undefined;
    
    	typeof(age);//undefined;