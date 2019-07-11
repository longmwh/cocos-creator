[Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises)  

本质上：Promise是一个绑定了回调的对象，而不是将回调传进函数内部  







***********************

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

__描述__  
Promise有以下几种状态：  
*pending:初始状态，既不是成功，也不是失败状态  
*fulfilled：意味着操作成功完成  
*rejected：意味着操作失败  


__Promise原型__  
**属性**  
Promise.prototype.constructor  
返回被创建的实例函数. 默认为Promise函数  

__方法__  
Promise.prototype.catch(onRejected)  
添加一个拒绝(rejection) 回调到当前 promise, 返回一个新的promise。当这个回调函数被调用，新 promise 将以它的返回值来resolve，否则如果当前promise 进入fulfilled状态，则以当前promise的完成结果作为新promise的完成结果.  

Promise.prototype.then(onFulfilled, onRejected)  
添加解决（fulfillment）和拒绝（rejection）回调到当前promise，返回一个新的promise，将以回调的返回值来resolve  


Promise.prototype.finally(onFinally)  
添加一个事件处理回调于当前的Promise对象，并且在原Promise对象解析完毕后，返回一个新的Promise对象。回调会在当前Promise运行完毕后被调用，无论当前Promise的状态是完成（fulfilled）还是失败（rejected）  
