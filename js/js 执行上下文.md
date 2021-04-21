当 JavaScript 代码执行一段可执行代码(executable code)时，会创建对应的执行上下文(execution context)。

对于每个执行上下文，都有三个重要属性：

- 变量对象(Variable object，VO)

- 作用域链(Scope chain)

- this

  

  VO： 在当前上下文中用来存放值和变量的地方

  GO（Gloable object）：全局上下文中的变量对象就是全局对象呐！

  AO: 在函数私有上下文中，我们用活动对象(activation object, AO)来表示变量对象。

活动对象（AO）和变量对象（VO）其实是一个东西，只是变量对象（VO）是规范上的或者说是引擎实现上的，不可在 JavaScript  环境中访问，只有到当进入一个执行上下文中，这个执行上下文的变量对象才会被激活，所以才叫 activation object  呐，而只有被激活的变量对象，也就是活动对象上的各种属性才能被访问。

### 变量对象创建和执行过程

执行上下文的代码会分成两个阶段进行处理：分析和执行，我们也可以叫做：

1. 进入执行上下文
2. 代码执行

#### 进入执行上下文

变量对象会包括：

1. 函数的所有形参 (如果是函数上下文)

   - 由名称和对应值组成的一个变量对象的属性被创建
   - 没有实参，属性值设为 undefined

2. 函数声明

   - 由名称和对应值（函数对象(function-object)）组成一个变量对象的属性被创建
   - 如果变量对象已经存在相同名称的属性，则完全替换这个属性

3. 变量声明

   - 由名称和对应值（undefined）组成一个变量对象的属性被创建；

   - 如果变量名称跟已经声明的形式参数或函数相同，则变量声明不会干扰已经存在的这类属性

     eg：

     ```js
     function foo(a) {
       var b = 2;
       function c() {}
       var d = function() {};
     
       b = 3;
     
     }
     
     foo(1);
     
     AO 是：
     AO = {
         arguments: {
             0: 1,
             length: 1
         },
         a: 1,
         b: undefined,
         c: reference to function c(){},
         d: undefined
     }
     ```



#### 代码执行

在代码执行阶段，会顺序执行代码，根据代码，修改变量对象的值

```
AO = {
    arguments: {
        0: 1,
        length: 1
    },
    a: 1,
    b: 3,
    c: reference to function c(){},
    d: reference to FunctionExpression "d"
}
```



到这里变量对象的创建过程就介绍完了，让我们简洁的总结我们上述所说：

1. 全局上下文的变量对象初始化是全局对象

2. 函数上下文的变量对象初始化只包括 Arguments 对象

3. 在进入执行上下文时会给变量对象添加形参、函数声明、变量声明等初始的属性值

4. 在代码执行阶段，会再次修改变量对象的属性值

   

### 作用域链

当查找变量的时候，会先从当前上下文的变量对象中查找，如果没有找到，就会从父级(词法层面上的父级)执行上下文的变量对象中查找，函数的作用域在函数 **定义** 的时候就决定了。

```js
var scope = "global scope";
function checkscope(){
    var scope2 = 'local scope';
    return scope2;
}
checkscope();
```

1. checkscope 函数被创建，保存作用域链到 内部属性[[scope]]

   ```js
   checkscope.[[scope]] = [
       globalContext.VO
   ];
   ```

2. 执行 checkscope 函数，创建 checkscope 函数执行上下文，checkscope 函数执行上下文被压入执行上下文栈

   ```js
   ECStack = [
       checkscopeContext,
       globalContext
   ];
   ```

3. checkscope 函数并不立刻执行，开始做准备工作，第一步：复制函数[[scope]]属性创建作用域链

   ```js
   checkscopeContext = {
       Scope: checkscope.[[scope]],
   }
   ```

4. 第二步：用 arguments 创建活动对象，随后初始化活动对象，加入形参、函数声明、变量声明

   ```js
   checkscopeContext = {
       AO: {
           arguments: {
               length: 0
           },
           scope2: undefined
       }，
       Scope: checkscope.[[scope]],
   }
   ```

5. 第三步：将活动对象压入 checkscope 作用域链顶端

   ```js
   checkscopeContext = {
       AO: {
           arguments: {
               length: 0
           },
           scope2: undefined
       },
       Scope: [AO, [[Scope]]]
   }
   ```

6. 准备工作做完，开始执行函数，随着函数的执行，修改 AO 的属性值

   ```js
   checkscopeContext = {
       AO: {
           arguments: {
               length: 0
           },
           scope2: 'local scope'
       },
       Scope: [AO, [[Scope]]]
   }
   ```

7. 查找到 scope2 的值，返回后函数执行完毕，函数上下文从执行上下文栈中弹出

   ```
   ECStack = [
       globalContext
   ];
   ```

 

### This

