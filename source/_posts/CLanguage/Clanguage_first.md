---
title: 用C语言实现贪吃蛇
date: 2020.5.2
tag: C
abbrlink: 7fccb627
---
# 背景
&emsp;四月份，随着考研复试的临近，毕业论文也在此刻提上了日程，我停下了手边的前端学习计划。
&emsp;我想着在四月底实现心心念念的[贪吃蛇游戏](https://github.com/keviness/ExerciseProject/blob/master/snakes/snake_try.c)，于是就开始多线程工作啦。
&emsp;当一个个贪吃蛇游戏的功能模块在自己手里逐步实现时，那种快乐难以描述哈。以下是一些个工作。
<!--more-->
### 头文件准备工作
~~~c
    <windows.h>
    <conio.h>
    <time.h>
~~~
以上这头文件需要先了解，对其中常用的API需要掌握。
### 贪吃蛇的实现原理
~~~c
    struct snakes{
        unsigned int len;
        unsigned int speed;
        unsigned int x[MAXSNAKE];
        unsigned int y[MAXSNAKE];
    }snake;

    struct foods{
        unsigned int x;
        unsigned int y;
    }food;
~~~
>* 贪吃蛇的实现原理在于用结构体中的数组储存贪吃蛇的x轴与y轴的坐标。
>* 再在相应坐标位置是打印需要的符号。
>* 蛇的移动效果：蛇每次向前移动一个位置时，清除最后一个坐标的打印符号（打印空格符）（" "）
>* 蛇吃食物的增长原理：每次吃完食物后，长度加一，尾部坐标不清除其符号。
### 各个功能的实现
贪吃蛇的实现主要依靠以下函数：
~~~c
    void welcome(void);  //欢迎用户图形界面
    void initGraph(void);  //游戏初始化界面
    void createFood(void);  //随机产生食物
    void eatFood(void);   //当蛇吃到食物时
    void movingSnake(void);   //移动蛇身
    void controlSnake(void);   //控制蛇运动
    void gotoxy(int x, int y); //移动光标到对应坐标
    void hidenCursor(void);  //隐藏光标
    bool snakeStatus(void);  //判断蛇的状态
~~~
>* 其中对蛇的控制，和蛇身的移动是游戏的核心。