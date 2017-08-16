##一些必须要会的东西##
1. html5标签语义化
	1. header footer nav video audio section aside article
2. cookie和session的区别
	1. cookie是保存在本地的，可以设置过期时间，每次http都会带上cookie的信息；
	2. session是当前会话，窗口关闭后就会被清除掉。 
3. 浏览器渲染的过程
	1. 
4. 浏览器内核
	1. IE Trident
	2. Chrome、Opera Blink
	3. FireFox Gecko
	4. safari webkit
5. 前端优化
	1. 压缩JS CSS
	2. 减少http请求数量（精灵图）
	3. 减少DOM重绘 重计算
	4. CDN
	5. 浏览器缓存
6. 闭包
	1. 闭包是指有权访问另一个函数作用域的函数
	2. 变量常驻内存
	3. 私有化成员属性与方法
7. this
	1. this是在运行时基于函数的执行环境绑定的
8. 原型链
9. Ajax 

    	var xhr=new XMLHttpRequest();
    
    	xhr.onreadystatechange=function(){
     
    	if(xhr.readyState=4){
    
    		if(xhr.status>=200&&xhr.status<300||xhr.status==304){
    			do something
    		}}}
10. 数组去重
