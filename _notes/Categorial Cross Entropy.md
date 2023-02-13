---
title: Categorial Cross Entropy
use_math: true
---

$$
\begin{align}
D(S, L)=-\sum_{i=1}^nL_i\log S_i\\
\mathcal{L}=\cfrac{1}{n}\sum_{i=1}^nD(S(W\cdot X +B), L_i)
\end{align}
$$
- S : Result from Softmax function
- L : Actual Classification