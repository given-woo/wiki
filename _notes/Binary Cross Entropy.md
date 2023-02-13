---
title: Binary Cross Entropy
use_math: true
---

<img src="assets/Pasted image 20230213210457.png">
$$
\begin{align*}
C(H(x), y) &= 
\begin{cases}
-log(H(x))\space \space(y=1) \\
-log(1-H(x))\space \space (y=0)
\end{cases} \\
&= -ylog(H(x))-(1-y)log(1-H(x)) \\
cost(W)&=\cfrac{1}{m}\sum C(H(x), y)\\
&=-\cfrac{1}{m}\sum\big\{ ylog(H(x))+(1-y)log(1-H(x))\big\}
\end{align*}
$$