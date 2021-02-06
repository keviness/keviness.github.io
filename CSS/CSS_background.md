<<<<<<< HEAD
---
title: CSS 背景颜色
date: 2020.4.11
tags:
  - CSS
  - background
abbrlink: acbbb184
---
# 背景
&emsp;颜色使我们这个世界色彩纷呈。在web界面中，适宜的颜色让人心旷神怡。那么怎么对CSS颜色进行控制呢？
<!--more-->
## CSS背景
>颜色的应用主要分为前景色、背景色和透明三个部分。

### 前景色
>color | border-color
>* 值: color | inherit
>* 初始值: 用户代理特定的值
>* 应用于: 所有元素
>* 继承性: 有
>* 影响一个元素的前景色，可以使用color属性，也可以使用属性border-color设置边框颜色。

### 透明度
>opacity
>* opacity是CSS3中专门用来设置透明度的一个属性，opacity只能给整个元素设置一个透明度，并且其透明度直接会继承给其后代元素
>* 值: value | inherit
>* value:默认值是1，可以取0-1的任意浮点数。其中，1表示完全不透明，0表示完全透明
>* 继承性: 无

### 背景色
>* 所有背景属性都不能继承
>* 背景色background-color接受所有合法颜色，默认值是transparent。
~~~css
    background-color: red; 
~~~
### 背景图像
>* 背景图像background-image会放在所指定的背景颜色之上，初始值: none
~~~css
    background-image: url("image/img.jpg");
~~~
### 背景平铺
>* 背景平铺的属性值中space和round是CSS3新增的值。
>* space表示背景图像的两端对齐平铺，多出来的空间用空白代替。
>* round表示背景图像的两端对齐平铺，但多出来的空间通过自身拉伸来填充。
>* 值: repeat | repeat-x | repeat-y | no-repeat | space | round | inherit
~~~css
    background-repeat: repeat;
~~~
### 背景定位
>* 背景定位background-position，初始值: 0% 0%
>* 值:  length | left | center | right | top | center | bottom 
~~~css
    background-position: center ;        
    background-position: 10px 20px;  
~~~
### 背景裁切
>* 背景裁切(background-clip)属性用来定义背景图像的裁剪区域。
>* 值：background-clip: padding-box || border-box || content-box
~~~css
    background-clip: content-box;
~~~
### 背景尺寸
>* 使用背景尺寸(background-size)属性可以指定背景图片的尺寸，可以控制背景图片在水平和垂直两个方向的缩放。
~~~css
    background-size: 20px 30px;
=======
---
title: CSS 背景颜色
date: 2020.4.11
tags:
  - CSS
  - background
abbrlink: acbbb184
---
# 背景
&emsp;颜色使我们这个世界色彩纷呈。在web界面中，适宜的颜色让人心旷神怡。那么怎么对CSS颜色进行控制呢？
<!--more-->
## CSS背景
>颜色的应用主要分为前景色、背景色和透明三个部分。

### 前景色
>color | border-color
>* 值: color | inherit
>* 初始值: 用户代理特定的值
>* 应用于: 所有元素
>* 继承性: 有
>* 影响一个元素的前景色，可以使用color属性，也可以使用属性border-color设置边框颜色。

### 透明度
>opacity
>* opacity是CSS3中专门用来设置透明度的一个属性，opacity只能给整个元素设置一个透明度，并且其透明度直接会继承给其后代元素
>* 值: value | inherit
>* value:默认值是1，可以取0-1的任意浮点数。其中，1表示完全不透明，0表示完全透明
>* 继承性: 无

### 背景色
>* 所有背景属性都不能继承
>* 背景色background-color接受所有合法颜色，默认值是transparent。
~~~css
    background-color: red; 
~~~
### 背景图像
>* 背景图像background-image会放在所指定的背景颜色之上，初始值: none
~~~css
    background-image: url("image/img.jpg");
~~~
### 背景平铺
>* 背景平铺的属性值中space和round是CSS3新增的值。
>* space表示背景图像的两端对齐平铺，多出来的空间用空白代替。
>* round表示背景图像的两端对齐平铺，但多出来的空间通过自身拉伸来填充。
>* 值: repeat | repeat-x | repeat-y | no-repeat | space | round | inherit
~~~css
    background-repeat: repeat;
~~~
### 背景定位
>* 背景定位background-position，初始值: 0% 0%
>* 值:  length | left | center | right | top | center | bottom 
~~~css
    background-position: center ;        
    background-position: 10px 20px;  
~~~
### 背景裁切
>* 背景裁切(background-clip)属性用来定义背景图像的裁剪区域。
>* 值：background-clip: padding-box || border-box || content-box
~~~css
    background-clip: content-box;
~~~
### 背景尺寸
>* 使用背景尺寸(background-size)属性可以指定背景图片的尺寸，可以控制背景图片在水平和垂直两个方向的缩放。
~~~css
    background-size: 20px 30px;
>>>>>>> a7c4693 (Update: blog)
~~~