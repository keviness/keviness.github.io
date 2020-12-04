---
title: CSS Layout 之两栏布局实现
date: 2020.3.17
tags:
  - CSS
  - Layout
abbrlink: 493d0ba7
---
# 背景
&emsp;两栏布局是web布局中的经典布局，在布局中的应用十分广泛，以下总结六种常用的CSS两栏布局方法：
<!--more-->
### 实现两栏布局的方法（左侧固定右侧自适应）
~~~html
    <div class="wrap">
    <div class="left">left</div>
    <div class="right">right</right>
    </div>
~~~
#### 一，双inline-block方案
~~~css
    .wrap{font-size:0}
    .left, .right{
        display:inline-block;
        vertical-align:top;
        font-size:14px;
        box-sizing:border-box;
    }
    .right{width:calc(100%-140px)}
~~~
#### 二，双float方案
~~~css
    .wrap{overflow:auto;
        box-sizing:content-box;
    }
    .left, .right{
        float:left;
        box-sizing:border-box;
    }
    .right{
        width:calc(100%-140px);
    }
~~~
#### 三，float + margin-left方案
~~~css
    .wrap{overflow:hidden;}
    .left{float:left;}
    .right{margin-left:150px;}
~~~
#### 四，absolute + margin-left方案
~~~css
    .left{position:absolute;}
    .right{margin-left:150px;}
~~~
#### 五，float + BFC方案
~~~css
    .wrap{overflow:auto;}
    .left{
        float:left;
        margin-left:20px;
    }
    .right{
        margin-left:0;
        overflow:auto; //形成BFC
    }
~~~
#### 六，flex方案
~~~css
    .wrap{
        display:flex;
        align-items:flex-start;
    }
    .left{flex:0 0 auto}
    .right{flex:1 1 auto}
~~~