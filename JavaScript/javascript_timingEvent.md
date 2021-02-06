<<<<<<< HEAD
---
title: JavaScript Timing Event
date: 2020.7.11
tags:
  - JavaScript
  - time
  - event
abbrlink: c9819eef
---
# 背景
&emsp;在web编程中，我们经常需要重复一件事，或者让一个操作多次重复执行。JavaSript为我们提供了两个相关函数，这两个函数有共同也有不同之处，以下是一些个总结:
<!--more-->
## 一，总述
>* window 对象允许以指定的时间间隔执行代码，这些时间间隔称为定时事件。
>* `setTimeout(function, milliseconds)`
>* `setInterval(function, milliseconds)`
>* `setTimeout()`只可执行一次该函数，可以通过放在函数中（递归）持续执行该函数。
>* `setInterval()`等同于 `setTimeout()`，但可以持续重复执行该函数。
>* `setTimeout()` 和 `setInterval()`都属于 HTML DOM Window对象的方法。

## 二，setTimeout()
>* `window.setTimeout(function, milliseconds);`
>* `window.setTimeout()`可不带window前缀来编写。
>* 第一个参数是要执行的函数，第二个参数指示执行之前的毫秒数。

### 停止执行clearTimeout() 
>* 停止执行`setTimeout()`中规定的函数。
>* `clearTimeout()`使用从`setTimeout()`返回的变量：
>* `window.clearTimeout(timeoutVariable)`

~~~js
myVar = setTimeout(function, milliseconds);
clearTimeout(myVar);
~~~

### 示例
~~~js
//example1: setTimeout()在函数外
function timedText() {
  setTimeout(myTimeout1, 2000) 
  setTimeout(myTimeout2, 4000) 
  setTimeout(myTimeout3, 6000) 
}
function myTimeout1() {
  document.getElementById("demo").innerHTML = "2 秒";
}
function myTimeout2() {
  document.getElementById("demo").innerHTML = "4 秒";
}
function myTimeout3() {
  document.getElementById("demo").innerHTML = "6 秒";
}

//example2: setTimeout()在函数之内（递归）
function startTime() {
  var today = new Date();
  var h = today.getHours();
  var m = today.getMinutes();
  var s = today.getSeconds();
  m = checkTime(m);
  s = checkTime(s);
  document.getElementById('txt').innerHTML =
  h + ":" + m + ":" + s;
  var t = setTimeout(startTime, 500);
}
function checkTime(i) {
  if (i < 10) {i = "0" + i};  // 在数字 < 10 之前加零
  return i;
~~~

## 三，setInterval()
>* 在每个给定的时间间隔重复给定的函数。
>* `window.setInterval(function, milliseconds);`
>* 第一个参数是要执行的函数。
>* 第二个参数每个执行之间的时间间隔的长度。
>* `window.setInterval()`方法可以不带window前缀。

### 示例
~~~js
//显示当前时间：
//1s=1000ms
var myVar = setInterval(myTimer, 1000);
function myTimer() {
    var d = new Date();
    document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
~~~

### 停止执行clearInterval() 
>* 停止`setInterval()`方法中指定的函数的执行。
>* `window.clearInterval(timerVariable)`
>* `clearInterval()`方法使用从`setInterval()`返回的变量：
~~~js
myVar = setInterval(function, milliseconds);
clearInterval(myVar);
~~~

### 示例
~~~js
<p id="demo"></p>
<button onclick="clearInterval(myVar)">停止时间</button>
var myVar = setInterval(myTimer, 1000);
 function myTimer() {
    var d = new Date();
    document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
=======
---
title: JavaScript Timing Event
date: 2020.7.11
tags:
  - JavaScript
  - time
  - event
abbrlink: c9819eef
---
# 背景
&emsp;在web编程中，我们经常需要重复一件事，或者让一个操作多次重复执行。JavaSript为我们提供了两个相关函数，这两个函数有共同也有不同之处，以下是一些个总结:
<!--more-->
## 一，总述
>* window 对象允许以指定的时间间隔执行代码，这些时间间隔称为定时事件。
>* `setTimeout(function, milliseconds)`
>* `setInterval(function, milliseconds)`
>* `setTimeout()`只可执行一次该函数，可以通过放在函数中（递归）持续执行该函数。
>* `setInterval()`等同于 `setTimeout()`，但可以持续重复执行该函数。
>* `setTimeout()` 和 `setInterval()`都属于 HTML DOM Window对象的方法。

## 二，setTimeout()
>* `window.setTimeout(function, milliseconds);`
>* `window.setTimeout()`可不带window前缀来编写。
>* 第一个参数是要执行的函数，第二个参数指示执行之前的毫秒数。

### 停止执行clearTimeout() 
>* 停止执行`setTimeout()`中规定的函数。
>* `clearTimeout()`使用从`setTimeout()`返回的变量：
>* `window.clearTimeout(timeoutVariable)`

~~~js
myVar = setTimeout(function, milliseconds);
clearTimeout(myVar);
~~~

### 示例
~~~js
//example1: setTimeout()在函数外
function timedText() {
  setTimeout(myTimeout1, 2000) 
  setTimeout(myTimeout2, 4000) 
  setTimeout(myTimeout3, 6000) 
}
function myTimeout1() {
  document.getElementById("demo").innerHTML = "2 秒";
}
function myTimeout2() {
  document.getElementById("demo").innerHTML = "4 秒";
}
function myTimeout3() {
  document.getElementById("demo").innerHTML = "6 秒";
}

//example2: setTimeout()在函数之内（递归）
function startTime() {
  var today = new Date();
  var h = today.getHours();
  var m = today.getMinutes();
  var s = today.getSeconds();
  m = checkTime(m);
  s = checkTime(s);
  document.getElementById('txt').innerHTML =
  h + ":" + m + ":" + s;
  var t = setTimeout(startTime, 500);
}
function checkTime(i) {
  if (i < 10) {i = "0" + i};  // 在数字 < 10 之前加零
  return i;
~~~

## 三，setInterval()
>* 在每个给定的时间间隔重复给定的函数。
>* `window.setInterval(function, milliseconds);`
>* 第一个参数是要执行的函数。
>* 第二个参数每个执行之间的时间间隔的长度。
>* `window.setInterval()`方法可以不带window前缀。

### 示例
~~~js
//显示当前时间：
//1s=1000ms
var myVar = setInterval(myTimer, 1000);
function myTimer() {
    var d = new Date();
    document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
~~~

### 停止执行clearInterval() 
>* 停止`setInterval()`方法中指定的函数的执行。
>* `window.clearInterval(timerVariable)`
>* `clearInterval()`方法使用从`setInterval()`返回的变量：
~~~js
myVar = setInterval(function, milliseconds);
clearInterval(myVar);
~~~

### 示例
~~~js
<p id="demo"></p>
<button onclick="clearInterval(myVar)">停止时间</button>
var myVar = setInterval(myTimer, 1000);
 function myTimer() {
    var d = new Date();
    document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
>>>>>>> a7c4693 (Update: blog)
~~~