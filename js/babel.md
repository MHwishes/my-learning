> 相关学习文档：
+ https://zhuanlan.zhihu.com/p/43249121
+ https://www.babeljs.cn/docs/
### 1. babel 是什么？
javascript的编译器，可以将ES6代码转为ES5代码，从而在现有环境执行。就像其他编译器一样，编译过程分为三个阶段：解析、转换和生成。
babel可以做：
+ 语法转换
+ 通过 Polyfill 方式在目标环境中添加缺失的特性 (通过 @babel/polyfill 模块),Babel默认只转换新的JavaScript句法（syntax），而不转换新的API，ES6在Array对象上新增了`Array.from`方法。Babel就不会转码这个方法。如果想让这个方法运行，必须使用`babel-polyfill`，为当前环境提供一个垫片。
+ 源码转换 (codemods)

### 2. babel 插件
babel 本身不具有任何转化功能，它把转化的功能都分解到一个个 plugin 里面。因此当我们不配置任何插件时，经过 babel 的代码和输入是相同的。
插件分为两种：
+ 语法插件：当我们添加 语法插件 之后，在`解析`这一步就使得 babel 能够解析更多的语法。(顺带一提，babel 内部使用的解析类库叫做 babylon，并非 babel 自行开发)
+ 转译插件: 当我们添加之后，在转换这一步把源码转换并输出。这也是我们使用 babel 最本质的需求。
eg:转译插件其实更好理解，比如箭头函数 `(a) => a` 就会转化为 `function (a) {return a}`。完成这个工作的插件叫做 `babel-plugin-transform-es2015-arrow-functions。`

同一类语法可能同时存在语法插件版本和转译插件版本。如果我们使用了转译插件，就不用再使用语法插

### 3. preset
因为es2015 是一套规范，包含大概十几二十个转译插件。如果每次要开发者一个个添加并安装，配置文件很长不说，npm install 的时间也会很长，为了解决这个问题，babel 还提供了一组插件的集合
preset 分为以下几种：

+ 官方内容，目前包括 env, react, flow, minify 等。这里最重要的是 env，后面会详细介绍。
+ stage-x，这里面包含的都是当年最新规范的草案，每年更新。
这里面还细分为
  + Stage 0 - 稻草人: 只是一个想法，经过 TC39 成员提出即可。
  + Stage 1 - 提案: 初步尝试。
  + Stage 2 - 初稿: 完成初步规范。
  + Stage 3 - 候选: 完成规范和浏览器初步实现。
  + Stage 4 - 完成: 将被添加到下一年度发布。

### 4.执行顺序
+ Plugin 会运行在 Preset 之前。
+ Plugin 会从前到后顺序执行。
+ Preset 的顺序则 刚好相反(从后向前)。

preset 的逆向顺序主要是为了保证向后兼容，因为大多数用户的编写顺序是 ['es2015', 'stage-0']。这样必须先执行 stage-0 才能确保 babel 不报错。因此我们编排 preset 的时候，也要注意顺序，其实只要按照规范的时间顺序列出即可。

### 5. env
env 的核心目的是通过配置得知目标环境的特点，然后只做必要的转换。

### 6. babel 的入口
+ babel-cli：可以在命令行使用babel命令来转义文件
+ babel-node: 允许命令行使用babel-node 直接转义+node 文件
+ babel-register: 改写require命令，为其加载的文件进行转码，不对当前文件转码，只适用于开发环境
+ babel-polyfill： 为所有的API增加兼容性的方法，缺点：一是打出来的包非常大，因为 babel-polyfill 是一个整体，把所有方法都加到原型链上。比如我们只使用了 Array.from，但它把 Object.defineProperty 也给加上了，这就是一种浪费了。这个问题可以通过单独使用 core-js 的某个类库来解决，core-js 都是分开的。二是污染全局变量，给很多类的原型链上都作了修改，如果我们开发的也是一个类库供其他开发者使用，这种情况就会变得非常不可控。
+ babel-runtime 和 babel-plugin-transform-runtime：把帮助类方法每次使用前统一改为require,精简代码。babel-runtime 需要安装为依赖而不是开发依赖
+ babel-loader:使用webpack作为loader在代码混淆之前进行代码转换

### 7. babel-7
+ preset 的变更：淘汰 es201x，删除 stage-x，强推 env (重点)
+ npm package 名称的变化，把所有 babel-* 重命名为 @babel/*
+ 不再支持低版本 node，要求 nodejs >= 6 
+ only 和 ignore 匹配规则的变化
+ @babel/node 从 @babel/cli 中独立了，如果要使用 @babel/node，就必须单独安装，并添加到依赖中。

### 8.babel-upgrade
它的目的是帮助用户自动化地从 babel 6 升级到 7。
```
# 不安装到本地而是直接运行命令，npm 的新功能
npx babel-upgrade --write

# 或者常规方式
npm i babel-upgrade -g
babel-upgrade --write
```

