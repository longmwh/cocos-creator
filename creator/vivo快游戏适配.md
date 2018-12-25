## vivo 快游戏适配

[vivo快游戏文档](https://jerrymoon.github.io/)  

适配过程中遇到的最大的问题是一开始无法真机调试，  
当时按照文档  [chrome浏览器真机调试](http://minigame.vivo.com.cn/documents/lesson/debug.html#chrome%E6%B5%8F%E8%A7%88%E5%99%A8%E7%9C%9F%E6%9C%BA%E8%B0%83%E8%AF%95)  
中写的一步一步都对过，可是还是连接不上，在电脑中的 chrome上面显示“Debugging connection was closed.Reason:websocket_closed Recconnect when ready by reopening DevTools.”  
当时去问vivo的程序对接人员，就问我手机ip能不能ping通，然后给了我一个新的小游戏引擎安装包，可是还是不行，  

后来换了 vivo小游戏引擎20181027版本的就可以了（之前用的是20181210更新的版本），也不知道为什么....  

感觉还是老版本的会稳定一些，之前一直想这新版本功能支持的多，所以就一直用新版本。  
不过经过这件事情后，发现，有的时候新版的软件不行，可以去试一试老版的。毕竟老版的还存在，就有意义  

中间也了解了一些知识：  
1.手机IP可以从设置中的wifi模块获取  
2.在vivo小游戏中，cc.sys.isNative获取到的是true，判断为native版本  

    var loc = cc.sys.isNative ? gl.getUniformLocation(program, "CC_MVPMatrix") : gl.getUniformLocation(program, "CC_MVMatrix");

    WebGLRenderingContext.getUniformLocation();返回uniform变量的指针位置

导致后面矩阵计算错误，球的位置也就错了