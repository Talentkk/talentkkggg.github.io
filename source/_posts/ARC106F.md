---
title: ARC106F
date: 2021/12/10
description: 　
---

给出 $n$ 个点，以及数组 $d_i$ 。对于 $n$ 个点的一棵树，假设每个点的度数是 $p_i$ ，则它的代价是 $\prod {d_i^\underline{p_i}}$ 。求所有生成树的代价和，对 $998244353$ 取模。

$1\leq n\leq 2\times 10^5$ 

对于生成树，想到 `prufer` 序列，而一个点的度数 $p_i$ 正是 `prufer` 序列中 $i$ 出现的次数加一。故对于一个度数序列 $p_1,p_2,...,p_n$ ，设 $q_i=p_i-1$ 其中 $\sum{p_i}=2n-2$ ，对应的 `prufer` 序列有 $(n-2)!\times\prod{\frac{1}{q_i!}}$ 。所以答案变成：
$$
\sum_{\sum{q_i}=n-2}{(n-2)!\times \prod \frac{d_i!}{q_i!\times(d_i-q_i-1)!}}=\sum_{\sum{q_i}=n-2}{(n-2)!\times \prod{d_i} \prod{d_i-1\choose q_i}}
$$
整理下式子变成：
$$
(n-2)!\times \prod{d_i}\times \sum_{\sum{q_i}=n-2}{\prod{d_i-1\choose q_i}}
$$
发现对于最后一项，相当于有 $i$ 类物品，每类有 $d_i-1$ 个，现在要从中选 $n-2$ 个的方案数，其实就是 $\sum{d_i}-n \choose n-2$ ，式子变成了：
$$
(n-2)! \times \prod{d_i} \times {\sum{d_i}-n \choose n-2}
$$
直接计算即可。