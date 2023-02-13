---
title: Gradient Descent Algorithm
use_math: true
---

A method or algorithm to optimize neural networks in [[Machine Learning]].

<img src="assets/iRg3svSg.gif">
*Fig 1. Visualization of Gradient Descent Algorithm*

## Algorithm
Start with a random or static initial guess and keep changing W and b to reduce $cost(W, b)$

## Formal Definition
$$
W:=W-\alpha\cfrac{\partial}{\partial W}\sum_{i=1}^m(H(x_i)-y_i)^2
$$

If $W$ is having a positive effect on Cost, decrease it a little. And if $W$ is having a negative effect on Cost, increase it a little. We can get the effects using [[Back Propagation]].

## Source Code
Implantation of Gradient Descent on [[Linear Regression]]
```python
import os
import tensorflow as tf
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

# X and Y data
n = int(input('Number of Train Data Set : '))
X = []
Y = []
for i in range(n):
    X.append(float(input('%d - x : ' % (i+1))))
    Y.append(float(input('%d - y : ' % (i+1))))
e = int(input('Number of epochs : '))

# Random weight
W = tf.Variable(tf.random.normal([1]), dtype=tf.float32)

# Hypothesis for linear model X*W
hypothesis = X * W

# Cost function
cost = tf.reduce_mean(tf.square(hypothesis - Y))

# Minimizing Cost : Gradient Descent Algorithm
learning_rate = 0.01
for i in range(e):
    W = W - learning_rate*tf.reduce_mean((W*X-Y)*X)
    hypothesis = X * W
    cost = tf.reduce_mean(tf.square(hypothesis - Y))
    tf.print("cost", i, ":", cost)

tf.print(100*W)
```