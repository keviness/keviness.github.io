---
title: Canvas概述
date: 2020.6.30
tags:
  - JavaScript
  - canvas
abbrlink: 53ec7d50
---
# 背景
&emsp;眨眼之间，2020年已经过去了一半。前端学习的计划还没结束，新的计划就要开始，顿时感觉压力倍增呀。暑假是一个很好的学习时间，希望在这一段时间的“闭关”中，我能够打牢基础，为以后的学习做准备。
&emsp;闲言少叙，除了SVG之外，HTML5新增了canvas绘图利器，在动态展现表格数据方面有着强大的功能。
<!--more-->
## Canvas定义

>* HTML5 canvas标签用于绘制图像。
>* getContext()方法可返回一个对象，该对象提供了用于在画布上绘图的方法和属性。
>* canvas元素创造了一个固定大小的画布，它公开了一个或多个渲染上下文，其可以用来绘制和处理要展示的内容。
>* canvas元素有一个叫做 getContext()的方法，这个方法是用来获得渲染上下文和它的绘画功能。getContext()只有一个参数，上下文的格式。
~~~js
var canvas = document.getElementById('tutorial');
var ctx = canvas.getContext('2d');
~~~

## Canvas绘制常见图形

### 线条
~~~js
beginPath()  //新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。
closePath()  //闭合路径之后图形绘制命令又重新指向到上下文中。
stroke()  //通过线条来绘制图形轮廓。
fill()  //通过填充路径的内容区域生成实心的图形。
lineTo(x, y)  //绘制一条从当前位置到指定x以及y位置的直线。
moveTo(x, y)  //将笔触移动到指定的坐标x以及y上。
~~~

#### 示例
~~~js
//绘制三角形
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext){
  var ctx = canvas.getContext('2d');

  // 填充三角形
  ctx.beginPath();
  ctx.moveTo(25, 25);
  ctx.lineTo(105, 25);
  ctx.lineTo(25, 105);
  ctx.fill();

  // 描边三角形
  ctx.beginPath();
  ctx.moveTo(125, 125);
  ctx.lineTo(125, 45);
  ctx.lineTo(45, 125);
  ctx.closePath();
  ctx.stroke();
  }
}
~~~

###  矩形
~~~js
fillRect(x, y, width, height)  //绘制一个填充的矩形
strokeRect(x, y, width, height)  //绘制一个矩形的边框
clearRect(x, y, width, height)  //清除指定矩形区域，让清除部分完全透明。
~~~

#### 示例
~~~js
//绘制矩形
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    ctx.fillRect(25, 25, 100, 100);
    ctx.clearRect(45, 45, 60, 60);
    ctx.strokeRect(50, 50, 50, 50);
  }
}
~~~

### 圆弧
>* 画一个以（x,y）为圆心的以radius为半径的圆弧（圆），从startAngle开始到endAngle结束，按照anticlockwise给定的方向（默认为顺时针）来生成。
>* arc()函数中表示角的单位是弧度，不是角度。角度与弧度的js表达式:
弧度=(Math.PI/180)*角度。
~~~js
arc(x, y, radius, startAngle, endAngle, anticlockwise)
~~~
#### 示例
~~~js
//绘画一个笑脸
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext){
    var ctx = canvas.getContext('2d');

    ctx.beginPath();
    ctx.arc(75, 75, 50, 0, Math.PI * 2, true); // 绘制
    ctx.moveTo(110, 75);
    ctx.arc(75, 75, 35, 0, Math.PI, false);   // 口(顺时针)
    ctx.moveTo(65, 65);
    ctx.arc(60, 65, 5, 0, Math.PI * 2, true);  // 左眼
    ctx.moveTo(95, 65);
    ctx.arc(90, 65, 5, 0, Math.PI * 2, true);  // 右眼
    ctx.stroke();
  }
}
~~~

### 曲线
~~~js
quadraticCurveTo(cp1x, cp1y, x, y)  //绘制二次贝塞尔曲线，cp1x,cp1y为一个控制点，x,y为结束点。
bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)  //绘制三次贝塞尔曲线，cp1x,cp1y为控制点一，cp2x,cp2y为控制点二，x,y为结束点。
~~~
#### 示例
~~~js
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    // 二次贝塞尔曲线
    ctx.beginPath();
    ctx.moveTo(75, 25);
    ctx.quadraticCurveTo(25, 25, 25, 62.5);
    ctx.quadraticCurveTo(25, 100, 50, 100);
    ctx.quadraticCurveTo(50, 120, 30, 125);
    ctx.quadraticCurveTo(60, 120, 65, 100);
    ctx.quadraticCurveTo(125, 100, 125, 62.5);
    ctx.quadraticCurveTo(125, 25, 75, 25);
    ctx.stroke();
   }
}
~~~

### 文本
~~~js
fillText(text, x, y [, maxWidth]) //在指定的(x,y)位置填充指定的文本，绘制的最大宽度是可选的.
strokeText(text, x, y [, maxWidth])  //在指定的(x,y)位置绘制文本边框，绘制的最大宽度是可选的.
~~~
#### 示例
~~~js
//填充文本
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = "48px serif";
  ctx.fillText("Hello world", 10, 50);
}
//文本边框
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = "48px serif";
  ctx.strokeText("Hello world", 10, 50);
}
~~~