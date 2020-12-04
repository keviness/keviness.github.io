---
title: CSS 常见对齐方式
date: 2020.4.2
tag: CSS
abbrlink: d0426352
---
# 背景
&emsp;在对HTML文档进行CSS渲染时，经常需要进行元素的对齐。鉴于此，各种对齐方式总结如下：
<!--more-->
### CSS 水平居中
#### 若子元素为行内元素（inline）
~~~css
    parentNode{
        text-align:center;
    }
~~~
#### 若子元素为块元素（block）
##### 宽度固定 
~~~css
    childNode{
        margin:0 auto;
    }
~~~
##### 宽度不固定
~~~css
    parentNode{
        text-align:center;
    }
    childNode{
        display:inline-block(inline);
    }
~~~
*** 
### CSS垂直居中
#### 若子元素为行内元素（inline）
~~~css
    parentNode{
        height:A px;
    }
    childNode{
        line-heght:A px;
    }
~~~
#### 若子元素为块元素（block）
> 块级元素的高度由内容撑起。
##### 高度未定
~~~css
    parentNode{
        display:table-cell;
        vertical-align:middle;
    }
~~~
##### 高度已定
~~~css
    parentNode{
        height:A px;
    }
    childNode{
        height:B px;
        margin-top/margin-bottom:(A-B)/2px; 
    }
~~~
***
### CSS垂直居中万能语法
~~~css
    parentNode{
        position:relative;
    }
    childNode{
        position:absolute;
        top:50%;
        left:50%;
        width:Xpx;
        height:Ypx;
        margin-top:-(Y/2)px;
        margin-left:-(X/2)px;
    }
~~~
***
### CSS水平垂直居中
#### 水平对齐+行高（子元素为inline元素）
~~~css
    parentNode{
        height:A px;
        text-align:center;
    }
    childNode{
        line-height:A px;
    }
~~~
#### 水平对齐+垂直对齐（子元素为block元素）
~~~css
    parentNode{
        display:table-cell;
        text-align:center;
        vertical-align:center;
    }
    childNode{
        diaplay:inline-block;
    }
~~~
#### relative+absolute（任意元素）
~~~css
    parentNode{
        position:relative;
    }
    childNode{
        position:absolute;
        margin:auto;
    }
~~~