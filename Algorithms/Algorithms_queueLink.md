<<<<<<< HEAD
---
title: 队列：链式存储实现
date: 2020.9.13
tags:
  - Algorithms
  - Queue
  - Link
  - C
abbrlink: 91f8721d
---
# 背景
&emsp;暑假快要结束了，研究生生涯就要拉开序幕了。数据结构的工作可以告一段落了，这个暑假过得还是很充实的，接下来的Java工作也要加油~
&emsp;队列这个数据结构和我们生活的一些排队场景十分相似（FIFO），前面已经简单论述过它的顺序存储实现，接下来是它的链式存储实现，以下是一些实现思路，完整代码请用[随意门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_C/DataStruct/queue_link.c)
<!--more-->
## 队列的链式存储实现
### 一，概念及示意图
#### 队列示意图
{% asset_img queue_link.png queueLink %}

### 二，实现代码
#### （一）队列数据形式
~~~c
typedef struct node
{
    int data;
    struct node *pnext;
}Node, * Pnode;

typedef struct queue
{
    Pnode front;
    Pnode rear;
}Queue, * Pqueue;
~~~
#### （二）初始化队列
~~~c
void InitQueue(Pqueue queue)
{
    queue->front = (Pnode)malloc(sizeof(Node));
    if (queue->front == NULL)
    {
        puts("Can\'t locate the memory!");
        exit(EXIT_FAILURE);
    }
    queue->rear = queue->front;
}
~~~
#### （三）检测队列为空
~~~c
bool QueueIsEmpty(Pqueue queue)
{
    return (queue->front == queue->rear)? true:false;
}
~~~
#### （四）入队操作
~~~c
bool EnQueue(Pqueue queue)
{
    int data, ch;
    puts("Enter the data you want to enqueue:");
    while (scanf("%d", &data) != 1)
    {
        while ((ch = getchar()) != '\n')
        {
            putchar(ch);
        }
        puts(" is not a number! try again:");
    }
    EATLINE;
    Pnode newNode = (Pnode)malloc(sizeof(Node));
    newNode->data = data;
    newNode->pnext = NULL; 
    queue->rear->pnext = newNode;
    queue->rear = newNode;
    printf("Enter the %d successfully! \n", data);

    return true;
}
#### （五）出队操作
bool DeQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return false;
    }
    int data;
    Pnode temp = queue->front->pnext;
    data = temp->data;
    queue->front->pnext = temp->pnext;
    
    if (temp == queue->rear)
    {
        queue->rear = queue->front;
    }
    free(temp);
    printf("Delete %d from the queue successfully!\n", data);

    return true;
}
~~~
#### （六）队列长度
~~~c
int QueueLength(Pqueue queue)
{
    int count = 0;
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        count = 0;
    }
    Pnode start = queue->front->pnext;
    
    while (start != NULL)
    {
        count++;
        start = start->pnext;
    }
    printf("The queue length:%d \n", count);
}
~~~
#### （七）打印队列
~~~c
void ShowQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    Pnode start = queue->front->pnext;
    while (start != NULL)
    {
        printf("%d ", start->data);
        start = start->pnext;
    }
    putchar('\n');
}
~~~
#### （八）清空队列
~~~c
void ClearQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    Pnode temp = queue->front;
    while (temp != NULL)
    {
        queue->front = queue->front->pnext;
        free(temp);
        temp = queue->front;
    }
    puts("clear the queue successfully!");
}
=======
---
title: 队列：链式存储实现
date: 2020.9.13
tags:
  - Algorithms
  - Queue
  - Link
  - C
abbrlink: 91f8721d
---
# 背景
&emsp;暑假快要结束了，研究生生涯就要拉开序幕了。数据结构的工作可以告一段落了，这个暑假过得还是很充实的，接下来的Java工作也要加油~
&emsp;队列这个数据结构和我们生活的一些排队场景十分相似（FIFO），前面已经简单论述过它的顺序存储实现，接下来是它的链式存储实现，以下是一些实现思路，完整代码请用[随意门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_C/DataStruct/queue_link.c)
<!--more-->
## 队列的链式存储实现
### 一，概念及示意图
#### 队列示意图
{% asset_img queue_link.png queueLink %}

### 二，实现代码
#### （一）队列数据形式
~~~c
typedef struct node
{
    int data;
    struct node *pnext;
}Node, * Pnode;

typedef struct queue
{
    Pnode front;
    Pnode rear;
}Queue, * Pqueue;
~~~
#### （二）初始化队列
~~~c
void InitQueue(Pqueue queue)
{
    queue->front = (Pnode)malloc(sizeof(Node));
    if (queue->front == NULL)
    {
        puts("Can\'t locate the memory!");
        exit(EXIT_FAILURE);
    }
    queue->rear = queue->front;
}
~~~
#### （三）检测队列为空
~~~c
bool QueueIsEmpty(Pqueue queue)
{
    return (queue->front == queue->rear)? true:false;
}
~~~
#### （四）入队操作
~~~c
bool EnQueue(Pqueue queue)
{
    int data, ch;
    puts("Enter the data you want to enqueue:");
    while (scanf("%d", &data) != 1)
    {
        while ((ch = getchar()) != '\n')
        {
            putchar(ch);
        }
        puts(" is not a number! try again:");
    }
    EATLINE;
    Pnode newNode = (Pnode)malloc(sizeof(Node));
    newNode->data = data;
    newNode->pnext = NULL; 
    queue->rear->pnext = newNode;
    queue->rear = newNode;
    printf("Enter the %d successfully! \n", data);

    return true;
}
#### （五）出队操作
bool DeQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return false;
    }
    int data;
    Pnode temp = queue->front->pnext;
    data = temp->data;
    queue->front->pnext = temp->pnext;
    
    if (temp == queue->rear)
    {
        queue->rear = queue->front;
    }
    free(temp);
    printf("Delete %d from the queue successfully!\n", data);

    return true;
}
~~~
#### （六）队列长度
~~~c
int QueueLength(Pqueue queue)
{
    int count = 0;
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        count = 0;
    }
    Pnode start = queue->front->pnext;
    
    while (start != NULL)
    {
        count++;
        start = start->pnext;
    }
    printf("The queue length:%d \n", count);
}
~~~
#### （七）打印队列
~~~c
void ShowQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    Pnode start = queue->front->pnext;
    while (start != NULL)
    {
        printf("%d ", start->data);
        start = start->pnext;
    }
    putchar('\n');
}
~~~
#### （八）清空队列
~~~c
void ClearQueue(Pqueue queue)
{
    if (QueueIsEmpty(queue))
    {
        puts("The queue is empty!");
        return;
    }
    Pnode temp = queue->front;
    while (temp != NULL)
    {
        queue->front = queue->front->pnext;
        free(temp);
        temp = queue->front;
    }
    puts("clear the queue successfully!");
}
>>>>>>> a7c4693 (Update: blog)
~~~