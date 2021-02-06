<<<<<<< HEAD
---
title: JavaScript对HTML进行编码与解码
date: 2020.5.31
tag: JavaScript
abbrlink: e10ad84b
---
# 背景
&emsp;经常遇到一些字符需要进行转义后才能显示到界面上。此时，就需要进行编码与解码，那么如何进行编码和解码呢？以下是一些个总结：
<!--more-->
### 代码示例：
~~~js
    <script>
    var HtmlUtil = {

        /*1.用浏览器内部转换器实现html编码*/
        htmlEncode:function (html){
            //动态创建一个容器标签元素
            var temp = document.createElement ("div");

            //将要转换的字符串设置为元素的innerText(ie)或textContent(firefox，google支持)
            (temp.textContent != undefined ) ? (temp.textContent = html) : (temp.innerText = html);

            //返回元素的innerHTML，即得HTML编码的字符串
            var output = temp.innerHTML;
            temp = null;
            return output;
        },

        /*2.用浏览器内部转换器实现html解码*/
        htmlDecode:function (text){

            //动态创建一个容器标签元素
            var temp = document.createElement("div");

            //将要转换的字符串设置为元素的innerHTML(ie，firefox，google)
            temp.innerHTML = text;

            //返回这个元素的innerText(ie)或textContent(firefox，google)，即得到经HTML解码的字符串
            var output = temp.innerText || temp.textContent;
            temp = null;
            return output;
        },

        /*3.用正则表达式实现html编码*/
        htmlEncodeByRegExp:function (str){ 
            var s = "";
            if(str.length == 0) return "";
            s = str.replace(/&/g,"&");
            s = s.replace(/</g,"<");
            s = s.replace(/>/g,">");
            s = s.replace(/ /g," ");
            s = s.replace(/\'/g,"'");
            s = s.replace(/\"/g,""");
            return s; 
        },

        /*4.用正则表达式实现html解码*/
        htmlDecodeByRegExp:function (str){ 
            var s = "";
            if(str.length == 0) return "";
            s = str.replace("&", /&/g);
            s = s.replace(">", /</g);
            s = s.replace("<", />/g);
            s = s.replace(" ", / /g);
            s = s.replace("\'", /'/g);
            s = s.replace("\"", /"/g);
            return s; 
        }
    };
    </script>
~~~
### 参考：
=======
---
title: JavaScript对HTML进行编码与解码
date: 2020.5.31
tag: JavaScript
abbrlink: e10ad84b
---
# 背景
&emsp;经常遇到一些字符需要进行转义后才能显示到界面上。此时，就需要进行编码与解码，那么如何进行编码和解码呢？以下是一些个总结：
<!--more-->
### 代码示例：
~~~js
    <script>
    var HtmlUtil = {

        /*1.用浏览器内部转换器实现html编码*/
        htmlEncode:function (html){
            //动态创建一个容器标签元素
            var temp = document.createElement ("div");

            //将要转换的字符串设置为元素的innerText(ie)或textContent(firefox，google支持)
            (temp.textContent != undefined ) ? (temp.textContent = html) : (temp.innerText = html);

            //返回元素的innerHTML，即得HTML编码的字符串
            var output = temp.innerHTML;
            temp = null;
            return output;
        },

        /*2.用浏览器内部转换器实现html解码*/
        htmlDecode:function (text){

            //动态创建一个容器标签元素
            var temp = document.createElement("div");

            //将要转换的字符串设置为元素的innerHTML(ie，firefox，google)
            temp.innerHTML = text;

            //返回这个元素的innerText(ie)或textContent(firefox，google)，即得到经HTML解码的字符串
            var output = temp.innerText || temp.textContent;
            temp = null;
            return output;
        },

        /*3.用正则表达式实现html编码*/
        htmlEncodeByRegExp:function (str){ 
            var s = "";
            if(str.length == 0) return "";
            s = str.replace(/&/g,"&");
            s = s.replace(/</g,"<");
            s = s.replace(/>/g,">");
            s = s.replace(/ /g," ");
            s = s.replace(/\'/g,"'");
            s = s.replace(/\"/g,""");
            return s; 
        },

        /*4.用正则表达式实现html解码*/
        htmlDecodeByRegExp:function (str){ 
            var s = "";
            if(str.length == 0) return "";
            s = str.replace("&", /&/g);
            s = s.replace(">", /</g);
            s = s.replace("<", />/g);
            s = s.replace(" ", / /g);
            s = s.replace("\'", /'/g);
            s = s.replace("\"", /"/g);
            return s; 
        }
    };
    </script>
~~~
### 参考：
>>>>>>> a7c4693 (Update: blog)
* [JavaScript对HTML进行编码与解码](https://www.cnblogs.com/GumpYan/p/7883133.html)