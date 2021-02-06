<<<<<<< HEAD
---
title: JavaScript阻止浏览器默认事件发生
tags:
  - JavaScript
  - HTML
date: 2020.6.8
abbrlink: 7a8ff88c
---
# 背景
&emsp;在JavaScript Event中经常需要对事件进行阻止，主要有以下方法：
&emsp;event.preventDefault()阻止浏览器默认事件。
&emsp;event.stopPropagation()阻止元素事件冒泡。
<!--more-->
## 一，event.preventDefault()
>阻止浏览器默认行为
~~~html
<!DOCTYPE html>
<html>
<head>
    <script type="text/javascript" src="/jquery/jquery.js"></script>
    <script type="text/javascript">
    $(document).ready(function(){
        $("a").click(function(event){
        event.preventDefault();
        });
    });        //event.preventDefault() 方法将防止上面的链接打开 URL
    </script>
</head>
<body>
    <a href="http://w3school.com.cn/">W3School</a>
</body>
</html>  
~~~


## 二，event.stopPropagation()
>阻止元素事件冒泡。
~~~js

    var btn = document.getElementById('myBtn');
    document.onclick = function(){
        alert(1);
    }
    btn.onclick = function(event){
        event.stopPropagation();
    }
~~~
&emsp;这样当点击btn时，绑定在document的事件不会被触发，因为btn的事件冒泡机制被组织了。

## 三，兼容IE浏览器
~~~js
    if (event.stopPropagation){  
        event.stopPropagation();  
    }else{  
        event.cancelBubble=true;  
    }  

    if (event.preventDefault){  
    event.preventDefault();  
    }else{  
        event.returnValue=false;  
    }  
=======
---
title: JavaScript阻止浏览器默认事件发生
tags:
  - JavaScript
  - HTML
date: 2020.6.8
abbrlink: 7a8ff88c
---
# 背景
&emsp;在JavaScript Event中经常需要对事件进行阻止，主要有以下方法：
&emsp;event.preventDefault()阻止浏览器默认事件。
&emsp;event.stopPropagation()阻止元素事件冒泡。
<!--more-->
## 一，event.preventDefault()
>阻止浏览器默认行为
~~~html
<!DOCTYPE html>
<html>
<head>
    <script type="text/javascript" src="/jquery/jquery.js"></script>
    <script type="text/javascript">
    $(document).ready(function(){
        $("a").click(function(event){
        event.preventDefault();
        });
    });        //event.preventDefault() 方法将防止上面的链接打开 URL
    </script>
</head>
<body>
    <a href="http://w3school.com.cn/">W3School</a>
</body>
</html>  
~~~


## 二，event.stopPropagation()
>阻止元素事件冒泡。
~~~js

    var btn = document.getElementById('myBtn');
    document.onclick = function(){
        alert(1);
    }
    btn.onclick = function(event){
        event.stopPropagation();
    }
~~~
&emsp;这样当点击btn时，绑定在document的事件不会被触发，因为btn的事件冒泡机制被组织了。

## 三，兼容IE浏览器
~~~js
    if (event.stopPropagation){  
        event.stopPropagation();  
    }else{  
        event.cancelBubble=true;  
    }  

    if (event.preventDefault){  
    event.preventDefault();  
    }else{  
        event.returnValue=false;  
    }  
>>>>>>> a7c4693 (Update: blog)
~~~