<<<<<<< HEAD
---
title: web storage常用的两种方式
date: 2020.6.27
tags:
  - JavaScript
  - storage
abbrlink: 5b4c752e
---
# 背景
&emsp;数据是网络世界的灵魂，我们浏览网页的根本目的在于获得由数据构成的信息。在HTML5之前，这些都是由cookie完成的。但是cookie不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得cookie速度很慢而且效率也不高。HTML5之后，网页本地存储数据有了新的选择。
<!--more-->
&emsp;HTML5中，数据不是由每个服务器请求传递的，而是只有在请求时使用数据。它使在不影响网站性能的情况下存储大量数据成为可能。

# web本地存储(web storage) 
## 本地存储定义：
>* 存储对象是简单的键值存储，类似于对象。
>* 可以像访问对象一样访问这些值，或者使用`Storage.getItem()`和 `Storage.setItem()`方法。
~~~js
    localStorage.colorSetting = '#a4509b';
    localStorage['colorSetting'] = '#a4509b';
    localStorage.setItem('colorSetting', '#a4509b');
~~~
## 本地存储常用方法
~~~js
    localStorage/sessionStorage.setItem('myCat', 'Tom');  //添加项，加入到本地存储中
    let cat = localStorage/sessionStorage.getItem('myCat'); //获取项的相应值
    localStorage/sessionStorage.removeItem('myCat');  //移除指定项
    localStorage/sessionStorage.clear();  //清空本地所有存储的数据
~~~
## Web Storage包含如下两种：
### sessionStorage 
>`sessionStorage`方法针对一个session进行数据存储。当用户关闭浏览器窗口后，数据会被删除(页面刷新和恢复，存储数据不会清除)。
### sessionStorage应用示例
~~~js
    function clickCounter() {
        if(typeof(Storage) !== "undefined") {
            if (sessionStorage.clickcount) {
                sessionStorage.clickcount = Number(sessionStorage.clickcount)+1;
            } else {
                sessionStorage.clickcount = 1;
            }
            document.getElementById("result").innerHTML = "在本 session中，点击按钮 " + sessionStorage.clickcount + " 次。";
        } else {
            document.getElementById("result").innerHTML = "抱歉！您的浏览器不支持 Web Storage ...";
        }
    }
~~~
### localStorage 
>与`sessionStorage`相似，但`localStorage`是没有时间限制的数据存储，在浏览器关闭，重新打开页面后数据仍然存在。
### localStorage应用示例
~~~js
    if (localStorage.pagecount)
	{
	    localStorage.pagecount=Number(localStorage.pagecount) +1;
	}
    else
	{
	    localStorage.pagecount=1;
	}
    document.write("Visits: " + localStorage.pagecount + " time(s).");
~~~

