---
title: Vanishing Gradient Problem
---

In [[Deep Learning]], it looks as if the more layers we have, the better the ai become. But this is not true because of the Vanishing Gradient Problem. When you encounter Vanishing Gradient, during [[Back Propagation]] the farther it becomes from the output layer, the less the gradient become. This is often due to [[Activation Function]], especially [[Sigmoid Function]].

<img src="assets/Pasted image 20230213161710.png" />
*Fig 1. Vanishing Gradient*

## Reference
- [기울기 소실(Vanishing Gradient)의 의미와 해결방법](https://heytech.tistory.com/388)
- [Vanishing gradient problem - Wikipedia](https://en.wikipedia.org/wiki/Vanishing_gradient_problem)