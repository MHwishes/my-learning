> 相关的学习文档：http://es6.ruanyifeng.com/#docs/module

#### 1. 概述

ES6之前的模块加载：
相关的文章：https://juejin.im/post/5a422b036fb9a045211ef789
+ CommonJS：用于服务器node，是一种规范，CommonJS 规范是为了解决 JavaScript 的作用域问题而定义的模块形式，可以使每个模块它自身的命名空间中执行。

+ AMD：用于浏览器，AMD（异步模块定义）是为浏览器环境设计的，因为 CommonJS 模块系统是同步加载的，当前浏览器环境还没有准备好同步加载模块的条件。AMD 定义了一套 JavaScript 模块依赖异步加载标准，来解决同步加载的问题。

ES6 之后：
模块功能module实现,且得相当简单，完全可以取代 CommonJS 和 AMD 规范，成为浏览器和服务器通用的模块解决方案。
#### 2.用法
模块功能主要由两个命令构成：`export`和`import`. export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能。

用法：
```
// 第一组
export default function crc32() { // 输出
  // ...
}

import crc32 from 'crc32'; // 输入

// 第二组
export function crc32() { // 输出
  // ...
};

import {crc32} from 'crc32'; // 输入
```
本质上，export default就是输出一个叫做default的变量或方法，然后系统允许你为它取任意名字。所以下面的用法是正确的

```
// modules.js
function add(x, y) {
  return x * y;
}
export {add as default};
// 等同于
// export default add;

// app.js
import { default as foo } from 'modules';
// 等同于
// import foo from 'modules';
```

#### 3. import和require的区别
+ require:
   + 规范：CommonJS规范	
   + 调用：运行是调，require的引用可以在代码的任何地方。
   + 本质：赋值过程，require的结果就是对象、数字、字符串、函数等，再把require的结果赋值给某个变量

   + 特点：非语言层面的标准。 社区方案，提供了服务器/浏览器的模块加载方案。只能在运行时确定模块的依赖关系及输入/输出的变量，无法进行静态优化
+ import：
   + 规范：es6+的语法标准	
   + 调用：编译时调用，import语法规范上是放在文件开头。
   + 本质：解构过程，目前所有的引擎都还没有实现import，我们在node中使用babel支持ES6，也仅仅是将ES6转码为ES5再执行，import语法会被转码为require
	
   + 特点：语言规格层面支持模块功能。支持编译时静态分析，便于JS引入宏和类型检验。动态绑定
