---
layout: post
title: "C语言堆排序算法"
date: 2013-03-29 15:50
comments: true
categories: C_Alogrithm
---
###背景###
>经典算法，必须熟悉，记录下来，便于当自己遗忘时查阅
>

<!--more-->

###代码实现###
>函数名：heap_fix_down
>
>功  能：将节点的较大值下拉
>
>参  数：a[]:排序的数组，i:父节点号，n:节点个数
>
	void heap_fix_down(int a[],int i,int n)
	{
		int temp;
		int j;
		temp = a[i];
		j = i*2+1; //i节点的左子节点
		while(j < n){
			if(j+1 < n && a[j+1] < a[j])  //j不是最后一个节点并且i的左子节点大于右子节点
				j++;
			if(a[j] >= temp) //i节点已经是最小堆
>				break;
>
			/* 如果i节点还不是最小堆 */
			a[i] = a[j];
			i = j; 
			j = 2*i+1;
		}
		a[i] = temp;
	}
>

>函数名：make_heap
>
>功  能：构建最小堆
>
>参  数：a[]:排序的数组，n:节点个数
>
	void make_heap(int a[],int n)
	{
		int i;
		//对每个父节点调整为最小堆
		for(i = n/2 -1;i >= 0;i--){
			heap_fix_down(a,i,n);
		}
	}
>

>函数名：sort_heap
>
>功  能：排序
>
>参  数：a[]:排序的数组，n:节点个数
>
	void sort_heap(int a[],int n)
	{
		int i;
		/* 每次将最小的那个值放到最后面，然后重新调整为最小堆 */
		for(i = n - 1;i >= 1;i--){
			/* 交换第一个和最后一个节点的值 */
			a[i] = a[0] ^ a[i];
			a[0] = a[0] ^ a[i];
			a[i] = a[0] ^ a[i];
>
>			heap_fix_down(a,0,i);
		}
	}
>

>函数名：main
>
>功  能：主函数
>
>参  数：无
>
	int main(void)
	{
		int i;
		int a[] = {2013,3,29,16,24,55};
		make_heap(a,6);
		sort_heap(a,6);
>
>		for(i = 0;i < 6;i++)
			printf("a[%d] = %d\t",i,a[i]);
>		printf("\n");
>
>		return 0;
	}
