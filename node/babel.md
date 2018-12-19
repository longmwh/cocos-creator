
# babel

[babel文档](https://babeljs.io/docs/en/6.26.3/index.html)  
需要将代码从ES6转换为ES5格式，来使用uglifyjs混淆打包

## Babel 转码器
Babel 是一个广泛使用的ES6转码器，可以将ES6代码转为ES5代码，从而在现有的环境运行，  
例如：  
    // 转码前  
    input.map(item => item + 1);

    // 转码后  
    input.map(function (item) {
    return item + 1;
    });

 上面的原始代码用了箭头函数，Babel 将其转为普通函数，就能在不支持箭头函数的 JavaScript 环境执行了。  


