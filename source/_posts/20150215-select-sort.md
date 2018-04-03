---
title: 选择排序算法的时间复杂度
date: 2015-02-15 19:30:16
tags:
    - 选择排序
---

1、首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置
    
2、再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾

3、将两个排序好的子序列合并成一个最终的排序序列,直到所有元素均排序完毕

4、选择排序是非常稳定的

5、无论什么数据进去时间复杂度都是 O(n2)

6、所以用到它的时候，数据规模越小越好

<!--more-->

7、选择排序，实例代码如下.

    #include <stdio.h>

    #define LEN   10
    int data[LEN] = {10, 1, 6, 3, 4, 8, 2, 9, 5, 0};


    void print_data(void)
    {
        printf("%d %d %d %d %d %d %d %d %d %d\n",
                data[0], data[1], data[2], data[3],
                data[4], data[5], data[6], data[7],
                data[8], data[9]);
    }

    int main(int argc, char *argv[])
    {
        int i, j, temp;

        print_data();

        for(i = 0; i < LEN-1; i++){
            for(j = i+1; j < LEN; j++) {
                if(data[i] > data[j]) {//找最小的数
                    temp = data[i];
                    data[i] = data[j];
                    data[j] = temp;
                }
                print_data();
            }
        }

        return 0;
    }

