---
title: ABC230H
date: 2021/12/17
description: 　
---

现在有 $k$ 种重量分别为 $w_i$ 的金块，每种无限个，以及无限个重量为 $1$ 的背包。一个背包中可以装 $0$ 个或多个非空背包以及任意数量的金块，问对于 $i=2,3,...,W$ ，大小为 $i$ 的背包有多少种。

+ 两个金块被认为不同当且仅当它们重量不相同。
+ 两个背包被认为相同当且仅当它们中金块和背包构成的**可重集**相同。

$2\leq W\leq 2.5\times 10^5,1\leq k\leq W$ 



设 $h_x$ 表示是否有重量为 $x$ 的物品，设 $i=x$ 时的答案为 $f_x$ ，记 $f_x$ 的普通生成函数为 $F(x)$ ，则有：
$$
F(x)=x\prod_{i\geq1}{\frac{1}{(1-x^i)^{f_i+h_i}}} -x
$$
这里的最后减去 $x$ 是因为 $f_x$ 的定义是非空的背包。

移项后得到：
$$
F(x)+x=x\prod_{i\geq 1}{\frac{1}{(1-x^i)^{f_i+h_i}}}
$$
两边同时取 $\ln$ ：
$$
\ln(F(x)+x)=\ln(x)-\sum_{i\geq 1}{\ln(\frac{1}{1-x^i})\times(f_i+h_i)}
$$
两边同时求导并化简得到：
$$
xF'(x)=F(x)+(F(x)+x)\sum_{i\geq 1}{(f_i+h_i)\times\frac{ix^i}{1-x^i}}
$$
因为：
$$
[x^n]\sum_{i\geq 1}{(f_i+h_i)\times\frac{ix^i}{1-x^i}}\\=[x^n]\sum_{i\geq 1}{(f_i+h_i)ix^i(1+x^i+x^{2i}+...)} \\=[x^n]\sum_{j|n} j(f_j+h_j)
$$
对等式取 $x^n$ 项系数得到：
$$
nf_n=f_n+\sum_{i=1}^{n-1}{(f_i+[i=1])\sum_{j|n-i}{j(h_j+f_j)}}
$$
记 $g_n=\sum_{i|n}{i(h_i+f_i)}$ ，则：
$$
f_n=\frac{1}{n-1}(\sum_{i=1}^{n-1}{f_ig_{n-i}+g_{n-1}})
$$
初始值为 $f_1=0$ ，分治 `fft` 即可。

