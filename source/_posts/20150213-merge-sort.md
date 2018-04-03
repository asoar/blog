---
title: 归并排序算法的时间复杂度
date: 2015-02-13 09:39:49
tags:
    - 归并排序
---

1、归并排序算法采取分而治之 (Divide-and-Conquer)的策略.
    
    $ 时间复杂度为: Θ(nlgn)

2、把长度为n的输入序列分成两个长度为n/2的子序列

3、对这两个子序列分别采用归并排序，这是一个递归的过程

4、将两个排序好的子序列合并成一个最终的排序序列

<!--more-->

5、归并排序，实例代码如下.

    #include <stdio.h>

    #define LEN   10
    int data[LEN] = {10, 1, 6, 3, 4, 8, 2, 9, 5, 0};

    void print_data(const char *head, int start, int mid, int end)
    {
        printf("%s (%d-%d, %d-%d) %d %d %d %d %d %d %d %d %d %d\n",
                head, start, mid, mid+1, end,
                data[0], data[1], data[2], data[3],
                data[4], data[5], data[6], data[7],
                data[8], data[9]);
    }

    void merge(int start, int mid, int end)
    {
        int n1 = mid - start + 1;
        int n2 = end - mid;
        int left[n1], right[n2];
        int i, j, k;

        for (i = 0; i < n1; i++) /* left holds a[start..mid] */
            left[i] = data[start+i];
        for (j = 0; j < n2; j++) /* right holds a[mid+1..end] */
            right[j] = data[mid+1+j];
        i = j = 0;
        k = start;
        while (i < n1 && j < n2)
            if (left[i] < right[j])
                data[k++] = left[i++];
            else
                data[k++] = right[j++];

        while (i < n1) /* left[] is not exhausted */
            data[k++] = left[i++];

        while (j < n2) /* right[] is not exhausted */
            data[k++] = right[j++];
    }
   
    void sort(int start, int end)
    {
        int mid;

        if (start < end) {
            mid = (start + end) / 2;
            print_data("sort", start, mid, end);

            sort(start, mid);
            sort(mid+1, end);
            merge(start, mid, end);
            print_data("merge", start, mid, end);
        }
    }

    int main(int argc, char *argv[])
    {
        sort(0, LEN-1);
        return 0;
    }



