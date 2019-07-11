[Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises)  

本质上：Promise是一个绑定了回调的对象，而不是将回调传进函数内部  







////////////////////////////////////////////////////////////////////////////////////////////  

[Promise构造函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)  
Promise对象用于表示一个异步操作的最终状态（完成或失败），以及该异步操作的结果值。  

__语法__  
    new Promise(function(resolve,reject){...} /*executor*/ );  

__参数__  
_executor_  
executor是带有*resolve*和*rejects*两个参数的函数。Promise构造函数执行时立即调用executor函数，*resolve*和*reject*两个函数
作为参数传递给executor（executor函数在Promise构造函数返回所建Promise实例对象前被调用）。*resolve*和*reject*被调用时，分别将
promise的状态改为fulfilled（完成）或rejected（失败）。executor 内部通常会执行一些异步操作，一旦异步操作执行完毕(可能成功/失败)，
要么调用resolve函数来将promise状态改成fulfilled，要么调用reject 函数将promise的状态改为rejected。如果在executor函数中抛出一个
错误，那么该promise 状态为rejected。executor函数的返回值被忽略。  

