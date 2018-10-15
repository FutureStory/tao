# Javascript 划重点(ES5)

## 变量的作用域是如何限定的呢？

变量的作用域是该变量声明语句所在的 __function__。

    a = 1;
    function(){
        var b = 1;
    }
    if(true){
        var c = 1;
    }

    console.log(a + b); //Error: b is undefined
    console.log(a + c); //Success: 2

## Javascript有模块的概念吗？

原生Javascript没有模块的概念，大神们耐不住寂寞，制定了一些规则并基于规则开发了一些库实现了模块的概念。

### 1. CommonJS

使用时同步加载模块的特性决定了此规范更适用于服务端。比如Node  

模块的定义：一个文件为一个模块，通过module.exports将内容公开出来  

    // person.js
    module.exports.Person = {
        Name : "yingzheng",
        SayHi : function(){
            console.log("hi");
        }
    };

模块的引用：require方法

    var person = require("person.js");
    console.log(person.Name);

Node设计遵循了commonjs的规范，因此允许我们以commonjs的规则来声明和使用模块。  
commonjs推荐我们在模块使用时使用require同步加载模块，模块加载时会发生IO阻塞，因此commonjs规则更适用于服务端，在客户端性能太低。

### 2. AMD/CMD

提前异步加载模块的特性使得浏览器端性能更高。

## 如何写出类似面向对象的代码呢？