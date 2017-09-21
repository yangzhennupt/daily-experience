1. typeof 检测一个为声明的值也会返回undefined,而不是抛出错误。

    	var message;
    
    	// var age;并未声明；
    
    	typeof(message);//undefined;
    
    	typeof(age);//undefined;
2. 0.1+0.2!=0.3 (使用基于IEEE754数值的浮点计算通病)。

		0.1+0.2=0.30000000000000004;
3. NaN==NaN 结果是false。

4. forEach函数中用return是无法退出循环的。

5. for-in语句迭代出来的结果并不保证顺序。
6. 通过arguments对象访问到函数参数，例如arguments[0]，arguments[1]...，但是arguments本身并不是数组，只是类似数组。
7. 基本类型值在内存中占用固定大小，保存在栈内存中。
8. 引用类型的值是对象，保存在堆内存中。 