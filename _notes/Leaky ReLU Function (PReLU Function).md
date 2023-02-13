---
title: Leaky ReLU Function (PReLU Function)
use_math: true
---

<img src="assets/Pasted image 20230213185347.png">
*Fig 1. Graph of ReLU function and PReLU function*

$$
PR(x)=\max(0.01x, x)
$$

PReLU is a transformed function of [[ReLU Function]]. It dosen't [[Saturation Problem|saturate]] and is Computationally efficient. Also, [[Dying ReLU Problem]] dosen't happen.

## Reference
- [Lecture 6. Activation Functions에 대해 알아보자](https://deepinsight.tistory.com/113)