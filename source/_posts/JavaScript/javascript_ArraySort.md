---
title: Array Sort(数组排序)
date: 2020.5.26
tag: JavaScript
abbrlink: 73a0fa2d
---
# 背景
&emsp;在JavaScript中，我们经常需要对各种数据进行排序，array.sort()运用比较频繁，它可以自定义排序函数，功能强大，以下是一些个总结：
<!--more-->
### 语法
>* `array.sort([compareFunction])`
>* compareFunction：用来指定按某种顺序进行排列的函数。
>* 返回值：排序后的数组。
>* 注意：数组原地排序，不进行复制。
### 详细描述
>* 如果没有指明compareFunction，那么元素会按照转换为的字符串的诸个字符的Unicode位点进行排序。
>* 例如"Banana"会被排列到"cherry"之前。当数字按由小到大排序时,9出现在80之前，但因为（没有指明compareFunction），比较的数字会先被转换为字符串，所以在Unicode顺序上"80"要比"9"要靠前。
>* 如果指明了compareFunction，那么数组会按照调用该函数的返回值排序。a和b是两个将要被比较的元素：
~~~js
    compareFunction(a, b)<0，a会被排列到b之前；
    compareFunction(a, b)==0，a和b的相对位置不变。
    compareFunction(a, b)>0，b排列到a之前。
~~~
### compare(a, b)函数
#### 比较Number与String（通用）
~~~js
    function compare(a, b) {
        if (a < b ) {   
            return -1;
        }
        if (a > b ) {
            return 1;
        }
        return 0;
    }
~~~
#### 比较Number
~~~js
    function compareNumbers(a, b) {
        return a - b;
    }
~~~
### 排序示例
#### 数组排序
~~~js
    var numbers = [4, 2, 5, 1, 3];
    numbers.sort(function(a, b) {
        return a - b;
    });
    console.log(numbers);
    等价于：
    var numbers = [4, 2, 5, 1, 3]; 
    numbers.sort((a, b) => a - b); 
    console.log(numbers);
~~~

#### 对象类型排序
~~~js
    var items = [
        { name: 'Edward', value: 21 },
        { name: 'Sharpe', value: 37 },
        { name: 'And', value: 45 },
        { name: 'The', value: -12 },
        { name: 'Magnetic' },
        { name: 'Zeros', value: 37 }
    ];
    // sort by value
    items.sort(function (a, b) {
        return (a.value - b.value)
    });

    // sort by name
    items.sort(function(a, b) {
        var nameA = a.name.toUpperCase(); 
        var nameB = b.name.toUpperCase(); 
        if (nameA < nameB) {
            return -1;
        }
        if (nameA > nameB) {
            return 1;
        }
        return 0;
    });
~~~

### 非ASCII字符排序
>当排序非ASCII字符的字符串（如包含类似e、é、è、a、ä等字符的字符串）。一些非英语语言的字符串需要使用`String.localeCompare`。
#### 示例
~~~js
    var items = ['réservé', 'premier', 'cliché'];
    items.sort(function (a, b) {
        return a.localeCompare(b);
    });
~~~

### 用映射辅助排序
>* compareFunction可能需要对元素做多次映射以实现排序，当 compareFunction较为复杂，且元素较多的时候，可能会导致很高的负载。可使用 map()辅助排序。
>* 基本思想是首先将数组中的每个元素比较的实际值取出来，排序后再将数组恢复。

#### 示例
~~~js
    var list = ['Delta', 'alpha', 'CHARLIE', 'bravo'];
    var mapped = list.map(function(el, i) {
        return { index: i, value: el.toLowerCase() };
    })

    mapped.sort(function(a, b) {
        return +(a.value > b.value) || +(a.value === b.value) - 1;
    });

    var result = mapped.map(function(el){
        return list[el.index];
    });
~~~
