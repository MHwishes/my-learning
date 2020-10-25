## 背景描述

mobile 上点击按钮打开一个modal， modal 的全屏覆盖，宽100%, 高100%.

伪代码如下：

```css
<div class="modal">
 <div class="header">
 我是定高的header, 我的高度是57px
 <div>
 <div class="child">
  <div class="content">
    我是content div
  </div>
 <div>
</div>
```



问题：如何使content div 的高度占除过header 的后父容器的剩余全部高度？（因为要实现content div 中内容的垂直居中，所以希望知道content div 的高度）

### 解决办法：

1. 用 window.innerHeight 获取手机屏幕的高度，然后用flex 布局

   ```css
   .content{
     width: window.innerHeight-57
   }
   .content{
     display: flex;
     flex-direction: column;
     justify-content: center;
   }
   ```

   出现的问题： 浏览器上测试时，切换不同的手机，发现没有垂直居中且出现了滚动条，因为不同的手机屏幕高度不一致，所以window.innerHeight 是不同的值，但代码css 的计算只执行了一次，切换后高度错误，所以导致了问题

2. 另一种解决办法（完美）

   ```css
   .modal{
     display:flex;
     flex-direction:column;
   }
   .child{
     display:flex;
     flex-grow:1; // 这个是关键，当容器modal 除过header后有剩余空间时，child 元素占满剩余空间
   }
   .content{ // 当child 元素占满剩余空间时，content 也就占满了剩余空间，flex的布局的垂直居中也ok了
     display: flex;
     flex-direction: column;
     justify-content: center;
   }
   
   ```

   