

[闭包](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)  

__闭包__  
闭包是由函数以及创建该函数的词法环境组合而成。这个环境包含了这个闭包创建时所能访问的所有局部变量。  

	function makeAdder(x){
		return function(y){
			return x+y;
		};
	}

	var add5 = makeAdder(5);
	var add10 = makeAdder(10);

	console.log(add5(2));
	console.log(add10(2));


从本质上讲，makeAdder 是一个函数工厂 — 他创建了将指定的值和它的参数相加求和的函数。在上面的示例中，我们使用函数工厂创建了两个新函数 — 一个将其参数和 5 求和，另一个和 10 求和。


使用：  
*使用闭包当函数工厂  
*用闭包模拟私有方法--实现数据隐藏和封装  

