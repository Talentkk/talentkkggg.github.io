---
title: AGC001E
date: 2022/5/16
description: 　
---

有 $n$ 对数 $(a_i,b_i)$ ，求：
$$
\sum_{i=1}^{n}{\sum_{j=i+1}^{n}{a_i+b_i+a_j+b_j\choose a_i+a_j}}
$$
答案对 $10^9+7$ 取模。

$2\leq n\leq 200000,1\leq a_i,b_i\leq 2000$

考虑 $a_i+b_i+a_j+b_j\choose a_i+a_j$ 的组合意义，为：在网格图中 $(-a_i,-b_i)$ 走到 $(a_j,b_j)$ 的方案数，现在要求每对点的方案数和。

由于 $a_i,b_i\leq 2000$ ，考虑一个 $dp(i,j)$ ，表示对于所有 $(-a_x,-b_x)$ 到 $(i,j)$ 的路径数的总和是多少。转移为：$dp(i,j)=dp(i-1,j)+dp(i,j-1)$ ，最后求出 $\sum_{i}{dp(a_i,b_i)}$ 就是每对点的路径方案数总和。

注意题目中要求 $i< j$ ，所以减去 $i=j$ 的情况再除 $2$ 即可。

令 $v=\max(a_i,b_i)$,时间复杂度 $O(n+v^2)$ 。