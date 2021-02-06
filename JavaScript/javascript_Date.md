<<<<<<< HEAD
---
title: JavaScript Date类型
date: 2020.4.17
tag: JavaScript
abbrlink: b683b12d
---
# 背景
&emsp;时间就是生命，人类每天都需要有一个时间的概念，从而知道自己度过了多久时光。所以我们每天不可避免地要获取有关时间的信息，JavaScript提供了一个很好的获得时间的方法：
<!--more-->
### 创建Date对象
~~~js
    var now = new Date();   
    console.log(now);  //中国标准时间
~~~
### Date解析
>* Date.parse() 传入一个日期格式的字符串，该方法会返回特定的时间格式。
#### 月/日/年
~~~js
    var date = Date.parse("06/07/2017");
    console.log(new Date(date));  
~~~
#### 英文月名 日，年
~~~js
    var date = Date.parse("June 07, 2017");
    console.log(new Date(date));  
~~~
***
### Date.UTC() 
>* 接收7个参数，年，基于0的月，天，时，分，秒以及毫秒数
~~~js
    var date = new Date(2017, 05, 06, 18, 0, 0);
    console.log(new Date.UTC(date)); 
~~~
#### Date.now() 
>* 返回调用该方法时的毫秒数。
****

### Date对象的格式化

* dateObject.toLocaleString() 
>按照与浏览器设置的地区相适应的格式返回日期和时间。

* dateObject.toString() 
>返回带有时区的日期和时间。

* dateObject.valueOf() 
>返回毫秒数
***
### 日期格式化方法

* toDateString() 

>* 以特定于实现的格式显示星期几，月，日和年
>* dateObject.toDateString(); 

* toLocaleDateString() 

>* 以特定于地区的格式显示星期几，月，日和年
>* dateObject.toLocaleDateString();

* toTimeString() 

>* 以特定于实现的格式显示时，分，秒和时区
>* dateObject.toTimeString();  

* toLocaleTimeString() 

>* 以特定于实现的格式显示时，分，秒
>* dateObject.toLocaleTimeString(); 

* toUTCString() 

>* 显示完整的UTC日期
>* dateObject.toUTCString();

***
### 访问Date对象的方法
~~~js
    dateObject.getFullYear() 获取年
    dateObject.getMonth() 获取月
    dateObject.getDate() 获取日
    dateObject.getHours() 获取小时
    dateObject.getMinutes() 获取分钟
    dateObject.getSeconds() 获取秒
=======
---
title: JavaScript Date类型
date: 2020.4.17
tag: JavaScript
abbrlink: b683b12d
---
# 背景
&emsp;时间就是生命，人类每天都需要有一个时间的概念，从而知道自己度过了多久时光。所以我们每天不可避免地要获取有关时间的信息，JavaScript提供了一个很好的获得时间的方法：
<!--more-->
### 创建Date对象
~~~js
    var now = new Date();   
    console.log(now);  //中国标准时间
~~~
### Date解析
>* Date.parse() 传入一个日期格式的字符串，该方法会返回特定的时间格式。
#### 月/日/年
~~~js
    var date = Date.parse("06/07/2017");
    console.log(new Date(date));  
~~~
#### 英文月名 日，年
~~~js
    var date = Date.parse("June 07, 2017");
    console.log(new Date(date));  
~~~
***
### Date.UTC() 
>* 接收7个参数，年，基于0的月，天，时，分，秒以及毫秒数
~~~js
    var date = new Date(2017, 05, 06, 18, 0, 0);
    console.log(new Date.UTC(date)); 
~~~
#### Date.now() 
>* 返回调用该方法时的毫秒数。
****

### Date对象的格式化

* dateObject.toLocaleString() 
>按照与浏览器设置的地区相适应的格式返回日期和时间。

* dateObject.toString() 
>返回带有时区的日期和时间。

* dateObject.valueOf() 
>返回毫秒数
***
### 日期格式化方法

* toDateString() 

>* 以特定于实现的格式显示星期几，月，日和年
>* dateObject.toDateString(); 

* toLocaleDateString() 

>* 以特定于地区的格式显示星期几，月，日和年
>* dateObject.toLocaleDateString();

* toTimeString() 

>* 以特定于实现的格式显示时，分，秒和时区
>* dateObject.toTimeString();  

* toLocaleTimeString() 

>* 以特定于实现的格式显示时，分，秒
>* dateObject.toLocaleTimeString(); 

* toUTCString() 

>* 显示完整的UTC日期
>* dateObject.toUTCString();

***
### 访问Date对象的方法
~~~js
    dateObject.getFullYear() 获取年
    dateObject.getMonth() 获取月
    dateObject.getDate() 获取日
    dateObject.getHours() 获取小时
    dateObject.getMinutes() 获取分钟
    dateObject.getSeconds() 获取秒
>>>>>>> a7c4693 (Update: blog)
~~~