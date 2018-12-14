---
title: 一个简单的C语言程序Bug引起的思考
toc: true
category: 编程相关
tags: Program
date: 2018-11-23 13:53:00
author:
keywords:
description:
source_url:
---

### 源代码

```

#include <stdio.h>

#include <stdlib.h>

#include <string.h>

typedef struct student

{

char name[50]; //姓名

unsigned int age;

int score;

} student;

`void print_stu(student *stu, int n)`

{

int i = 0;

printf("name\tage\tscore\n");

for (int i = 0; i < n; i++)

{

printf("%s\t%d\t%d\n", stu[i].name, stu[i].age, stu[i].score);

}

}

`void sort_stu(student *stu, int n)`

{

int i = 0;

int j = 0;

student temp;

for (int i = 0; i < n - 1; i++)

{

for (int j = 0; j < n - i- 1; j++)//之前写成i<n-j-1

{

if (stu[j].age > stu[j + 1].age)

{

printf("--\n");

temp = stu[j];

stu[j] = stu[j + 1];

stu[j + 1] = temp;

printf("-1--%d--%d\n", i, j);

}

else if (stu[j].age == stu[j + 1].age)

{

printf("-2-\n");

if (stu[j].score > stu[j + 1].score)

temp = stu[j];

stu[j] = stu[j + 1];

stu[j + 1] = temp;

}

}

}

}

`int main(int argc, char *argv[])`

{

student stu[5] =

{

{"mike", 18, 86},

{"jake", 41, 47},

{"itgoyo", 24, 86},

{"mkosto", 18, 83},

{"luck", 41, 86}

};

int n = sizeof(stu) / sizeof(*stu);

printf("n=%d\n", n);

print_stu(stu, n);

sort_stu(stu, n);

print_stu(stu, n);

return 0;

}

```

昨晚在做一个简单的C代码Demo的时候遇到了一个比较常见的bug，就是简单的冒泡排序，居然没有出现我想要的答案，然后问了一下寝室的C大佬，然后他过来让我调试一下，我说VSCode怎么进入Debug模式，他说可以进，但是比较复杂，那就在循环里打几个printf看看。然后我就在循环里打了，后面被他说没打对位置。然后他看我printf只循环了一次然后那会他就知道可能出现的问题是哪里了，然后他没有告诉我答案，然后他问，你觉得可能的问题出现在哪里，我说不知道，应该没错的啊，冒泡排序就是两个循环嵌套，然后逐个两两相比较最后得到正确的排序。其实那会那会觉得自己挺傻的，回了这么一句话。如果自己没错，那为什么不会得出正确的答案？所以问题肯定是有的，但是你就是不想承认自己的错误，而且一直觉得自己是对的。后面他让我查一下冒泡排序的代码是怎么样子的，自己比对一下，看看是哪里错了。然后我很熟练的搜了一下C语言冒泡排序，然后出来了，然后我就看比对，感觉没什么错误啊，我那会的重点就是冒泡就是两个for循环嵌套，我是两个，写法没错呀。但是错误的原因根本不是在这里，我没有分析为什么冒泡只会for循环只跑一次，只跑一次的话就可能是逻辑条件有错啊，不然怎么会只循环一次。后面发现是我的第二个for循环中的j写错了，本来是j=n-i-1的，但我却写成了j=n-j-1。

### 个人思考

明明是一个简单的错误，很多人都没有看出来，我们很多时候都是只凭自己主观的印象来找错误，但不是按照科学的逆序倒推排除法。其实现象已经知道了，就是for循环只执行一次，我们就应该从为什么只会执行一次入手，缩小错误范围，便于我们快速定位错误位置。

查找bug的步骤：

*   复现bug现象

*   缩小会产生bug的范围

*   调试

*   代码验证

*   Fixed





---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
