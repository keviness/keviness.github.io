---
title: 队列链式存储实现（java实现）
date: 2020.12.18
tags:
  - Algorithms
  - Java
  - Queue Link
abbrlink: dcb6bac6
---
# 背景
&emsp;前面已经简单论述过它的顺序存储实现，接下来是它的链式存储实现，以下是一些实现思路，完整代码请用[随意门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_Java/DataStruct/Queue/QueueLink.java)
<!--more-->
### 一，实现代码
#### （一）队列结点形式
~~~java
class Node
{
    private int data;
    private String name;
    public Node next;

    public Node(String name, int data)
    {
        this.name = name;
        this.data = data;
    }

    public String toString()
    {
        return "The name:"+this.name+" The data:"+this.data;
    }
}
~~~
#### （二）初始化队列
~~~java
public Node front;
    public Node rear;
    public int length;

    public Queue()
    {
        this.front = new Node(null, 0);
        this.rear = this.front;
        this.length = 0;
    }
~~~
#### （三）检测队列为空
~~~java
public boolean isEmpty()
    {
        return this.rear == this.front;
    }
~~~
#### （四）入队操作
~~~java
public void EnQueue(Node target)
    {
        this.rear.next = target;
        this.rear = target;
        this.length++;
    }
~~~
#### （五）出队操作
~~~java
public Node DeQueue()
    {
        if (this.isEmpty())
        {
            System.out.println("The queue is empty!");
            return null;
        }
        Node temp = this.front.next;
        System.out.println("The enqueue node:"+temp);
        this.front.next = temp.next;
        if (temp == this.rear)
        {
            this.rear = this.front;
        }

        return temp;
    }
~~~

#### （六）打印队列
~~~java
public void show()
    {
        if (this.isEmpty())
        {
            System.out.println("The queue is empty!");
            return;
        }
        Node temp = this.front.next;
        while (temp != null)
        {
            System.out.println(temp);
            temp = temp.next;
        }
    }
~~~
