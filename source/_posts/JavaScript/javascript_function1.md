---
title: Function Type
date: 2020.4.9
tag: JavaScript
abbrlink: 77058f3d
---
# 背景
&emsp;JavaScript中皆为对象，其中的函数也是如此。因此JavaScript中的函数调用十分地灵活，让我们来看看JavaScript中的函数类型吧。
## 理解Function类型
>* JavaScript中Function类型实际上是一种对象，每一个函数实际上都是Function类型的一个实例，函数通常是用函数声明语法定义的，而且每一个函数都有默认的属性和方法。
>* 因为函数是一个对象，故函数名实际上也是一个指向函数对象的指针变量，不会与某个函数绑定。
<!--more-->
### 函数声明与表达式（匿名函数）
函数声明会优先被读取使用（函数可提前访问）。
~~~js
    console.log(test(10,30))；　　//40
    function test(num1,num2) {
        return num1+num2;
    };
~~~
函数表达式则必须等到执行完它所在的表达行后再可以使用。
~~~js
    console.log(test(10,30));　　//error
    var test = function (num1,num2) {
        return num1+num2;
    };
~~~
### 作为值的函数
>* js中的函数名本身就是变量，所以函数也可以作为值来使用，可以像传递参数一样把一个函数传递给另一个函数。
~~~js
    function sum (num1, num2) {
        return num1 + num2;
    }
    function fuc (num3, num4) {
        return num3 + num4;
    }
    console.log(fuc(sum(2,3), 5));　　//10

    等同于：
    function sum (num1, num2) {
        return num1+num2;
    }
    function func(num1){
        return sum(num1,5);
    }
    alert(func(5));    //10
~~~
***
## 函数内部属性
>* 在函数内部包含两个特殊的对象：arguments和this
### arguments:
>* arguments 是一个类数组，用来保存函数传递过来的参数。
>* arguments 中还有一个很重要的属性就是callee，是一个指针变量，指向的是arguments所在的函数本身，在递归中可用这个属性，因为如果函数名改变了，也不需要改变内部的实现。
>* arguments.callee()始终代表的是这个函数本身. 
~~~js
    function box(num){
        if(num<=1){
            return 1;
        }else{
            return num*arguments.callee(num-1);
                //arguments.callee代表的是函数的本身，故和上面是同样的效果
        }
    }
    alert(box(3));//6
~~~
### this:
>* this 这个属性代表的是它所在的对象本身，this 引用的是函数据以执行的环境对象，也就是函数执行的作用域。
>* window是JS中最大的一个对象，在window对象中声明一个变量其实就是给window这个对象声明一个属性，var box=1;相当于 window.box=1;也就等价于this.box=1;
>* 当在全局作用域中调用函数时，this 对象引用的就是 window。
>* 在显示的声明一个对象box，这个box中使用的this就代表的是box本身，this.color就是返回的box中属性color的值，而不是window对象中color的值
~~~js
    var box={
        color:'blue',
        run:function(){
            alert(this.color);    //blue
            return this.color;
        }
    }
    alert(window.color);    //red
    alert(this.color);     //red 此处this代表的是window对象，故this.color是代表的window的属性
    alert(box.run());      //blue
~~~
****
## 函数的属性和方法
>每个函数都包含两个属性：length和prototype
### length:
>函数的属性length代表的是函数希望接收的参数的个数，是由声明函数时参数列表中的个数决定的。

### prototype:
>* prototype 是保存所有实例方法的实际所在，也就是原型。  
>* prototype下面有两个方法：apply()，call()，这两个方法都是函数非继承而来的方法，是每一个函数都具有的方法。
>* 这两个方法的用途都是在特定的作用域中调用函数(看this指向的作用域是谁) 
~~~js
    function sum (num1, num2) {
        return num1 + num2;
    }
    var result = sum.apply(this,[10,20]);
    var result = sum.call(this,10,20);
    console.log(result);
~~~
>* func.apply()；方法有两个参数，第一个参数是要执行这个方法的作用域，也就是传递一个对象，第二个参数是一个数组，这个数组中是存放的调用的函数func的实参，也就是要传递给func的值，当然这个参数可以省略。  
>* func.call()：方法和上面的apply()方法相似，不同的是参数，作用域和apply()一样，但其余的参数是逐个列举出传递给函数的，而不是传递一个数组。
>* 使用这apply()和call()这两个方法来扩充作用域最大的好处是：对象不需要与方法发生任何的耦合关系。
### 代码示例:
~~~js    
    var color='red';
    var box={
        color:'green'
    }
    function sayColor(){
        return this.color;
    }
    alert(sayColor());          　　//red 对象：window
    alert(sayColor.apply(window));  //red  对象：window
    alert(sayColor.apply(this));    //red  对象：window
    alert(sayColor.apply(box));     //green  对象：box
~~~