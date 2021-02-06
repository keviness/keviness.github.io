<<<<<<< HEAD
---
title: CSS Flex
date: 2020.3.16
tags:
  - CSS
  - Flex
abbrlink: 2230ef59
---
# 背景
&emsp;我们经常需要对web页面的元素进行布局，在现代浏览器中，Flex功能强大，应用十分广泛，以下是一些个总结：
<!--more-->
## CSS Flex
> Flexible Box
### Flex示意图
{% asset_img CSSFlex.png CSS flex %}
#### 1，任何容器都可指定为flex布局(webkit内核浏览器应加前缀-webkit)
~~~css
    .block_box{display:flex}
    .inline_box{display:inline-flex}
~~~
#### 2，flex布局之后：子元素float,clear,vertical-align将失效。
***
### 一，容器属性
#### 1，容器内项目排列属性
~~~css
    flex-direction: row(default) | row-recerse |colum | colum-reverse
    flex-wrap: nowrap | wrap | wrap-reverse
    flex-flow: flex-direction || flex-wrap
~~~
#### 2，容器内项目在主轴对齐方式
~~~css
    justify-content: flex-start | flex-end | center | space-around | space-between
~~~
#### 3，容器内项目在交叉轴的对齐方式
~~~css
    align-items: flex-start | flex-end | baseline | stretch
~~~
#### 4，定义多样轴线对齐方式
~~~css
    align-content: flex-start | flex-end | center | stretch | space-between | space-around
~~~
### 二，项目属性
* ord: 定义排列顺序
~~~css
    .item{ord:integer}
~~~
* flex-grow：定义放大比例（default:0）
~~~css
    .item{flex-grow:integer}
~~~
* flex-shrink：定义缩小比例（default:1）
~~~css
    .item{flex-shrink:integer}
~~~
* flex-basis：定义项目占据主轴空间
~~~css
    .item{flex-basis:integer | auto}
~~~
* flex：混合定义
~~~css
    .item{flex: flex-grow | flex-shrink | flex-basis}
~~~
### 三，align-self
允许单个项目与其他项目相比有不一样的对齐方式
> 与align-items属性相似，如无父元素，等同于stretch
~~~css
    align-self: auto | flex-start | flex-end | flex-center | baseline | stretch
~~~
***
### 参考
=======
---
title: CSS Flex
date: 2020.3.16
tags:
  - CSS
  - Flex
abbrlink: 2230ef59
---
# 背景
&emsp;我们经常需要对web页面的元素进行布局，在现代浏览器中，Flex功能强大，应用十分广泛，以下是一些个总结：
<!--more-->
## CSS Flex
> Flexible Box
### Flex示意图
{% asset_img CSSFlex.png CSS flex %}
#### 1，任何容器都可指定为flex布局(webkit内核浏览器应加前缀-webkit)
~~~css
    .block_box{display:flex}
    .inline_box{display:inline-flex}
~~~
#### 2，flex布局之后：子元素float,clear,vertical-align将失效。
***
### 一，容器属性
#### 1，容器内项目排列属性
~~~css
    flex-direction: row(default) | row-recerse |colum | colum-reverse
    flex-wrap: nowrap | wrap | wrap-reverse
    flex-flow: flex-direction || flex-wrap
~~~
#### 2，容器内项目在主轴对齐方式
~~~css
    justify-content: flex-start | flex-end | center | space-around | space-between
~~~
#### 3，容器内项目在交叉轴的对齐方式
~~~css
    align-items: flex-start | flex-end | baseline | stretch
~~~
#### 4，定义多样轴线对齐方式
~~~css
    align-content: flex-start | flex-end | center | stretch | space-between | space-around
~~~
### 二，项目属性
* ord: 定义排列顺序
~~~css
    .item{ord:integer}
~~~
* flex-grow：定义放大比例（default:0）
~~~css
    .item{flex-grow:integer}
~~~
* flex-shrink：定义缩小比例（default:1）
~~~css
    .item{flex-shrink:integer}
~~~
* flex-basis：定义项目占据主轴空间
~~~css
    .item{flex-basis:integer | auto}
~~~
* flex：混合定义
~~~css
    .item{flex: flex-grow | flex-shrink | flex-basis}
~~~
### 三，align-self
允许单个项目与其他项目相比有不一样的对齐方式
> 与align-items属性相似，如无父元素，等同于stretch
~~~css
    align-self: auto | flex-start | flex-end | flex-center | baseline | stretch
~~~
***
### 参考
>>>>>>> a7c4693 (Update: blog)
* [阮一峰：Flex布局教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)