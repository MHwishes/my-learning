1. z- index:  only works on positioned elements (position: absolute, position: relative, position: fixed, or position: sticky) and flex items (elements that are direct children of [display:flex](https://www.w3schools.com/cssref/pr_class_display.asp) elements).

2. *box-sizing*: 属性定义了 [user agent](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) 应该如何计算一个元素的总宽度和总高度。

   - `content-box` 是默认值。如果你设置一个元素的宽为100px，那么这个元素的内容区会有100px 宽，并且任何边框和内边距的宽度都会被增加到最后绘制出来的元素宽度中。

   - `border-box` 告诉浏览器：你想要设置的边框和内边距的值是包含在width内的。也就是说，如果你将一个元素的width设为100px，那么这100px会包含它的border和padding，内容区的实际宽度是width减去(border + padding)的值。大多数情况下，这使得我们更容易地设定一个元素的宽高。

     **译者注:** `border-box`不包含`margin`

