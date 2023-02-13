---
title: Normalization
use_math: true
---

<img src="assets/Pasted image 20230213224839.png">
*Fig 1. Difference of Unnormalized and Normalized Data*

In un normalized data set, cost graph is elongated. And this may cause learning to be focused only on some columns.

## Noramlization Formula
$$
x'=\cfrac{x-x_{min}}{x_{max}-x_{min}}
$$
Normalization makes values into a range of 0 to 1. This makes learning to not focus on certain columns.