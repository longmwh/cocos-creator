

//人最重要的就是做事坦荡问心无愧，但万一有愧，就说服自己不要有

[语法和数据类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Grammar_and_types#Guide/Grammar_and_types#%E5%AD%97%E9%9D%A2%E9%87%8F_(Literals))

__变量提升__  
Javascript变量另一个不同寻常的地方是，你可以先使用变量稍后再声明变量而不会引发异常。这一概念称为变量提升;Javascript变量感觉上是被“提升”或移到了函数或语句的最前面。
但是提升后的变量将返回undefined值。因此在使用或引用某个变量之后进行声明和初始化操作，这个被提升的变量仍将返回undefined值。  

    /**
    * 例子1
    */
    console.log(x === undefined); // true
    var x = 3;


    /**
    * 例子2
    */
    // will return a value of undefined
    var myvar = "my value";

    (function() {
    console.log(myvar); // undefined
    var myvar = "local value";
    })();



__全局变量__  
全局变量是全局对象的属性。在网页中，全局对象的window，所以你可以用形如window.variable的语法来设置和访问全局变量.  

__常量（Constants）__  
可以用关键字**const**创建一个只读的常量  
    const PI = 3.14;  
常量不可以通过重新赋值改变其值，也不可以在代码运行时重新声明。它必须被初始化为某个值。  
然而：对象属性被赋值为常量是不受保护的  
    const MY_OBJECT = {"key": "value"};
    MY_OBJECT.key = "otherValue";
2.数组的被定义为常量也是不受保护的  
    const MY_ARRAY = ['HTML','CSS'];
    MY_ARRAY.push('JAVASCRIPT');
    console.log(MY_ARRAY); //logs ['HTML','CSS','JAVASCRIPT'];  



__数据类型__  
最新的 ECMAScript 标准定义了7种数据类型：

六种基本数据类型:
    布尔值（Boolean），有2个值分别是：true 和 false.
    null ， 一个表明 null 值的特殊关键字。 JavaScript 是大小写敏感的，因此 null 与 Null、NULL或变体完全不同。
    undefined ，和 null 一样是一个特殊的关键字，undefined 表示变量未定义时的属性。
    数字（Number），整数或浮点数，例如： 42 或者 3.14159。
    字符串（String），字符串是一串表示文本值的字符序列，例如："Howdy" 。
    *代表（Symbol）* ( 在 ECMAScript 6 中新添加的类型).。一种实例是唯一且不可改变的数据类型。
以及对象（Object）。


__数据类型的转换__  
Javascript是一种动态类型语言（dynamically typed language）


__字符串转换为数字__  

有一些方法可以将内存中表示一个数字的字符串转换为对应的数字。

parseInt()和parseFloat()
参见：parseInt()和parseFloat()的相关页面。

 parseInt 方法只能返回整数，所以使用它会丢失小数部分。另外，调用 parseInt 时最好总是带上进制(radix) 参数，这个参数用于指定使用哪一种进制。

将字符串转换为数字的另一种方法是使用**一元加法运算符**。

    "1.1" + "1.1" = "1.11.1"
    (+"1.1") + (+"1.1") = 2.2   
// 注意：加入括号为清楚起见，不是必需的。

__字面量__  
字面量是由语法表达式定义的常量；或，通过由一定字词组成的语词表达式定义的常量  


__转义字符__  
也可以在换行之前加上反斜线以转义换行（译注：实际上就是一条语句拆成多行书写），这样反斜线和换行都不会出现在字符串的值中。  
    var str = "this string \
    is broken \
    across multiple\
    lines."
    console.log(str);   // this string is broken across multiplelines.
