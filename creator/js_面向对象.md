

[适合初学者的Javascript面向对象](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/Object-oriented_JS)  

对象可以包含相关的数据和代码，这些代表现实世界模型的一些信息或者功能，或者它特有的一些行为。对象数据（也经常称为函数）可以有结构存储（官方术语为**封装**）在对象包内（也可以给一个特殊的名字来表示，有时候也叫做命名空间），可以使他容易组织和访问；对象也通常用于存储数据，这样就可以很容易的在网络上传输。  


原型链中的方法和属性没有被复制到其它对象---他们被访问需要通过前面所说的“原型链”的方式  


在原型链上查找属性比较耗时，对性能有副作用，这在性能要求苛刻的情况下很重要。另外，试图访问不存在的属性时会遍历整个原型链。

遍历对象的属性时，原型链上的每个可枚举属性都会被枚举出来。要检查对象是否具有自己定义的属性，而不是其原型链上的某个属性，则必须使用所有对象从 Object.prototype 继承的 hasOwnProperty 方法。下面给出一个具体的例子来说明它：  

    console.log(g.hasOwnProperty('vertices'));
    // true

    console.log(g.hasOwnProperty('nope'));
    // false

    console.log(g.hasOwnProperty('addVertex'));
    // false

    console.log(g.__proto__.hasOwnProperty('addVertex'));
    // true  

*hasOwnProperty*是Javascript中唯一一个处理属性并且不会遍历原型链的方法  
检查属性是否为undefined是不能够检查其是否存在的。该属性可能已存在，但其值恰好被设置成了undefined.  
