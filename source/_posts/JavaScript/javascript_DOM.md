---
title: JavaScript DOM
date: 2020.3.14
tag: JavaScript
author: keviness
abbrlink: a3b68a60
---
# 背景
&emsp;JavaScript DOM是JavaScript核心模型之一，是DOMcore的重要表现之一，它是用JavaScript进行前端开发的原生技术，是“祖先”级别的方法，以下是一些个总结：
<!--more-->
## JavaScript DOM
> DOM Document Object Model
* DOM是JavaScript核心模型之一，它也是DOMcore的重要表现之一。
* DOM实质应用表现为一个DOM节点树，除html根元素之外，都有父元素，且每个元素仅有一个父元素。
### DOM重要点：
#### 访问节点树
~~~js
    object.getElementById()
    object.getElementsByClassName()
    object.getElementsByTagName()
    object.getElementsByName()
~~~
#### 操作节点
~~~js
    document.createElement()
    document.createTextNode()
    object.appendChild()
    object.insertBefore()
    object.removeChild()
    object.cloneNode(true/false)
    object.replace(newNode, oldNode)
~~~
*** 
#### 操作节点属性
##### 位置信息
~~~js
    parentNode  
    childNode
    firstNode   
    lastNode
    previousSibling     
    nextSibling
~~~
##### 节点属性信息
~~~js
    attributes
    nodeType
    nodeName
    nodeValue
    innerHTML
    innerText
~~~