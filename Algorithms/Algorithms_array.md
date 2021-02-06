<<<<<<< HEAD
---
title: 线性表：数组的实现
date: 2020.9.3
tags:
  - Algorithms
  - List
  - Array
  - C
abbrlink: ab15e1cb
---
# 背景
&emsp;数组在C语言中已经存在了，那么如何实现一个自定义的数组呢？以下是一些实现思路，完整代码请走[神奇的传送门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_C/DataStruct/array.c)
<!--more-->
## 线性表：数组的实现
### 一，概念及示意图
* 数组的链式存储示意图
![数组链表存储示意图](./img/queue1.png)

### 二，实现代码
#### （一）数据形式
~~~c
typedef struct array
{
    int count;
    int length;
    int *pint;
}Array;
~~~
#### （二）初始化
~~~c
void InitializeArray(Array *parr)
{
    parr->pint = (int *)malloc(sizeof(int)*(parr->length));
    if ((parr->pint) == NULL)
    {
        puts("Can\'t locate the memory!");
        exit(EXIT_FAILURE);
    }
    parr->count = 0;
    parr->length = MAXSIZE;
}
~~~
#### （三）检测为空或已满
~~~c
bool ArrayIsFull(const Array *parr)
{
    return (parr->count)==(parr->length)? true:false;
}

bool ArrayIsEmpty(const Array *parr)
{
    return (parr->count) == 0? true:false;
}
~~~
#### （四）追加操作
~~~c
bool AppendItem(Array *parr)
{
    int item;
    if (ArrayIsFull(parr))
    {
        puts("The array is full!");
        return false;
    }
    puts("Enter the item you want to append:");
    scanf("%d", &item);
    EATLINE;
    (parr->pint)[parr->count] = item;
    (parr->count)++;
    return true;
}
~~~
#### （五）插入操作
~~~c
bool InsertItem(Array *parr)
{
    int pos;
    int item;
    if (ArrayIsFull(parr))
    {
        puts("The array is full!");
        return false;
    }
    puts("Enter the index you want to insert:");
    scanf("%d", &pos);
    EATLINE;
    if (pos<1 || pos>(parr->count)+1)
    {
        puts("Error pos!");
        return false;
    }
    puts("Enter the item you want to insert:");
    scanf("%d", &item);
    EATLINE;

    for (int i=(parr->count-1); i>=(pos-1); i--)
    {
        (parr->pint)[i+1] = (parr->pint)[i];
    }
    (parr->pint)[pos-1] = item;
    (parr->count)++;

    return true;
}
~~~
#### （六）删除操作
~~~c
int DeleteItem(Array *parr)
{
    int pos;
    int item;
    if (ArrayIsEmpty(parr))
    {
        puts("The array is empty!");
        return false;
    }
    puts("Enter the index of the item you want to delete:");
    scanf("%d", &pos);
    EATLINE;
    if (pos<1 || pos>(parr->count))
    {
        puts("The index out of range!");
        return false;
    }
    item = (parr->pint)[pos-1];
    for (int i=pos; i<(parr->count); i++)
    {
        (parr->pint)[i-1] = (parr->pint)[i];
    }
    parr->count--;
    return item;
}
~~~
#### （七）获取元素
~~~c
int GetItem(const Array *parr)
{
    int pos;
    int result;
    if (ArrayIsEmpty(parr))
    {
        puts("The Array is empty!");
        exit(EXIT_FAILURE);
    }
    puts("Enter the index of element you want to get:");
    scanf("%d", &pos);
    EATLINE;
    result = (parr->pint)[pos];

    return result;
}
~~~
=======
---
title: 线性表：数组的实现
date: 2020.9.3
tags:
  - Algorithms
  - List
  - Array
  - C
abbrlink: ab15e1cb
---
# 背景
&emsp;数组在C语言中已经存在了，那么如何实现一个自定义的数组呢？以下是一些实现思路，完整代码请走[神奇的传送门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_C/DataStruct/array.c)
<!--more-->
## 线性表：数组的实现
### 一，概念及示意图
* 数组的链式存储示意图
![数组链表存储示意图](./img/queue1.png)

### 二，实现代码
#### （一）数据形式
~~~c
typedef struct array
{
    int count;
    int length;
    int *pint;
}Array;
~~~
#### （二）初始化
~~~c
void InitializeArray(Array *parr)
{
    parr->pint = (int *)malloc(sizeof(int)*(parr->length));
    if ((parr->pint) == NULL)
    {
        puts("Can\'t locate the memory!");
        exit(EXIT_FAILURE);
    }
    parr->count = 0;
    parr->length = MAXSIZE;
}
~~~
#### （三）检测为空或已满
~~~c
bool ArrayIsFull(const Array *parr)
{
    return (parr->count)==(parr->length)? true:false;
}

bool ArrayIsEmpty(const Array *parr)
{
    return (parr->count) == 0? true:false;
}
~~~
#### （四）追加操作
~~~c
bool AppendItem(Array *parr)
{
    int item;
    if (ArrayIsFull(parr))
    {
        puts("The array is full!");
        return false;
    }
    puts("Enter the item you want to append:");
    scanf("%d", &item);
    EATLINE;
    (parr->pint)[parr->count] = item;
    (parr->count)++;
    return true;
}
~~~
#### （五）插入操作
~~~c
bool InsertItem(Array *parr)
{
    int pos;
    int item;
    if (ArrayIsFull(parr))
    {
        puts("The array is full!");
        return false;
    }
    puts("Enter the index you want to insert:");
    scanf("%d", &pos);
    EATLINE;
    if (pos<1 || pos>(parr->count)+1)
    {
        puts("Error pos!");
        return false;
    }
    puts("Enter the item you want to insert:");
    scanf("%d", &item);
    EATLINE;

    for (int i=(parr->count-1); i>=(pos-1); i--)
    {
        (parr->pint)[i+1] = (parr->pint)[i];
    }
    (parr->pint)[pos-1] = item;
    (parr->count)++;

    return true;
}
~~~
#### （六）删除操作
~~~c
int DeleteItem(Array *parr)
{
    int pos;
    int item;
    if (ArrayIsEmpty(parr))
    {
        puts("The array is empty!");
        return false;
    }
    puts("Enter the index of the item you want to delete:");
    scanf("%d", &pos);
    EATLINE;
    if (pos<1 || pos>(parr->count))
    {
        puts("The index out of range!");
        return false;
    }
    item = (parr->pint)[pos-1];
    for (int i=pos; i<(parr->count); i++)
    {
        (parr->pint)[i-1] = (parr->pint)[i];
    }
    parr->count--;
    return item;
}
~~~
#### （七）获取元素
~~~c
int GetItem(const Array *parr)
{
    int pos;
    int result;
    if (ArrayIsEmpty(parr))
    {
        puts("The Array is empty!");
        exit(EXIT_FAILURE);
    }
    puts("Enter the index of element you want to get:");
    scanf("%d", &pos);
    EATLINE;
    result = (parr->pint)[pos];

    return result;
}
~~~
>>>>>>> a7c4693 (Update: blog)
