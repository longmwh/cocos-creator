
[CCClass进阶参考](https://docs.cocos.com/creator/manual/zh/scripting/reference/class.html#serializable)  

*CCClass：使用 cc.Class 声明的类。  
*原型对象：调用 cc.Class 时传入的字面量参数。  
*实例成员：包含“成员变量”和“成员方法”。  
*静态成员：包含“静态变量”和“类方法”。  
*运行时：项目脱离编辑器独立运行时，或者在模拟器和浏览器里预览的时候。  
*序列化：解析内存中的对象，将它的信息编码为一个特殊的字符串，以便保存到硬盘上或传输到其它地方。  


serializable 参数  
__指定default默认值的属性默认情况下都会被序列化，序列化后就会将编辑器中设置好的值保存到场景等资源文件汇中，并且在加载场景时自动还原之前设置好的值。__ 
如果不想序列化，可以设置serializable:false  
    temp_url: {
        default: "",
        serializable: false
    }  


__属性延迟定义__  
如果两个类相互引用，脚本加载阶段就会出现循环引用，循环引用将导致脚本加载出错：  
    Game.js

    var Item = require("Item");

    var Game = cc.Class({
        properties: {
            item: {
                default: null,
                type: Item
            }
        }
    });

    module.exports = Game;
    Item.js

    var Game = require("Game");

    var Item = cc.Class({
        properties: {
            game: {
                default: null,
                type: Game
            }
        }
    });

 module.exports = Item;
上面两个脚本加载时，由于它们在 require 的过程中形成了闭环，因此加载会出现循环引用的错误，循环引用时 type 就会变为 undefined。
因此我们提倡使用以下的属性定义方式：   

    Game.js

    var Game = cc.Class({
        properties: () => ({
            item: {
                default: null,
                type: require("Item")
            }
        })
    });

    module.exports = Game;
    Item.js

    var Item = cc.Class({
        properties: () => ({
            game: {
                default: null,
                type: require("Game")
            }
        })
    });

    module.exports = Item;  

这种方式就是将 properties 指定为一个 ES6 的箭头函数（lambda 表达式），箭头函数的内容在脚本加载过程中并不会同步执行，而是会被 CCClass 以异步的形式在所有脚本加载成功后才调用。因此加载过程中并不会出现循环引用，属性都可以正常初始化。

箭头函数的用法符合 JavaScript 的 ES6 标准，并且 Creator 会自动将 ES6 转义为 ES5，用户不用担心浏览器的兼容问题。

你可以这样来理解箭头函数：  

    // 箭头函数支持省略掉 `return` 语句，我们推荐的是这种省略后的写法：

    properties: () => ({    // <- 箭头右边的括号 "(" 不可省略
        game: {
            default: null,
            type: require("Game")
        }
    })

    // 如果要完整写出 `return`，那么上面的写法等价于：

    properties: () => {
        return {
            game: {
                default: null,
                type: require("Game")
            }
        };      // <- 这里 return 的内容，就是原先箭头右边括号里的部分
    }

    // 我们也可以不用箭头函数，而是用普通的匿名函数：

    properties: function () {
        return {
            game: {
                default: null,
                type: require("Game")
            }
        };
    }