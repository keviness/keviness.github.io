---
title: 栈的顺序存储实现（Java实现）
date: 2020.12.17
tags:
  - Stack Sequence
  - Java
  - Algorithms
abbrlink: 2b04c71a
---
# 背景
&emsp;前面已经利用Java进行了栈的链式存储实现，接下来是它的顺序存储实现，以下是一些实现思路，完整代码请用[神奇的随意门~](https://github.com/keviness/Algorithms/blob/master/Algorithms_Java/DataStruct/Stack/stackLink.java)
<!--more-->
### 一，实现代码
#### （一）数据形式
~~~java
class Node
{
    public int data;
    public String name;

    public Node(String name, int data)
    {
        this.name = name;
        this.data = data;
    }

    public String toString()
    {
        return "name:"+this.name+" data:"+this.data;
    }
}
~~~
#### （二）初始化
~~~java
public Node[] stack;
public int top;
public int length;

public Stack(int length)
{
    stack = new Node[length];
    this.top = -1;
    this.length = length;
}
~~~
#### （三）检测为空或为满
~~~java
public boolean isEmpty()
    {
        return this.top == -1;
    }

public boolean isFull()
    {
        return this.top == this.length;
    }
~~~
#### （四）压栈操作
~~~java
public void push(Node target)
    {
        if (this.isFull())
        {
            System.out.println("The stack is full!");
            return;
        }
        this.top++;
        stack[this.top] = target;
        
        System.out.println("The push into the stack successfully!");
    }
~~~
#### （五）出栈操作
~~~java
public Node pop()
    {
        if (this.isEmpty())
        {
            System.out.println("The stack is empty!");
            return null;
        }
        Node temp = stack[this.top];
        this.top--;
        System.out.println("Pop successfully!");;
        return temp;
    }
~~~