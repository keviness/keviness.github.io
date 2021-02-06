---
title: 用C语言实现显示日历
date: 2021/2/6
tags:
  - C
  - Calendar
  - Project
abbrlink: 40451eee
---
# 背景
&emsp;时间过的飞快，研一上学期已经画上了句号。在翻看新年日历的时候，我突发奇想：能不能用程序实现日历的打印，于是就有了以下实现工作，具体的实现代码请用[随意门]()。
<!--more-->
{% asset_img calendar.png calendar %}

## 一，查找一星期的第几天
~~~c
int dayofweek(int year, int month, int day)
{
    if (month==1 && month==2)
    {
        year--;
        month += 12;
    }
    return (year+year/4 - year/100+year/400 +(13*month+8)/5 + day) % 7;
}
~~~

## 二，确定闰年与平年
~~~c
int is_leap(int year)
{
    return (year%4==0 && year%100!=0) || year%400==0;
}
~~~

## 三，确定每个月的天数
~~~c
int monthdays(int year, int month)
{
    if (month-- != 2)
    {
        return mday[month];
    }

    return mday[month] + is_leap(year);
}
~~~

## 四，生成日历
~~~c
void make_calendar(int year, int month, char s[7][22])
{
    int i, k;
    int wd = dayofweek(year, month, 1);
    int mdays = monthdays(year, month);
    char tmp[4];

    sprintf(s[0], "%14d / %02d     ", year, month);
    for (k=1; k<7; k++)
        s[k][0] = '\0';

    k = 1;
    sprintf(s[k], "%*s", 3*wd, "");

    for (i=1; i<=mdays; i++)
    {
        sprintf(tmp, "%3d", i);
        strcat(s[k], tmp);
        if (++wd % 7 == 0)
            k++;
    }
    if (wd % 7 == 0)
        k--;
    else
    {
        for (wd %= 7; wd<7; wd++)
            strcat(s[k], "  ");
    }
    while (++k < 7)
        sprintf(s[k], "%21s", "");
}
~~~

## 五，把存放在三维数组中的日历横向排列n个显示
~~~c
void print(char sbuf[3][7][22], int n)
{
    int i, j;

    for (i=0; i<n; i++)
    {
        printf("%s   ", sbuf[i][0]);
    }
    putchar('\n');

    for (i=0; i<n; i++)
        printf(" Sun Mon Tue Wed Thu Fri Sat     ");
    putchar('\n');
    for (i=0; i<n; i++)
        printf("-----------------------    ");
    putchar('\n');

    for (i=1; i<7; i++)
    {
        for (j=0; j<n; j++)
            printf("%s  ", sbuf[j][i]);
        putchar('\n');
    }
    putchar('\n');
}
~~~

## 六，打印y1/m1到y2/m2的日历
~~~c
void put_calendar(int y1, int m1, int y2, int m2)
{
    int y = y1;
    int m = m1;
    int n = 0;
    char sbuf[3][7][22];

    while (y <= y2)
    {
        if (y == y2 && m >m2) break;
        make_calendar(y, m, sbuf[n++]);
        if (n == 3)
        {
            print(sbuf, n);
            n = 0;
        }
        m++;
        if (m==13 && y<y2)
        {
            y++;
            m = 1;
        }
    }
    if (n)
    {
        print(sbuf, m);
    }
}
~~~