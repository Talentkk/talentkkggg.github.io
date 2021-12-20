---
title: ABC176F
date: 2021/12/21
description: 　
---

## ABC176F

有 $3n$ 个数 $a_i$ 排成一排。进行 $n-1$ 次如下操作：

+ 对最左边的 $5$ 个数重排，拿走最左边的三个。如果这三个数相同，则获得一分。

在操作结束后，如果剩下的三张牌相同，获得一分。

求可获得的最大分数。

$1\leq n\leq 2000$ 

容易想到暴力的 $dp$ 是：设 $dp(i,x,y)$ 表示考虑前 $i$ 次操作后，最左边的两个数是 $x$ 和 $y$ 的最大得分。转移时，分三类情况讨论：

+ $x,y$ 都不变
+ $x,y$ 中一个改变
+ $x,y$ 都改变

时间复杂度 $O(n^3)$ 。

考虑优化，如果我们把 $dp_i[x][y]$ 看成一个矩阵，则 $i\rightarrow i+1$ 的过程中，矩阵的变化量是 $O(n)$ 的。我们只要维护矩阵的每行最大值，每列最大值，以及全局最大值，就可以 $O(n)$ 转移。总时间复杂度 $O(n^2)$ 。