1. 为什么要有Promise？

   ```js
   doSomething(function(result) {
     doSomethingElse(result, function(newResult) {
       doThirdThing(newResult, function(finalResult) {
         console.log('Got the final result: ' + finalResult);
       }, failureCallback);
     }, failureCallback);
   }, failureCallback);
   ```

  Promise 可以解决回调地狱

2. 什么是Promise？

   本质上 Promise 是一个函数返回的**对象**，我们可以在它上面绑定回调函数，这样我们就不需要在一开始把回调函数作为参数传入这个函数了。

   Eg:

   ```js
   // 成功的回调函数
   function successCallback(result) {
     console.log("音频文件创建成功: " + result);
   }
   // 失败的回调函数
   function failureCallback(error) {
     console.log("音频文件创建失败: " + error);
   }
   createAudioFileAsync(audioSettings, successCallback, failureCallback)
   ```

   如果函数 `createAudioFileAsync()` 被重写为返回 Promise 的形式，那么我们可以像下面这样简单地调用它：

   ```js
   const promise = createAudioFileAsync(audioSettings); 
   promise.then(successCallback, failureCallback);
   ```

   语法：

   ```js
   new Promise( function(resolve, reject) {...});
   ```

   实际用法：

   ```js
   function search(term) {
     var url = 'http://example.com/search?q=' + term;
     var xhr = new XMLHttpRequest();
     var result;
   
     var p = new Promise(function (resolve, reject) {
       xhr.open('GET', url, true);
       xhr.onload = function (e) {
         if (this.status === 200) {
           result = JSON.parse(this.responseText);
           resolve(result);
         }
       };
       xhr.onerror = function (e) {
         reject(e);
       };
       xhr.send();
     });
   
     return p;
   }
   
   search('Hello World').then(console.log, console.error);
   ```

   

3. Promise 内部是如何实现的？

   规范: https://www.ituring.com.cn/article/66566#

