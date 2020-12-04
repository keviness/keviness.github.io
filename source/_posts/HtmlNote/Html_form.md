---
title: HTML FORM
date: 2020.4.8
tag: HTML
abbrlink: 8bf176c0
---
# 背景
&emsp;我们经常需要和远程服务器进行信息交互，在我们需要将信息提交的服务器中的时候，表单（form）的威力也就展示出来了，那么表单具体有哪一些呢？
<!--more-->
### 表单的一些属性：
1. name属性：用于对提交到服务器后的表单数据进行标识,是一种key-value的对应形式。  
2. value属性：在input框里面写的值。
3. readonly属性：使表单元素变为只读。
4. disabled属性：让按钮变灰，使表单元素不可用。
***
### 常见表单元素
#### 常见表单元素应用场景
{% asset_img form.png FormApplication %}
#### 代码举例：
~~~html
    单行文本框
    <input type="text" name="key" value="123" readonly="readonly" 
    disabled="disabled"/>  
    密码框
    <input type="password"/>　　
    下拉列表
    <selected>
        <option value="1" selected>1</option>
        <option value="2">2</option>
        <option value="3">3</option>
    </selected>
    单选框
    <input type="radio" name="like" value="喜欢" checked="checked"/>　　
    <input type="radio" name="like" value="不喜欢"/>
    多选框
    <input type="checkbox" name="run" value="跑" checked="checked"/>　　
    <input type="checkbox" name="climb" value="爬山"/>
    文件域
    <input type="file">
    多行文本框
    <textarea rows="5" cols="10"></textarea>
    提交按钮
    <input type="submit" value="提交"/>　
    重置按钮
    <input type="reset" value="重置"/>  
    按钮
    <input type="button" value="按钮"/>  
    图像按钮
    <input type="image" src="img.jpg">
~~~
