---
title: C语言实例分析
toc: true
category: 编程相关
tags: Program
date: 2018-04-01 11:41:42
author:
keywords:
description:
source_url:
---
### 使用C语言打出26个字母：
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// int main(int argc, char *argv[])
// {
//     char a;
//     for (int i = 0; i < 26; i++)
//     {
//         a = 'a' + i;
//         printf("%c ", a);
//     }
//     return 0;
// }
int main()
{
    char c;

    int a = 4;
    int b = 4;

    printf("%d", a++);

    printf("%d", ++b);

    for (c = 'A'; c <= 'Z'; ++c)
        printf("%c ", c);

    return 0;
}

```
注释的代码是我自己写的，和示例代码相比显得比较基础，缺点也比较明显，就是要自己算出个数，就好比别人让你从`b`到`k`这种，你要一个个先数清楚才能知道具体个数，但是如果换成了示例代码，它完全不用管，因为只要你写相应的字母就可以了，根本不用自己去计算。

### 斐波那契数列
>*   第一个月初有一对刚诞生的兔子
>*   第二个月之后（第三个月初）它们可以生育
>*   每月每对可生育的兔子会诞生下一对新兔子
>*   兔子永不死去

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
    int n, i, i1 = 0, i2 = 1, nextitem;
    printf("请输n的值\n");
    scanf("%d", &n);

    for (int i = 0; i < n; i++)
    {
        printf("%d, ", i1);
        nextitem = i1 + i2;
        i1 = i2;
        i2 = nextitem;
    }

    return 0;
}
```
做这道题目的时候我们可以先枚举一些数据出来以便于我们找出其中的规律，0，1，1，2，3，5，8，13...我们发现从第三项开始的数值就等于前面两项之和。这时候我们只要分2种情况就可以很好的写出来了。
- 情况一
前2项的数值独立出来
- 情况二
第三项开始就是有规律的数据

注意！！！
```c
nextitem = i1 + i2;
i1 = i2;
i2 = nextitem;
```
的顺序不能搞反，不然不会得出正确的答案。

### 判断三个数中最大的值
```c
#include <stdio.h>

int main()
{
    double n1, n2, n3;

    printf("请输入三个数，以空格分隔: ");
    scanf("%lf %lf %lf", &n1, &n2, &n3);

    if( n1>=n2 && n1>=n3 )
        printf("%.2f 是最大数。", n1);

    if( n2>=n1 && n2>=n3 )
        printf("%.2f 是最大数。", n2);

    if( n3>=n1 && n3>=n2 )
        printf("%.2f 是最大数。", n3);

    return 0;
}
上面是示例代码，但是我们可以明显看出这样子判断比较愚蠢，虽然可以得到正确答案，但是这样子的代码看起来一点都不优雅。

这时候我想到之前教程里面有讲到结构体指针的代码
```c
#include <stdio.h>

int max(int x, int y)
{
    return x > y ? x : y;
}

int main(void)
{
    /* p 是函数指针 */
    int (* p)(int, int) = & max; // &可以省略
    int a, b, c, d;

    printf("请输入三个数字:");
    scanf("%d %d %d", & a, & b, & c);

    /* 与直接调用函数等价，d = max(max(a, b), c) */
    d = p(p(a, b), c);

    printf("最大的数字是: %d\n", d);

    return 0;
}

```







---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
