

由于所有插件脚本都保证了会在普通脚本之前加载，那么除了用来加载插件，你还可以利用这个特性声明一些特殊的全局变量。你可以在项目中添加这样一个脚本，并且设置“导入为插件”：  


脚本执行顺序： 
* 控制同一个节点上的组件执行顺序：通过组件在属性检查器中的排列顺序来控制。排列在上的组件会先于排列在下的组件执行  
* 设置组件执行的优先级 ：executionOrder 越小，改组件相对其他组件就会越先执行  



__缓动系统（cc.tween）介绍__  
[cc.tween](https://docs.cocos.com/creator/manual/zh/scripting/tween.html)  


__长驻节点__  
在场景切换时不被自动销毁，常驻内存  
    cc.game.addPersistRootNode(myNode);
    cc.game.removePersistRootNode(myNode);//不会立即销毁指定节点，只是将节点还原为可在场景切换时销毁的节点  


__destroy和removeFromParent 的区别__  
调用一个节点的 removeFromParent 后，它不一定就能完全从内存中释放，因为有可能由于一些逻辑上的问题，导致程序中仍然引用到了这个对象。因此如果一个节点不再使用了，请直接调用它的 destroy 而不是 removeFromParent。destroy 不但会激活组件上的 onDestroy，还会降低内存泄露的几率，同时减轻内存泄露时的后果。

总之，如果一个节点不再使用，destroy 就对了，不需要 removeFromParent 也不需要设置 parent 为 null 哈。  
