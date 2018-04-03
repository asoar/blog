---
title: 插入排序的时间复杂度
date: 2015-02-12 20:14:01
tags:
    - 插入排序
---

1、插入排序算法采取增量式(Incremental)的策略解决问题，
   每添加一个元素到已排序的子序列中，会逐步将整个数组排序完.
    
    $ 所以插入排序的时间复杂度为: O(n*n)

2、正向插入排序，实例代码如下.

    #include <stdio.h>

    #define LEN   10
    int data[LEN] = {10, 1, 6, 3, 4, 8, 2, 9, 5, 0};

    extern void print_data(void);

    int main(int argc, char *argv[])
    {

        int i, j, temp;

        for(j = 1; j < LEN; j++) {  //LEN-1
            print_data();
            temp = data[j];         //a1
            i = j - 1;              //a2
            while(i >= 0 && data[i] > temp){//m
                data[i+1] = data[i];//a3
                i--;                //a4
            }
            data[i+1] = temp;       //a5
        }
        print_data();

        return 0;
    }

    void print_data(void)
    {
        for(int i = 0; i < LEN; i++)
            printf("%d ", data[i]);
        printf("\n");
    }


<!--more-->


3、解决同一个问题可以有很多种算法，比较算法的好坏主要标准就是时间复杂度.

    1)实例中计算复杂度时忽略print_data和printf输出语句

    2)最外层的for循环执行了 LEN-1 次，内层while循环假设执行m次，
      主要取决于原始数据，这里将括号内的比较和赋值的时间忽略了，
      总的执行时间粗略估计: (LEN-1)(a1+a2+a5+m(a3+a4))

    3)最好的情况下(即数据已正向排好)执行时间为:
      (a1+a2+a5)(LEN-1) = (a1+a2+a5)LEN - (a1+a2+a5)
      表示成: a*LEN - b，是LEN的线性函数

    4)最坏的情况下(数据逆向排好)执行时间为:
      (LEN-1)(a1+a2) + (a3+a4)(LEN*(LEN-1)/2)

    5)最坏和随机平均情况下都可以表示成:
      a*LEN*LEN + b*LEN + c  是LEN的二次函数

    6)分析算法时间复杂度时，主要关心最坏情况，该算法当LEN愈来愈大时，
      常数时间可以忽略不计，所以该插入排序算法的时间复杂度为:
      O(LEN*LEN) O表示小于等于
