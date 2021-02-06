---
title: 常用查找算法（Java实现）
date: 2020.12.27
tags:
  - Algorithms
  - Java
  - Search
abbrlink: dedb6031
---
# 背景
&emsp;怎样在一堆混乱的数据中查找到需要的数据呢？查找算法就显得很重要了。以下是常见的查找算法实现，看实现的完整代码请用[随意门~](https://github.com/keviness/Algorithms/tree/master/Algorithms_Java/Search)
<!--more-->

## 一，顺序查找
>* Sequence Search
>* 说明：顺序查找适合于存储结构为顺序存储或链接存储的线性表。
### （一）基本思想
>* 顺序查找也称为线形查找，属于无序查找算法。
>* 从数据结构线形表的一端开始，顺序扫描，依次将扫描到的结点关键字与给定值k相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于k的结点，表示查找失败。

### （二）复杂度分析　
>* 查找成功时的平均查找长度为：（假设每个数据元素的概率相等） ASL = 1/n(1+2+3+…+n) = (n+1)/2 ;
>* 当查找不成功时，需要n+1次比较，时间复杂度为O(n);
>* 所以，顺序查找的时间复杂度为O(n)。

### （三）代码实现
~~~java
public static int SequenceSort(int[] arr, int value)
{
    for (int i=0; i<SIZE; i++)
    {
        if (arr[i] == value)
            return i;
    }
    return -1;
}
~~~

## 二，折半查找
>* Binary Search
>* 说明：元素必须是有序的，如果是无序的则要先进行排序操作。

### （一）基本思想
>* 也称为是折半查找，属于有序查找算法。
>* 用给定值k先与中间结点的关键字比较，中间结点把线形表分成两个子表，若相等则查找成功；若不相等，再根据k与该中间结点关键字的比较结果确定下一步查找哪个子表，这样递归进行，直到查找到或查找结束发现表中没有这样的结点。

### （二）复杂度分析
>* 最坏情况下，关键词比较次数为log2(n+1)，且期望时间复杂度为O(log2n)。
### （三）代码实现
~~~java
/*** 非递归版本 ***/
public static int BinarySearch(int[] a, int value, int n)
{
    int low, high;
    low = 0;
    high = n-1;

    while(low <= high)
    {
        int mid = (low+high)/2;
        printf("low:%d\n", low);
        printf("high:%d\n", high);
        printf("middle:%d\n", mid);
        if(a[mid] == value)
            return mid;
        if(a[mid] > value)
            high = mid-1;
        if(a[mid] < value)
            low = mid+1;
    }
    return -1;
}
/*** 递归实现 ***/
public static int BinarySort(int[] arr, int value, int low, int high)
{
    if (low > high)
        return -1;
    int middle = (low+high)/2;
    if (arr[middle] == value)
        return middle;
    if (arr[middle] > value)
        return BinarySort(arr, value, low, high-1);
    if (arr[middle] < value)
        return BinarySort(arr, value, middle+1, high);
}
~~~

## 三，插值查找
### （一）基本思想
>* 基于二分查找算法，将查找点的选择改进为自适应选择，可以提高查找效率。当然，差值查找也属于有序查找。
>* mid=low+(key-a[low])/(a[high]-a[low])*(high-low)
>* 将上述的比例参数1/2改进为自适应的，根据关键字在整个有序表中所处的位置，让mid值的变化更靠近关键字key，这样也就间接地减少了比较次数。
### （二）复杂度分析
>* 查找成功或者失败的时间复杂度均为：O(log2(log2n))。
### （三）代码实现
~~~java
/*** 非递归版本 ***/
public static int InsertSearch(int[] arr, int value, int n)
{
    int low, high, mid;
    low = 0;
    high = n-1;

    while(low <= high)
    {
        //自适应获取应该取得的索引
        mid = low + ((value-arr[low])/(arr[high]-arr[low]))*(high-low);
        printf("low:%d\n", low);
        printf("high:%d\n", high);
        printf("middle:%d\n", mid);
        if(arr[mid] == value)
            return mid;
        if(arr[mid] > value)
            high = mid-1;
        if(arr[mid] < value)
            low = mid+1;
    }
    return -1;
}

/*** 递归实现 ***/
public static int InsertSort(int[] arr, int value, int low, int high)
{
    if (low > high)
        return -1;
    int middle = low + (value-arr[low])/(arr[high]-arr[low])*(high-low);
    if (arr[middle] == value)
        return middle;
    if (arr[middle] > value)
        return InsertSort(arr, value, low, high-1);
    if (arr[middle] < value)
        return InsertSort(arr, value, middle+1, high);
}
~~~

## 四，分块查找
### （一）基本思想
>* 也叫索引顺序查找，算法实现除了需要查找表本身之外，还需要根据查找表建立一个索引表。
>* 建立的索引表要求按照关键字进行升序排序，查找表要么整体有序，要么分块有序。 分块有序指的是第二个子表中所有关键字都要大于第一个子表中的最大关键字，第三个子表的所有关键字都要大于第二个子表中 的最大关键字，依次类推。
### （二）复杂度分析
>* 分块查找算法的运行效率受两部分影响：查找块的操作和块内查找的操作。
>* 查找块的操作可以采用顺序查找，也可以采用折半查 找（更优）；块内查找的操作采用顺序查找的方式。
>* 相比于折半查找，分块查找时间效率上更低一些；相比于顺序查找，由于在子表中进行，比较的子表个数会不同程度的减少，所有分块查找算法会更优
>* 总体来说，分块查找算法的效率介于顺序查找和折半查找之间。
### （三）代码实现
~~~java
public static int search(int key, int[] a)
{
    int i, startValue;
    i = 0;
    while (i<3 && key>newIndex[i].key) 
    { 
        //确定在哪个块中，遍历每个块，确定 key 在哪个块中
        i++;
    }
    if (i>=3) 
    { 
        //大于分得的块数，则返回 0
        return -1;
    }
    startValue = newIndex[i].start; //startValue 等于块范围的起始值
    while (startValue <= startValue+5 && a[startValue]!=key)
    {
        startValue++;
    }
    if (startValue>startValue+5) 
    { 
        //如果大于块范围的结束值，则说明没有要查找的数
        return -1;
    }

    return startValue;
}
~~~

## 五，斐波那契查找
### （一）基本思想
>* 也是二分查找的一种提升算法，通过运用黄金比例的概念在数列中选择查找点进行查找，提高查找效率。同样地，斐波那契查找也属于一种有序查找算法。
斐波那契查找与折半查找很相似，他是根据斐波那契序列的特点对有序表进行分割的。他要求开始表中记录的个数为某个斐波那契数小1，及n=F(k)-1;

>* 开始将k值与第F(k-1)位置的记录进行比较(及mid=low+F(k-1)-1),比较结果也分为三种：
>* 1）相等，mid位置的元素即为所求
>* 2）>，low=mid+1,k-=2;
>* 说明：low=mid+1说明待查找的元素在[mid+1,high]范围内，k-=2 说明范围[mid+1,high]内的元素个数为n-(F(k-1))= Fk-1-F(k-1)=Fk-F(k-1)-1=F(k-2)-1个，所以可以递归的应用斐波那契查找。
>* 3）<，high=mid-1,k-=1。
>* 说明：low=mid+1说明待查找的元素在[low,mid-1]范围内，k-=1 说明范围[low,mid-1]内的元素个数为F(k-1)-1个，所以可以递归 的应用斐波那契查找。
### （二）复杂度分析
>* 最坏情况下，时间复杂度为O(log 2 n)，且其期望复杂度也为O(log 2 n)。
### （三）代码实现
~~~java
/*构造一个斐波那契数组*/ 
public static void Fibonacci(int[] F)
{
    F[0] = 0;
    F[1] = 1;
    for(int i=2; i<max_size; ++i)
        F[i] = F[i-1] + F[i-2];
}

/*定义斐波那契查找法*/  
public static int FibonacciSearch(int[] a, int n, int key)  
{
    int low = 0;
    int high = n-1;
    int F[max_size];
    Fibonacci(F);   //构造一个斐波那契数组F 

    int k = 0;
    while(n > F[k]-1) //计算n位于斐波那契数列的位置
        ++k;
 
    int temp[F[k]-1];//将数组a扩展到F[k]-1的长度
    memcpy(temp, a, n*sizeof(int));
 
    for(int i=n; i<F[k]-1; ++i)
        temp[i] = a[n-1];
  
    while(low <= high)
    {
        int mid = low + F[k-1] - 1;
        if(key < temp[mid])
        {
            high = mid - 1;
            k-=1;
        }
        else if(key > temp[mid])
        {
            low = mid + 1;
            k-=2;
        }
        else
        {
            if(mid < n)
                return mid; //若相等则说明mid即为查找到的位置
            else
                return n-1; //若mid>=n则说明是扩展的数值,返回n-1
        }
    }  
    return -1;
}
~~~