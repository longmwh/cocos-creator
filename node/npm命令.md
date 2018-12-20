
[npm命令介绍](http://www.runoob.com/nodejs/nodejs-npm.html)  

npm install moduleName  #安装模块到项目目录下  

npm install -g moduleName # -g的意思是将模块安装到全局，具体安装到那个位置，要看npm config prefix的位置  

npm install -save moduleName # -save 的意思是将模块安装到项目目录下，并在package文件的dependencies节点写入依赖。  

npm install -save-dev moduleName #-save-dev 的意思是将模块安装到项目目录下，并在package文件的devDependencies节点写入依赖  



npm install express   #本地安装  
npm install express -g #全局安装

#### 本地安装  
1.将安装包放在./node_modules下（运行npm命令时所在的目录），如果没有node_modules 目录，会在当前执行npm命令的目录下生成node_modules目录  
2.可以通过require()来引入本地安装的包  

#### 全局安装  
1.将安装包放在/user/local下，或者你的node的安装目录(如：C:\Program Files\nodejs)下  
2.可以通过require()来引入本地安装的包  


#####关于 package.json  
package.json 位于模块的目录下，用于定义包的属性
