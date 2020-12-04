form一点击提交按钮(submit)必然跳转页面，如果表单的action为空也会跳转到自己的页面，即效果为刷新当前页。

如何阻止form的默认提交事件？

1. 将`<input>`标签内按钮类型从`type="submit"`修改为`type="button"`

2. 表单内的`<button>`未指定类型时，默认的类型为submit，可以显式的修改为`<button type="button">`来阻止表单提交

3. 利用preventDefault()方法

4. 用onclick点击事件来return false

   讲一下表单提交按钮onclick事件：
   `onclick="return true"` 为默认的表单提交事件
   `onclick="return false"`为阻止表单提交事件

   而一般用onclick来调用函数都是没有返回值的，所以一般调用完成后为默认return true;所以才会看到，先处理回调函数后再进行表单提交跳转。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script>
        function func(){
            return false;
        }
    </script>
</head>
<body>
    <form action="">
        <input type="submit" value="button" onclick="return func()" /> 
        <!--注意是onclick内是return func();而不是简单的调用func()函数-->
    </form>
</body>
</html>
```

5. 利用**表单**的onsubmit事件

   **onsubmit事件的作用对象为`<form>`，所以把onsubmit事件加在提交按钮身上是没有效果的。**

   form对象的onsubmit事件类似onclick,都是先处理调用的函数，再进行表单是否跳转布尔值的判断
   `onsubmit="return true"` 为默认的表单提交事件
   `onsubmit="return false"`为阻止表单提交事件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script>
        function func(){
            return false;
        }
    </script>
</head>
<body>
    <form action="" onsubmit="return func()">
        <input type="submit" value="button" /> 
    </form>
</body>
</html>
```

