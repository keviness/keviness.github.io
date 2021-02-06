<<<<<<< HEAD
---
title: 队列：顺序存储实现
date: 2020.8.11
tags:
  - C
  - Queue
  - Algorithms
abbrlink: 75b41c5c
---
# 背景
&emsp;队列在生活中可是经常见的。比如，食堂，商场等地方经常需要排队。它的主要性质是先进先出（first in first out），在算法中队列有顺序存储（连续存储）和链式存储（离散存储）两种方式。其中顺序存储必须要用循环队列的形式实现，具体如下：
<!--more--->
## 队列：顺序存储实现
### 一，顺序存储实现
>* 顺序存储实现队列必须用循环队列方式实现。
>* 如此，对内存的使用友好，不会使程序奔溃。
#### （一）概念及示意图
##### 1,入队出队示意图
{% asset_img queue_sequence.png queueSequence %}
##### 2,判断队列满或空示意图
{% asset_img queue_empty.png queueEmpty %}
### 二，实现代码
#### （一）队列数据形式
~~~c
typedef struct Queue
{
    int *pbase;
    int front;
    int rear;
}QUEUE, * PQUEUE;
~~~
#### （二）初始化队列
~~~c
void InitQueue(PQUEUE queue)
{
    queue->pbase = (int *)malloc(sizeof(int) * SIZE);
    if ((queue->pbase) == NULL)
    {
        puts("Error in locating the memory!");
        exit(EXIT_FAILURE);
    }
    queue->front = 0;
    queue->rear = 0;
}
~~~
#### （三）检测队列为空或已满
~~~c
bool QueueIsEmpty(PQUEUE queue)
{
    return ((queue->front) == (queue->rear))? true:false;
}
bool QueueIsFull(PQUEUE queue)
{
    return (((queue->rear)+1 % SIZE) == (queue->front)) ? true:false;
}
~~~
#### （四）入队出队操作
~~~c
bool EnterQueue(PQUEUE queue)
{
    if (QueueIsFull(queue))
    {
        puts("The queue is full!");
        return false;
    }
    int data;
    (queue->pbase)[queue->rear] = data;
    queue->rear = (queue->rear+1)%SIZE;

    return true;
}

bool OutQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return false;
    }
    int data;
    data = (queue->pbase)[queue->front];
    queue->front = (queue->front+1)%SIZE;
    printf("The out queue data:%d \n", data);

    return true;
}
~~~
#### （五）遍历队列
~~~c
void TraverseQueue(PQUEUE queue, void(*pfunc)(int *data))
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    int i = queue->front;
    while (i != queue->rear)
    {
        (*pfunc)(&(queue->pbase[i]));
        i = (i+1)%SIZE;
    }
}
~~~
#### （六）打印队列
~~~c
void ShowQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    int i = queue->front;
    while (i != queue->rear)
    {
        printf("%d ", (queue->pbase)[i]);
        i = (i+1)%SIZE;
    }
    putchar('\n');
}
~~~
#### （七）队列长度
~~~c
void QueueLength(PQUEUE queue)
{
    int i = queue->front;
    int count = 0;
    while (i != queue->rear)
    {
        count++;
        i = (i+1)%SIZE;
    }
    printf("The queue length:%d \n", count);
}
~~~
#### （八）清空队列
~~~c
void ClearQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    free(queue->pbase);
    puts("Clear queue successfully!");
}
=======
---
title: 队列：顺序存储实现
date: 2020.8.11
tags:
  - C
  - Queue
  - Algorithms
abbrlink: 75b41c5c
---
# 背景
&emsp;队列在生活中可是经常见的。比如，食堂，商场等地方经常需要排队。它的主要性质是先进先出（first in first out），在算法中队列有顺序存储（连续存储）和链式存储（离散存储）两种方式。其中顺序存储必须要用循环队列的形式实现，具体如下：
<!--more--->
## 队列：顺序存储实现
### 一，顺序存储实现
>* 顺序存储实现队列必须用循环队列方式实现。
>* 如此，对内存的使用友好，不会使程序奔溃。
#### （一）概念及示意图
##### 1,入队出队示意图
{% asset_img queue_sequence.png queueSequence %}
##### 2,判断队列满或空示意图
{% asset_img queue_empty.png queueEmpty %}
### 二，实现代码
#### （一）队列数据形式
~~~c
typedef struct Queue
{
    int *pbase;
    int front;
    int rear;
}QUEUE, * PQUEUE;
~~~
#### （二）初始化队列
~~~c
void InitQueue(PQUEUE queue)
{
    queue->pbase = (int *)malloc(sizeof(int) * SIZE);
    if ((queue->pbase) == NULL)
    {
        puts("Error in locating the memory!");
        exit(EXIT_FAILURE);
    }
    queue->front = 0;
    queue->rear = 0;
}
~~~
#### （三）检测队列为空或已满
~~~c
bool QueueIsEmpty(PQUEUE queue)
{
    return ((queue->front) == (queue->rear))? true:false;
}
bool QueueIsFull(PQUEUE queue)
{
    return (((queue->rear)+1 % SIZE) == (queue->front)) ? true:false;
}
~~~
#### （四）入队出队操作
~~~c
bool EnterQueue(PQUEUE queue)
{
    if (QueueIsFull(queue))
    {
        puts("The queue is full!");
        return false;
    }
    int data;
    (queue->pbase)[queue->rear] = data;
    queue->rear = (queue->rear+1)%SIZE;

    return true;
}

bool OutQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return false;
    }
    int data;
    data = (queue->pbase)[queue->front];
    queue->front = (queue->front+1)%SIZE;
    printf("The out queue data:%d \n", data);

    return true;
}
~~~
#### （五）遍历队列
~~~c
void TraverseQueue(PQUEUE queue, void(*pfunc)(int *data))
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    int i = queue->front;
    while (i != queue->rear)
    {
        (*pfunc)(&(queue->pbase[i]));
        i = (i+1)%SIZE;
    }
}
~~~
#### （六）打印队列
~~~c
void ShowQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    int i = queue->front;
    while (i != queue->rear)
    {
        printf("%d ", (queue->pbase)[i]);
        i = (i+1)%SIZE;
    }
    putchar('\n');
}
~~~
#### （七）队列长度
~~~c
void QueueLength(PQUEUE queue)
{
    int i = queue->front;
    int count = 0;
    while (i != queue->rear)
    {
        count++;
        i = (i+1)%SIZE;
    }
    printf("The queue length:%d \n", count);
}
~~~
#### （八）清空队列
~~~c
void ClearQueue(PQUEUE queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    free(queue->pbase);
    puts("Clear queue successfully!");
}
>>>>>>> a7c4693 (Update: blog)
~~~