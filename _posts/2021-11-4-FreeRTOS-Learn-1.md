---
layout: post
title: FreeRTOS学习教程（一）
description: FreeRTOS简介
categories:
  - FreeRTOS
  - M4
  - 实时操作系统
---

排序是计算机程序设计中一种重要的操作，功能是将一个元素数据的任意序列重新排列成一个按关键字的有序序列。

这篇文章是记录我学习和巩固常见的几种插入排序算法，参考教程为严蔚敏老师的[《数据结构（C语言版）》](https://pan.baidu.com/s/1kVCxIhL)。

## 直接插入排序

直接插入排序是一种最简单的排序方法，它的基本操作是将一个记录插入到已经排序好的有序表中，从而得到一个新的，插入了新的记录的有序表。

例如：现在有一个有序表：10、20、30、40。现在要记录35插入到这个有序表中。那么首先要在这个有序表中确定新记录的位置，然后进行插入，由于30<35<40；那么应该讲35插入到30和40之间，新得到的有序表为：10、20、30、35、40。

其实现算法如下：

```c
void InsertSort(int *num,int numSize)
{
	int i,j,k;
	for(i = 1; i < numSize; i++)
	{
		for(j = i - 1; j>= 0; j++)
		{
			if(a[j] < a[i]) break;
		}
		if(j != i - 1)
		{
			int temp = a[i];
			for(k = 0; k > j; k--) a[k + 1] = a[k];
			a[k+1] = temp;
		}
	}
}
```

从空间上来看，他只需要一个辅助空间，当序列本身正序排列时，所需要的比较次数最少，为n-1次；当序列本身逆排序时，记录移动次数达到最大值，为(n+2)(n-1)/2。由此直接插入排序的时间复杂度为O(n<sup>2</sup>)。

## 折半插入排序

由于插入排序是在一个有序表内进行查找，因此可以用二分法进行查找。

其实现算法如下：

```c
void BinsertSort(int *num, int numSize)
{
	int i, j, temp, m, left, right;
	for (i = 1; i < numSize; i++)
	{
		temp = num[i];
		left = 0; right = i-1;
		while (left <= right)
		{
			m = (left +right) / 2;
			if(num[m] > temp) right = m-1;
			else left = m+1;
		}
	}
	for (j = i-1; j>=right+1; j--)num[j+1] = num[j];
	num[j+1] = temp;
}
```

折半插入排序仅减少了关键字比较所用的时间，而记录此时不变，所以折半插入排序的时间复杂度仍为O(n<sup>2</sup>)。

## 2路插入排序

2路插入是在折半插入的基础上进行改进。折半插入在原先直接插入的基础上改进，通过折半查找，以较少的比较次数就找到了要插入的位置，但是在插入的过程中仍然没有减少移动次数，所以2路插入在此基础上改进，减少了移动次数，但是仍然并没有避免移动记录（如果要避免的话还是得改变存储结构）那么如何减少的移动次数？常规的一个数组{2, 7， 8，10，15 ，29，30， 40，50，66，70，80}，如果插入9，那么按照常规的折半查找后，需要移动记录9次，这是因为我们只能够在一个方向上插入。因此我们设定一个辅助数组A，大小是原来数组相同的大小，将A[0]设为第一个原数组第一个数，通过设置first和final指向整个有序序列的最小值和最大值，即为序列的尾部和头部，并且将其设置位一个循环数组，这样就可以进行双端插入。此时原数组只需往左边移动3次。之所以能减少移动次数的原因在于可以往2个方向移动记录，故称为2路插入。A[0]的前面是个有序序列，后面也是有序序列，整个也是有序序列。

```c
int ChangeTwoInsertSort()
{
	//ehance the two insert sort
	int final = 0;
	int first = 0;
	const int iLenght = iCount -1;
 
	int iTempBuff[iLenght] = {0};
	iTempBuff[0] = iRawBuff[1];
	//先和temp[0]比较从而以其为分界线
	for (int i = 2; i <= iLenght; i++ )
	{
		if (iRawBuff[i] >= iTempBuff[0])
		{
			//that means ,输入右半部
			if (iRawBuff[i] >=iTempBuff[final])
			{
				//大于当前最大值
				final++;
				iTempBuff[final] = iRawBuff[i];
			}
			else
			{
				//小于当前最大值，但大于分界线值，左移，但不超过零
				int j = final++;
				while ((iTempBuff[j]>=iRawBuff[i])&&(j>=0))
				{
					iTempBuff[j+1] = iTempBuff[j];
					j--;
 
				}
				iTempBuff[j+1] = iRawBuff[i];
			}
 
		}
		if (iRawBuff[i] < iTempBuff[0])
		{
			//that means 输入左半部
			if (iRawBuff[i] >= iTempBuff[first])
			{
				//
				int j = first--;
 
				while (j<=iLenght&&iTempBuff[j]<=iRawBuff[i])
				{
					iTempBuff[j-1] = iTempBuff[j];
					j++;
				}
				iTempBuff[j-1] = iRawBuff[i];
			}
			if (iRawBuff[i] < iTempBuff[first])
			{
				//小于当前最小
				first = (first-1+iLenght)%iLenght;
				iTempBuff[first] = iRawBuff[i];
			}
		}
		printf("第%d趟：\n",i);
		for(int k = 0; k < iLenght; k++)
		{
			std::cout<<iTempBuff[k]<<"\t";
		}
		std::cout<<"\n";
	
	}
	//数据导入原始数组
	for(int i = 0; i< iLenght; i++)
	{
        iRawBuff[i+1] = iTempBuff[(first++)%iLenght];
	}
 
	return 0;
}


```

代码原文链接：[https://blog.csdn.net/onedreamer/article/details/6745006](https://blog.csdn.net/onedreamer/article/details/6745006)

二路插入排序中，移动记录次数约为n<sup>2</sup>/8，因此，2路插入排序法只能减少移动记录次数，而不能绝对避免移动记录，时间复杂度仍为O(n<sup>2</sup>)。

