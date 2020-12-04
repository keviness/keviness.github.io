---
title: CSS样式表的引入
date: 2020.4.7
tag: CSS
abbrlink: '7e016094'
---
# 背景
&emsp;要对HTML中的各种元素进行渲染，让页面充满生机，CSS是不二的选择。CSS是web页面中的肌肤，好的CSS渲染可是一件了不得的艺术品。要对CSS进行渲染首当其冲的问题是在HTML中对CSS进行引入，以下是一些个引入方法：
<!--more-->
## css样式表的引入
### 内嵌样式表
> 内嵌样式表是写在Tag(标签)里面的。内嵌样式只对所在的Tag有效 (若有多种样式，内嵌式会覆盖其它的样式)。
~~~html
    <p style="font-size:20px; color:red"></p>
~~~
>这个style定义p标签里面的文字 是20px字体，字体颜色是红色。

### 内部样式表
> 内部样式表是写在HTML的head标签里面的，内部样式表只对所在的网页有效。
>内部样式表要用到style标签，如下 ：
~~~html
    <style  type="text/css">
        div{
            color : red;
        }
    </style>
~~~

### 外部样式表
>若很多网页需要用到同样的样式，此时需要用外部样式表。
>外部样式表需要将样式写在一个css文件中,然后在页面中用link标签引入，在需要应用该样式的每个页面中引入该文件。
>rel="stylesheet" type="text/css" 是固定写法不可修改。
~~~html
    <html>
    <head>
        <link href="./css/example.css " rel ="stylesheet" type="text/css ">
    </head>
    <body>…</body>
    </html>
~~~
