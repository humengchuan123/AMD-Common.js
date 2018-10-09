# AMD-Common.js
JS模块化知识总结

如果你听过js模块化这个东西，那么你就应该听过或CommonJS或AMD甚至是CMD



一、CommonJS
 
 CommonJS就是为JS的表现来制定规范，因为js没有模块的功能所以CommonJS应运而生，
 它希望js可以在任何地方运行，不只是浏览器中。
 
 CommonJS能有一定的影响力，我觉得绝对离不开Node的人气，Node，CommonJS，
 CommonJS定义的模块分为:{模块引用(require)} {模块定义(exports)} {模块标识(module)}
 
require()用来引入外部模块；exports对象用于导出当前模块的方法或变量，
唯一的导出口；module对象就代表模块本身。

比如：
//sum.js
 exports.sum = function(){...做加操作..};

 //calculate.js
 var math = require('sum');
 exports.add = function(n){
     return math.sum(val,n);
 };
 
 
 虽说Node遵循CommonJS的规范，但是相比也是做了一些取舍，填了一些新东西的。
 
不过，说了CommonJS也说了Node，那么我觉得也得先了解下NPM了。
NPM作为Node的包管理器，不是为了帮助Node解决依赖包的安装问题，
那它肯定也要遵循CommonJS规范，它遵循包规范（还是理论）的。
 
CommonJS WIKI讲了它的历史，还介绍了modules和packages等。


二、AMD
 
CommonJS是主要为了JS在后端的表现制定的，
 
这需要分析一下浏览器端的js和服务器端js都主要做了哪些事
AMD(异步模块定义)出现了，它就主要为前端JS的表现制定规范。
 
AMD就只有一个接口：define(id?,dependencies?,factory);
 
它要在声明模块的时候制定所有的依赖(dep)，并且还要当做形参传到factory中，像这样：
 
 
 
1 define(['dep1','dep2'],function(dep1,dep2){...});
 
 
要是没什么依赖，就定义简单的模块，下面这样就可以啦：
 
 
 
1 define(function(){
2     var exports = {};
3     exports.method = function(){...};
4     return exports;
5 });
 
 
这里有define，把东西包装起来，那Node实现中怎么没看到有define关键字，
它也要把东西包装起来，其实，只是Node隐式包装了而已.....
 
RequireJS就是实现了AMD规范的。
 
这有AMD的WIKI中文版，讲了很多蛮详细的东西，用到的时候可以查看：AMD的WIKI中文版
 
 
 
三、CMD
 
大名远扬的玉伯写了seajs，就是遵循他提出的CMD规范，与AMD蛮相近的，
不过用起来感觉更加方便些，最重要的是中文版，应有尽有：seajs官方doc
 
 
 
1 define(function(require,exports,module){...});

