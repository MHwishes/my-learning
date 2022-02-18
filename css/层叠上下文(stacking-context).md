## 层叠上下文
层叠上下文，英文称作”stacking context”. 是HTML中的一个三维的概念。如果一个元素含有层叠上下文，我们可以理解为这个元素在z轴上就“高人一等”。

层叠上下文，你可以理解为 JS 中的作用域，一个页面中往往不仅仅只有一个层叠上下文(因为有很多种方式可以生成层叠上下文)，在一个层叠上下文内，我们按照层叠水平的规则来堆叠元素。

正常情况下，一共有三种大的类型创建层叠上下文：

1. 默认创建层叠上下文
2. 需要配合 z-index 触发创建层叠上下文
3. 不需要配合 z-index 触发创建层叠上下文

#### 默认创建层叠上下文
默认创建层叠上下文，只有 HTML 根元素，这里你可以理解为 body 标签。它属于根层叠上下文元素，不需要任何 CSS 属性来触发。

#### 需要配合 z-index 触发创建层叠上下文
依赖 z-index 值创建层叠上下文的情况：

+ position 值为 relative/absolute/fixed(部分浏览器)
+ flex 项(父元素 display 为 flex|inline-flex)，注意是子元素，不是父元素创建层叠上下文

Notes:
这两种情况下，需要设置具体的 z-index 值，不能设置 z-index 为 auto，这也就是 z-index: auto 和 z-index: 0 的一点细微差别。
前面我们提到，设置 position: relative 的时候 z-index 的值为 auto 会生效，但是这时候并没有创建层叠上下文，当设置 z-index 不为 auto，哪怕设置 z-index: 0 也会触发元素创建层叠上下文。

#### 不需要配合 z-index 触发创建层叠上下文
这种情况下，基本上都是由 CSS3 中新增的属性来触发的，常见的 请看[MDN 文档](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context#the_stacking_context)

**创建了层叠上下文的元素可以理解局部层叠上下文，它只影响其子孙代元素，它自身的层叠水平是由它的父层叠上下文所决定的。**

## 层叠水平(stacking level)

普通元素的层叠水平优先由层叠上下文决定，因此，层叠水平的比较只有在当前层叠上下文元素中才有意义。

## 层叠顺序
“层叠顺序”英文称作”stacking order”. 表示元素发生层叠时候有着特定的垂直显示顺序，注意，这里跟上面两个不一样，上面的层叠上下文和层叠水平是概念，而这里的层叠顺序是规则。

在CSS2.1的年代，在CSS3还没有出现的时候（注意这里的前提），层叠顺序规则遵循下面这张图：
![image](https://user-images.githubusercontent.com/18116425/154636120-7175f050-a64e-4ae6-acfb-e1ceee9dfda7.png)

## 务必牢记的层叠准则
下面这两个是层叠领域的黄金准则。当元素发生层叠的时候，其覆盖关系遵循下面2个准则：

1. 谁大谁上：当具有明显的层叠水平标示的时候，如识别的z-indx值，在同一个层叠上下文领域，层叠水平值大的那一个覆盖小的那一个。通俗讲就是官大的压死官小的。
2. 后来居上：当元素的层叠水平一致、层叠顺序相同的时候，在DOM流中处于后面的元素会覆盖前面的元素


## 比较两个 DOM 元素显示顺序
1. 如果是在相同的层叠上下文，按照层叠水平的规则来显示元素
2. 如果是在不同的层叠上下文中，先找到共同的祖先层叠上下文，然后比较共同层叠上下文下这个两个元素所在的局部层叠上下文的层叠水平
例子：
 ![image](https://user-images.githubusercontent.com/18116425/154639054-bb19946f-3af9-4c42-b97c-c66ac5df9a1c.png)

页面中常见的 DOM 树大概是长这样：这里 Root、ParentX、ChildX 均为层叠上下文元素，并非一定是 ABCD 的父元素

1. A 元素想跟 B 或者 ChildB 元素比较，很高兴，它们属于相同层叠上下文(ChildB)下，根据层叠水平去判断就可以了
2. 如果 A 元素想跟 C 或者 ChildA 比较，那就去找它们共同的祖先层叠上下文(ParentB)，找到之后，就根据祖先层叠上下文下两个元素所在的局部层叠上下文比较层叠水平(这里就是 ChildA 和 ChildB 去比较)
3. 同理，如果 A 想跟 D 一决雌雄，那么就去找祖先层叠上下文(Root)，然后去比较 ParentA 和 ParentB 的层叠水平即可


## 参考文档
1. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context#the_stacking_context
2. https://www.zhangxinxu.com/wordpress/2016/01/understand-css-stacking-context-order-z-index/
