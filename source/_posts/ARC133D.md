---
title: ARC133D
date: 2022/1/16
description: 　
---

给出整数 $l,r,v$ ，求有多少对 $(x,y)$ 满足：

+ $l\leq x\leq y\leq r$
+ $x\oplus (x+1)\oplus...\oplus y= v$

答案对 $998244353$ 取模。

$1\leq l\leq r\leq 10^{18},0\leq v\leq 10^{18}$

记 $f(x)$ 为 $0$ 到 $x$ 的前缀异或和。

一个重要的观察是，$f(x)$ 的取值与其模 $4$ 的余数有很大关系，具体为：

+ $x \bmod 4=0,f(x)=x$
+ $x\bmod 4=1,f(x)=1$
+ $x\bmod 4=2,f(x)=x+1$
+ $x\bmod 4=3,f(x)=0$

这个结论可以归纳证明。

显然问题可以通过容斥转化为这样一个问题：求有多少对 $(x,y)$ 满足 $0\leq x\leq a,0\leq y\leq b$ ，且 $f(x)\oplus f(y)=v$ 。

于是我们可以按照 $x$ 和 $y$ 