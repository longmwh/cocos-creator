[严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)  


严格模式下，参数的值不会随 arguments 对象的值的改变而变化。在正常模式下，对于第一个参数是arg的函数，对arg赋值时会同时赋值给arguments[0],反之亦然（除非没有参数，或者arguments[0]被删除）。在严格模式下，函数的arguments对象会保存函数被调用时的原始参数。  