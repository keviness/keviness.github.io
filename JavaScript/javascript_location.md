<<<<<<< HEAD
---
title: Location Object概述
data: 2020.7.7
tags:
  - JavaScript
  - location
  - hash
  - history
abbrlink: abe472d8
---
# 背景
&emsp;以史为鉴，是人类发明的一种不错的改善当前经验的方法。每个人从过去的经历中学习到了很多，历史对我们而言十分重要。在web世界中，我们如何对待曾经发生过的历史呢？
<!--more-->
## 一，Location 对象属性
|属性|	描述|
|:----:|:-----:|
|hash  |设置或返回从井号 (#) 开始的 URL（锚）。|
|host  |设置或返回主机名和当前 URL 的端口号。|
|hostname|设置或返回当前 URL 的主机名。|
|href	|设置或返回完整的 URL。|
|pathname|设置或返回当前 URL 的路径部分。|
|port	|设置或返回当前 URL 的端口号。|
|protocol	|设置或返回当前 URL 的协议。|
|search	|设置或返回从问号 (?) 开始的 URL（查询部分）。|

## 二，Location对象方法
|属性|  描述 |
|:----:|:-------:|
|assign()|加载新的文档。|
|reload()|重新加载当前文档。|
|replace()|用新的文档替换当前文档。|

### Location hash示例
~~~js
        var bodyObj = document.getElementsByTagName("body")[0];
        bodyObj.addEventListener("click", getButtonValue, false);
        window.addEventListener("hashchange", showToCont, false);

        function getButtonValue(event) {
            var targetElement = event.target;
            if (targetElement.nodeName.toLowerCase() === "button") {
                value = targetElement.innerHTML;
                location.hash = value;
            }
        }

        function showToCont() {
            var value,
                contObj;

            contObj = document.querySelector("#cont");
            value = getLocationHash();
            if (value) {
                contObj.innerHTML = value;
            }
        }

        function getLocationHash() {
            var hashValue = location.hash;
            return hashValue? hashValue.substring(1, hashValue.length):null;
        }
~~~

## 三，pushState()和replaceState()
>* `history.pushState/replaceState(state, title, url)`;
>* state：存储JSON字符串，可以用在popstate事件中。
>* title：现在大多数浏览器不支持或者忽略这个参数，最好用null代替
>* url：任意有效的URL.
>* 两个方法的主要区别：`pushState()`是在history栈中添加一个新的条目，`replaceState()`是替换当前的记录值。

## 四，popstate
>* 当前活动历史项(history entry)改变会触发popstate事件。
>* 调用`history.pushState()`创建新的历史项(history entry)，或调用`history.replaceState()`替换新的历史项(history entry)，那么popstate事件的state属性会包含历史项(history entry)状态对象(state object)的拷贝。
>* 注意,调用`history.pushState()`或`history.replaceState()`不会触发popstate事件。只有在做出浏览器动作时，才会触发该事件，如用户点击浏览器的回退按钮（或者在Javascript代码中调用`history.back()`）
>* 不同的浏览器在加载页面时处理popstate事件的形式存在差异。页面加载时Chrome和Safari通常会触发popstate事件，但Firefox则不会。

~~~js
window.onpopstate = function(e) {
    //浏览器触发返回和前进时触发
    console.log(e.state);
   };
~~~

## 五，History对象
* `history.pushState()`会增加历史记录的条目，但是不会触发hashchange和popstate；
* hashchange也可以增加历史记录的条目，但是它却可以触发popstate。

## 六，change事件
- change事件在`<input>`, `<select>`, 和`<textarea>`元素的值更改时触发；与input事件不同，change事件不一定会对元素值的每次更改触发。
- `<input type="radio">`和`<input type="checkbox">`的默认选项被修改时，例如：通过点击或者键盘事件；
如：点击了`<select>`中的一个选项，从`<input type="date">`标签选择了一个日期，通过`<input type="file">`标签上传了一个文件等；
* 当标签的值被修改并且失焦后，但并未进行提交，例如：对`<textarea>`或者`<input type="text">`的值进行编辑后。

=======
---
title: Location Object概述
date: 2020.7.7
tags:
  - JavaScript
  - location
  - hash
  - history
abbrlink: abe472d8
---
# 背景
&emsp;以史为鉴，是人类发明的一种不错的改善当前经验的方法。每个人从过去的经历中学习到了很多，历史对我们而言十分重要。在web世界中，我们如何对待曾经发生过的历史呢？
<!--more-->
## 一，Location 对象属性
|属性|	描述|
|:----:|:-----:|
|hash  |设置或返回从井号 (#) 开始的 URL（锚）。|
|host  |设置或返回主机名和当前 URL 的端口号。|
|hostname|设置或返回当前 URL 的主机名。|
|href	|设置或返回完整的 URL。|
|pathname|设置或返回当前 URL 的路径部分。|
|port	|设置或返回当前 URL 的端口号。|
|protocol	|设置或返回当前 URL 的协议。|
|search	|设置或返回从问号 (?) 开始的 URL（查询部分）。|

## 二，Location对象方法
|属性|  描述 |
|:----:|:-------:|
|assign()|加载新的文档。|
|reload()|重新加载当前文档。|
|replace()|用新的文档替换当前文档。|

### Location hash示例
~~~js
        var bodyObj = document.getElementsByTagName("body")[0];
        bodyObj.addEventListener("click", getButtonValue, false);
        window.addEventListener("hashchange", showToCont, false);

        function getButtonValue(event) {
            var targetElement = event.target;
            if (targetElement.nodeName.toLowerCase() === "button") {
                value = targetElement.innerHTML;
                location.hash = value;
            }
        }

        function showToCont() {
            var value,
                contObj;

            contObj = document.querySelector("#cont");
            value = getLocationHash();
            if (value) {
                contObj.innerHTML = value;
            }
        }

        function getLocationHash() {
            var hashValue = location.hash;
            return hashValue? hashValue.substring(1, hashValue.length):null;
        }
~~~

## 三，pushState()和replaceState()
>* `history.pushState/replaceState(state, title, url)`;
>* state：存储JSON字符串，可以用在popstate事件中。
>* title：现在大多数浏览器不支持或者忽略这个参数，最好用null代替
>* url：任意有效的URL.
>* 两个方法的主要区别：`pushState()`是在history栈中添加一个新的条目，`replaceState()`是替换当前的记录值。

## 四，popstate
>* 当前活动历史项(history entry)改变会触发popstate事件。
>* 调用`history.pushState()`创建新的历史项(history entry)，或调用`history.replaceState()`替换新的历史项(history entry)，那么popstate事件的state属性会包含历史项(history entry)状态对象(state object)的拷贝。
>* 注意,调用`history.pushState()`或`history.replaceState()`不会触发popstate事件。只有在做出浏览器动作时，才会触发该事件，如用户点击浏览器的回退按钮（或者在Javascript代码中调用`history.back()`）
>* 不同的浏览器在加载页面时处理popstate事件的形式存在差异。页面加载时Chrome和Safari通常会触发popstate事件，但Firefox则不会。

~~~js
window.onpopstate = function(e) {
    //浏览器触发返回和前进时触发
    console.log(e.state);
   };
~~~

## 五，History对象
* `history.pushState()`会增加历史记录的条目，但是不会触发hashchange和popstate；
* hashchange也可以增加历史记录的条目，但是它却可以触发popstate。

## 六，change事件
- change事件在`<input>`, `<select>`, 和`<textarea>`元素的值更改时触发；与input事件不同，change事件不一定会对元素值的每次更改触发。
- `<input type="radio">`和`<input type="checkbox">`的默认选项被修改时，例如：通过点击或者键盘事件；
如：点击了`<select>`中的一个选项，从`<input type="date">`标签选择了一个日期，通过`<input type="file">`标签上传了一个文件等；
* 当标签的值被修改并且失焦后，但并未进行提交，例如：对`<textarea>`或者`<input type="text">`的值进行编辑后。

>>>>>>> a7c4693 (Update: blog)
