---
title: Softmax Function
use_math: true
---

$$
softmax(z)=[\cfrac{e^{z1}}{e^{z1}+e^{z2}+e^{z3}}, \cfrac{e^{z2}}{e^{z1}+e^{z2}+e^{z3}}, \cfrac{e^{z3}}{e^{z1}+e^{z2}+e^{z3}}]\\
$$

When we use Softmax Function, every value becomes a probability. They become a range of 0 to 1 and the sum of the result become 1. After the Softmax Function, we can use One-Hot Encoding to classify the output.