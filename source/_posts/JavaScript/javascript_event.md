---
title: JavaScript Event
date: 2020.3.15
tag: JavaScript
abbrlink: 342ca1f
---

# 背景
&emsp;众所周知，我们的世界处于动态之中，我们身边在无时无刻不发生一些变化。在web世界中，当我们让一些元素的状态发生改变时，会引发“事件”。
<!--more-->
## JavaScript事件
### JavaScript Event 示意图
{% asset_img javascript_event.png javascript event %}

#### 事件流：描述从页面接收事件的次序
* 事件冒泡（event bubbling）
> 由嵌套层次最深节点元素（具体事件发生元素）接收，然后向上级元素传播到不具体元素。
* 事件捕获（event capturing）
> 由不具体元素到具体元素传播。
#### 事件处理程序：事件发生后响应的处理函数（方法）
* HTML事件处理程序
> 在HTML文档内部为指定元素赋予事件处理程序。
> 例如：在input元素中直接调用事件处理程序。
* DOM0级事件处理程序
> 在script tag中为元素节点绑定事件处理程序

    element.onclick = function(){statements;}
    
* DOM2级事件处理程序
> 应用事件监听程序为元素节点绑定事件处理程序。

    element.addEventListener("click", function,usecapture)

#### 事件委托（事件代理）
> 利用事件冒泡，只指定一个事件处理程序，可管理某一类型的所有事件。
> 事件代理可有效减少对DOM文档的操作，在父元素中统一执行子元素中某一类型的事件，可大大优化运行性能。

* 举例
&emsp;页面上有这么一个节点树，div>ul>li>a;比如给最里面的a加一个click点击事件，那么这个事件就会一层一层的往外执行，执行顺序a>li>ul>div。

&emsp;有这样一个机制，给最外面的div加点击事件，那么里面的ul，li，a做点击事件的时候，都会冒泡到最外层的div上，所以都会触发，这就是事件委托，委托它们父级代为执行事件。
