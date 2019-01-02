## JS 中的继承

    var A = function(){
        this._a = 0;
        this._a2 = "a2";
    }

    A.prototype.aPrint = function(){
        console.log("a print",this._a);
    }

    var B = function(){
        A.call(this);
        this._a = 1;
    }
    B.prototype.bPrint = function(){
        A.prototype.aPrint.call(this);
        console.log("b print",this._a);
        console.log("b print:",this._a2);
    }


    var bObj = new B();
    bObj.bPrint();

输出 a print 1
    b print 1
    b print: a2

在B的对象中有A对象中的 _a和_a2属性，B中重新定义了_a会覆盖A中定义的_a  
在子构造函数中，通过调用父构造函数的call方法来实现继承，


[call](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)  

###call()方法调用一个函数，其具有一个指定的this值和 参数列表  

    function Product(name, price) {
    this.name = name;
    this.price = price;
    }

    function Food(name, price) {
    Product.call(this, name, price);
    this.category = 'food';
    }

    console.log(new Food('cheese', 5).name);

// expected output: "cheese"

语法：fun.call(thisArg,arg1,arg2,....)  

call()允许为不同的对象分配和调用属于一个对象的函数/方法  

call()提供新的this值给当前调用的函数/方法。你可以使用call来实现继承：写一个方法，然后让另外一个新的对象来继承它(而不是在新的对象中再写一次这个方法)  

示例：  

1.使用call方法调用匿名函数  

    var animals = [
    { species: 'Lion', name: 'King' },
    { species: 'Whale', name: 'Fail' }
    ];

    for (var i = 0; i < animals.length; i++) {
        (function(i) {
            this.print = function() {
            console.log('#' + i + ' ' + this.species
                    + ': ' + this.name);
                }
            this.print();
        }).call(animals[i], i);
    }

2.使用call方法调用函数并且指定上下文的“this”

    function greet() {
        var reply = [this.animal, 'typically sleep between', this.sleepDuration].join(' ');
        console.log(reply);
    }

    var obj = {
        animal: 'cats', sleepDuration: '12 and 16 hours'
    };

    greet.call(obj);  // cats typically sleep between 12 and 16 hours

greet.call(obj)中调用greet函数时，greet函数中的this会是obj对象  
如果没有传递obj那么greet中this的值将会是greet函数所在作用域的this  

