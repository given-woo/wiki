---
title: Regularization
use_math: true
---

$$
L=\cfrac{1}{n}\sum_{i=1}^nD(S(W\cdot X+B))+\lambda\sum_{i=1}^nW^2\\
$$
Regularization is not having too big numbers in the weight. By adding $\lambda\sum_{i=1}^nW^2$ ($\lambda$ : Regularization Strength), we prevent weight from getting to big. 