## StorageEvent（存储事件）
>* 通过`StorageEvent`响应存储的变化
>* `Storage`对象发生变化时（创建/更新/删除数据项时，重复设置相同的键值不会触发该事件，`Storage.clear()`方法至多触发一次该事件），
>* `StorageEvent`事件在同一个页面内发生的改变不会起作用，在相同域名下的其他页面（如一个新标签或 iframe）发生的改变才会起作用。在其他域名下的页面不能访问相同的 `Storage`对象。
>* 这里，我们为window对象添加了一个事件监听器，在当前域名相关的 `Storage`对象发生改变时该事件监听器会触发。改变的数据项的键，改变前的旧值，改变后的新值，改变的存储对象所在的文档的 URL，以及存储对象本身。
~~~js
    window.addEventListener('storage', function(e) {  
        document.querySelector('.my-key').textContent = e.key;
        document.querySelector('.my-old').textContent = e.oldValue;
        document.querySelector('.my-new').textContent = e.newValue;
        document.querySelector('.my-url').textContent = e.url;
        document.querySelector('.my-storage').textContent = e.storageArea;
});
~~~
## 参考
* [MDN web storage](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
=======
---
title: web storage常用的两种方式
date: 2020.6.27
tags:
  - JavaScript
  - storage
abbrlink: 5b4c752e
---
# 背景
&emsp;数据是网络世界的灵魂，我们浏览网页的根本目的在于获得由数据构成的信息。在HTML5之前，这些都是由cookie完成的。但是cookie不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得cookie速度很慢而且效率也不高。HTML5之后，网页本地存储数据有了新的选择。
<!--more-->
&emsp;HTML5中，数据不是由每个服务器请求传递的，而是只有在请求时使用数据。它使在不影响网站性能的情况下存储大量数据成为可能。

# web本地存储(web storage) 
## 本地存储定义：
>* 存储对象是简单的键值存储，类似于对象。
>* 可以像访问对象一样访问这些值，或者使用`Storage.getItem()`和 `Storage.setItem()`方法。
~~~js
    localStorage.colorSetting = '#a4509b';
    localStorage['colorSetting'] = '#a4509b';
    localStorage.setItem('colorSetting', '#a4509b');
~~~
## 本地存储常用方法
~~~js
    localStorage/sessionStorage.setItem('myCat', 'Tom');  //添加项，加入到本地存储中
    let cat = localStorage/sessionStorage.getItem('myCat'); //获取项的相应值
    localStorage/sessionStorage.removeItem('myCat');  //移除指定项
    localStorage/sessionStorage.clear();  //清空本地所有存储的数据
~~~
## Web Storage包含如下两种：
### sessionStorage 
>`sessionStorage`方法针对一个session进行数据存储。当用户关闭浏览器窗口后，数据会被删除(页面刷新和恢复，存储数据不会清除)。
### sessionStorage应用示例
~~~js
    function clickCounter() {
        if(typeof(Storage) !== "undefined") {
            if (sessionStorage.clickcount) {
                sessionStorage.clickcount = Number(sessionStorage.clickcount)+1;
            } else {
                sessionStorage.clickcount = 1;
            }
            document.getElementById("result").innerHTML = "在本 session中，点击按钮 " + sessionStorage.clickcount + " 次。";
        } else {
            document.getElementById("result").innerHTML = "抱歉！您的浏览器不支持 Web Storage ...";
        }
    }
~~~
### localStorage 
>与`sessionStorage`相似，但`localStorage`是没有时间限制的数据存储，在浏览器关闭，重新打开页面后数据仍然存在。
### localStorage应用示例
~~~js
    if (localStorage.pagecount)
	{
	    localStorage.pagecount=Number(localStorage.pagecount) +1;
	}
    else
	{
	    localStorage.pagecount=1;
	}
    document.write("Visits: " + localStorage.pagecount + " time(s).");
~~~

## StorageEvent（存储事件）
>* 通过`StorageEvent`响应存储的变化
>* `Storage`对象发生变化时（创建/更新/删除数据项时，重复设置相同的键值不会触发该事件，`Storage.clear()`方法至多触发一次该事件），
>* `StorageEvent`事件在同一个页面内发生的改变不会起作用，在相同域名下的其他页面（如一个新标签或 iframe）发生的改变才会起作用。在其他域名下的页面不能访问相同的 `Storage`对象。
>* 这里，我们为window对象添加了一个事件监听器，在当前域名相关的 `Storage`对象发生改变时该事件监听器会触发。改变的数据项的键，改变前的旧值，改变后的新值，改变的存储对象所在的文档的 URL，以及存储对象本身。
~~~js
    window.addEventListener('storage', function(e) {  
        document.querySelector('.my-key').textContent = e.key;
        document.querySelector('.my-old').textContent = e.oldValue;
        document.querySelector('.my-new').textContent = e.newValue;
        document.querySelector('.my-url').textContent = e.url;
        document.querySelector('.my-storage').textContent = e.storageArea;
});
~~~
## 参考
* [MDN web storage](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
>>>>>>> a7c4693 (Update: blog)
* [W3C html5 web storage](https://www.w3school.com.cn/html5/html_5_webstorage.asp)