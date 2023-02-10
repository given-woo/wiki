---
title: Back Propagation
---

# Back Propagation

*Backprogation* is a general algorithm to train Aritificial Neural Networks today. We can update weights and train Multi-Layer-Network using this method. This solved the [[XOR Problem]].

The backprogration algorithm was originally introduced in the 1970s, but its importance wasn't fully appreiciated until a [famus 1986 paper](http://neuralnetworksanddeeplearning.com/chap2.html) by David Rumelhart, Geoffrey Hinton, and Ronald Williams. That paper describes several neural networks where backpropagation works far faster than earlier approaches to learning, making it possible to use neural nets to solve problems which had previously been insoluble. Today, the backpropagation algorithm is the workhorse of learning in neural networks.

## a. Example of Back Propagation

![[Pasted image 20230210152912.png]]
*Fig 1. A example Neural Network. Activation function is Sigmoid*

After getting the error $E=0.072$ from [[Forward Propagation]], Let's  update $w_{10}^1$ . To do this, we have to know how much impact $w_{10}^1$ ahd on $E$. We can use [[Chain Rule]] to solve this.

![[Pasted image 20230210153843.png]]
$$
\cfrac{\partial E}{\partial w_{10}^1}=\cfrac{\partial E}{\partial a_{20}}\cdot\cfrac{\partial a_{20}}{\partial z_{20}}\cdot\cfrac{\partial z_{20}}{\partial w_{10}^1}
$$
$$
\begin{align}
E=\cfrac{1}{2}((t_1-a_{20})^2+(t_2-a_{21})), \\
\cfrac{\partial E}{\partial a_{20}}=(t_1-a_{20})=-0.37
\end{align}
$$
$$
\cfrac{\partial a_{20}}{\partial z_{20}}=a_{20}\times(1-a_{20})=0.25
$$
$$
\cfrac{\partial z_{20}}{\partial w_{10}^1}=a_{10}=0.54
$$
$$
\begin{align}
\cfrac{\partial E}{\partial w_{10}^1}=-0.37\times0.25\times0.54=-0.049, \\
w_{10}^{1+}=w_{10}^{1}-(\alpha\times\cfrac{\partial E}{\partial w_{10}^1})
\end{align}
$$

## Reference
- [Neural networks and deep learning](http://neuralnetworksanddeeplearning.com/chap2.html)
- [Backpropagation, 역전파 알아보기 | Evans Library](https://evan-moon.github.io/2018/07/19/deep-learning-backpropagation/)

