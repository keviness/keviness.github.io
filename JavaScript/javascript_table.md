<<<<<<< HEAD
---
title: JavaScript实现跨行合并table中相同单元格
tags:
  - JavaScript
  - Table
abbrlink: 6a9fb1f0
---
# 背景
&emsp;在web中我们经常需要用到table表格对我们的数据进行呈现，table表格能很友好地显示我们的数据，那在动态创建table时，如何进行跨行合并相同内容单元格呢？以下是一些个方法：
<!--more-->
## 合并表格相同列的内容
>* table：表格或者表格ID（最好是tbody，避免把表尾给合并了)
>* startRow：起始行，没有标题就从0开始
>* endRow：终止行，此参数是递归时检查的范围，一开始时会自动赋值为最后一行
>* col：当前处理的列
>* endCol:终止列
>* isInit:是否初始调用，如果是则在终止行为0时自动取最后一行
~~~js
    function MergeCell(table, startRow, endRow, col, endCol isInit)  {
        if (typeof (table) == 'string')
            table = document.getElementById(table);
        if (col >= table.rows[0].cells.length || col > endCol) {
            return;
        }
        if (isInit == undefined) isInit = true;
        //当检查第0列时检查所有行
        if ((col == 0 || endRow == 0) && isInit) {
            endRow = table.rows.length - 1;
        }
        for (var i = startRow; i < endRow; i++) {
            //程序是自左向右合并
            if (table.rows[startRow].cells[col].innerHTML == table.rows[i + 1].cells[col].innerHTML) {
            //如果相同则隐藏下一行的同列单元格
                table.rows[i + 1].cells[col].style.display = 'none';
            //更新rowSpan属性
                table.rows[startRow].cells[col].rowSpan = (table.rows[startRow].cells[col].rowSpan | 0) + 1;
            //当循环到终止行前一行并且起始行和终止行不相同时递归(因为上面的代码已经检查了i+1行，所以此处只到endRow-1)
                if (i == endRow - 1 && startRow != endRow) {
                MergeCell(table, startRow, endRow, col + 1, endCol, false);
                }
        } else {
            //起始行，终止行不变，检查下一列
            MergeCell(table, startRow, i, col + 1, endCol, false);
            //增加起始行
            startRow = i + 1;
        }
    }
=======
---
title: JavaScript实现跨行合并table中相同单元格
date: 2020.10.23
tags:
  - JavaScript
  - Table
abbrlink: 6a9fb1f0
---
# 背景
&emsp;在web中我们经常需要用到table表格对我们的数据进行呈现，table表格能很友好地显示我们的数据，那在动态创建table时，如何进行跨行合并相同内容单元格呢？以下是一些个方法：
<!--more-->
## 合并表格相同列的内容
>* table：表格或者表格ID（最好是tbody，避免把表尾给合并了)
>* startRow：起始行，没有标题就从0开始
>* endRow：终止行，此参数是递归时检查的范围，一开始时会自动赋值为最后一行
>* col：当前处理的列
>* endCol:终止列
>* isInit:是否初始调用，如果是则在终止行为0时自动取最后一行
~~~js
    function MergeCell(table, startRow, endRow, col, endCol isInit)  {
        if (typeof (table) == 'string')
            table = document.getElementById(table);
        if (col >= table.rows[0].cells.length || col > endCol) {
            return;
        }
        if (isInit == undefined) isInit = true;
        //当检查第0列时检查所有行
        if ((col == 0 || endRow == 0) && isInit) {
            endRow = table.rows.length - 1;
        }
        for (var i = startRow; i < endRow; i++) {
            //程序是自左向右合并
            if (table.rows[startRow].cells[col].innerHTML == table.rows[i + 1].cells[col].innerHTML) {
            //如果相同则隐藏下一行的同列单元格
                table.rows[i + 1].cells[col].style.display = 'none';
            //更新rowSpan属性
                table.rows[startRow].cells[col].rowSpan = (table.rows[startRow].cells[col].rowSpan | 0) + 1;
            //当循环到终止行前一行并且起始行和终止行不相同时递归(因为上面的代码已经检查了i+1行，所以此处只到endRow-1)
                if (i == endRow - 1 && startRow != endRow) {
                MergeCell(table, startRow, endRow, col + 1, endCol, false);
                }
        } else {
            //起始行，终止行不变，检查下一列
            MergeCell(table, startRow, i, col + 1, endCol, false);
            //增加起始行
            startRow = i + 1;
        }
    }
>>>>>>> a7c4693 (Update: blog)
~~~