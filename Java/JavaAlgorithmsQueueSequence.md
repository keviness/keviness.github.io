---
title: 队列顺序存储实现（java实现）
date: 2020.12.19
tags:
  - Java
  - Algorithms
  - Queue Sequence
abbrlink: f8b7c9ad
---
# 背景
&emsp;在算法中队列有顺序存储（连续存储）和链式存储（离散存储）两种方式。其中顺序存储必须要用循环队列的形式实现，具体实现可以走[随意门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_Java/DataStruct/Queue/QueueSequence.java)
<!--more--->
### 一，实现代码
#### （一）队列数据形式
~~~java
class Node
{
    private int data;
    private String name;
    
    public Node(String name, int data)
    {
        this.name = name;
        this.data = data;
    }

    public String toString()
    {
        return "The name:"+this.name+" the data:"+this.data;
    }
}
~~~
#### （二）初始化队列
~~~java
public int length;
public int count;
public int front;
public int rear;
public Node[] queue;
public Queue(int length)
{
    this.length = length;
    queue = new Node[this.length];
    this.front = 0;
    this.rear = 0;
}
~~~
#### （三）检测队列为空或已满
~~~java
public boolean isEmpty()
{
    return this.front == this.rear;
}

public boolean isFull()
{
    return (this.rear+1)%this.length == this.front;
}
~~~
#### （四）入队出队操作
~~~c
public void EnQueue(Node target)
{
    if (this.isFull())
    {
        System.out.println("The queue is full!");
        return;
    }
    this.queue[this.rear] = target;
    this.rear = (this.rear+1)%this.length;
}

public Node DeQueue()
{
    if (this.isEmpty())
    {
        System.out.println("The queue is empty!");
        return null;
    }
    Node temp = this.queue[this.front];
    this.front = (this.front+1)%this.length;

    return temp;
}
~~~

#### （五）打印队列
~~~java
public void show()
{
    if (this.isEmpty())
    {
        System.out.println("The queue is empty!");
        return;
    }
    int i = this.front;
    while (i != this.rear)
    {
        System.out.println(this.queue[i]);
        i = (i+1)%this.length;
    }
}
~~~