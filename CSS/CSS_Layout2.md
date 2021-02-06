<<<<<<< HEAD
---
title: CSS Layout 之三栏布局实现
date: 2020.3.18
tags:
  - CSS
  - layout
abbrlink: '57483283'
---
# 背景
&emsp;三栏布局和两栏布局一样，是经典的web布局方法，以下介绍四种实现三栏布局的常用方法：
<!--more-->
### 实现三栏布局（网页宽度自适应）
#### 一，absolute绝对定位法（main置于中间）
HTML代码:
~~~html
    <body>
        <div id="left"></div>
        <div id="main"></div>
        <div id="right"></div>
    </body>
~~~
*** 
CSS:
~~~css
    #left, #right{
        position:absolute;
        top:0;
        height:100%;
        width:200px;
    }
    #left{
        left:0;
    }
    #right{
        right:0;
    }
    #main{
        margin: 210px;
    }
~~~
*** 
#### 二，magrin负值法（negative margin）
HTML代码：main要用双重嵌套标签。
~~~html
    <body>
        <div id="main">
            <div id="body"></div>
        </div>
        <div id="left"></div>
        <div id="right"></div>
    </body>
~~~
***
CSS:
~~~css
    #main{
        width:100%;
        height:100%;
        float:left;
    }
    #main #body{
        margin:0 210px;
        height:100%;
    }
    #left, #right{
        width:200px;
        height:100px;
        float:float;
    }
    #left{
        margin-left: -100%;
    }
    #right{
        margin-right: -200px;
    }
~~~
***
#### 三，float自身浮动法
HTML代码：main放于最后。
~~~html
    <body>
        <div id="left"></div>
        <div id="right"></div>
        <div id="main"></div>
    </body>
~~~
***
CSS：
~~~css
    #main{
        height:100%;
        margin:0 210px;
    }
    #left, #right{
        right:100%;
        width:200px;
    }
    #left{
        float:left;
    }
    #right{
        float:right;
    }
~~~
***
#### 四，双飞翼布局
HTML代码：
~~~html
    <body>
        <div id="main"></div>
        <div id="sub"></div>
        <div id="extra"></div>
    </body>
~~~
***
##### 法一:（类似方案三）
HTML代码：不变。
*** 
CSS：
~~~css
    body{
        padding:0 230px 0 190px;
    }
    #main{
        float:left;
        width:100%;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
        position:relative;
        left:-190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
        position:relative;
        right:-230px;
    }
~~~
***
##### 法二：在main元素外加一层包装元素。
HTML代码：id="main"元素外加一个盒子，封装为id="main-content"
~~~html
    <div id="main-content">
        <div id="main"></div>
    </div>
~~~
**** 
CSS：
~~~css
    #main{
        float:left;
        width:100%;
    }
    #main-content{
        margin:0 230px 0 190px;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
    }
~~~
***
##### 法三：对main用padding。
HTML代码：不变。
***
CSS：
~~~css
    #main{
        float:left;
        width:100%;
        box-sizing:border-box;
        padding:0 210px 0 190px;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
    }
=======
---
title: CSS Layout 之三栏布局实现
date: 2020.3.18
tags:
  - CSS
  - layout
abbrlink: '57483283'
---
# 背景
&emsp;三栏布局和两栏布局一样，是经典的web布局方法，以下介绍四种实现三栏布局的常用方法：
<!--more-->
### 实现三栏布局（网页宽度自适应）
#### 一，absolute绝对定位法（main置于中间）
HTML代码:
~~~html
    <body>
        <div id="left"></div>
        <div id="main"></div>
        <div id="right"></div>
    </body>
~~~
*** 
CSS:
~~~css
    #left, #right{
        position:absolute;
        top:0;
        height:100%;
        width:200px;
    }
    #left{
        left:0;
    }
    #right{
        right:0;
    }
    #main{
        margin: 210px;
    }
~~~
*** 
#### 二，magrin负值法（negative margin）
HTML代码：main要用双重嵌套标签。
~~~html
    <body>
        <div id="main">
            <div id="body"></div>
        </div>
        <div id="left"></div>
        <div id="right"></div>
    </body>
~~~
***
CSS:
~~~css
    #main{
        width:100%;
        height:100%;
        float:left;
    }
    #main #body{
        margin:0 210px;
        height:100%;
    }
    #left, #right{
        width:200px;
        height:100px;
        float:float;
    }
    #left{
        margin-left: -100%;
    }
    #right{
        margin-right: -200px;
    }
~~~
***
#### 三，float自身浮动法
HTML代码：main放于最后。
~~~html
    <body>
        <div id="left"></div>
        <div id="right"></div>
        <div id="main"></div>
    </body>
~~~
***
CSS：
~~~css
    #main{
        height:100%;
        margin:0 210px;
    }
    #left, #right{
        right:100%;
        width:200px;
    }
    #left{
        float:left;
    }
    #right{
        float:right;
    }
~~~
***
#### 四，双飞翼布局
HTML代码：
~~~html
    <body>
        <div id="main"></div>
        <div id="sub"></div>
        <div id="extra"></div>
    </body>
~~~
***
##### 法一:（类似方案三）
HTML代码：不变。
*** 
CSS：
~~~css
    body{
        padding:0 230px 0 190px;
    }
    #main{
        float:left;
        width:100%;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
        position:relative;
        left:-190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
        position:relative;
        right:-230px;
    }
~~~
***
##### 法二：在main元素外加一层包装元素。
HTML代码：id="main"元素外加一个盒子，封装为id="main-content"
~~~html
    <div id="main-content">
        <div id="main"></div>
    </div>
~~~
**** 
CSS：
~~~css
    #main{
        float:left;
        width:100%;
    }
    #main-content{
        margin:0 230px 0 190px;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
    }
~~~
***
##### 法三：对main用padding。
HTML代码：不变。
***
CSS：
~~~css
    #main{
        float:left;
        width:100%;
        box-sizing:border-box;
        padding:0 210px 0 190px;
    }
    #sub{
        float:left;
        margin-left:-100%;
        width:190px;
    }
    #extra{
        float:left;
        margin-left:-230px;
        width:230px;
    }
>>>>>>> a7c4693 (Update: blog)
~~~