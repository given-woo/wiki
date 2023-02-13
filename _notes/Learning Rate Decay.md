---
title: Learning Rate Decay
---

Starting from a high [[Learning Rate]] and gradually decreasing it. This results in faster speed and better accuracy.

## Linear Decay
<img src="assets/Pasted image 20230213224442.png">
*Fig 1. Linear Learning Rate Decay*

## Cosine Decay
<img src="assets/Pasted image 20230213224508.png">
*Fig 2. Cosine Learning Rate Decay*

## Source Code
### a. Cosine Decay
```python

import os
import math
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

# Minimizing Cost : Gradient Descent Algorithm + Cosine Decay
for i in range(e):
    learning_rate=0.01*(1+math.cos(i*math.pi/e))/2
    W = W - learning_rate*tf.reduce_mean((W*X-Y)*X)
    hypothesis = X * W
    cost = tf.reduce_mean(tf.square(hypothesis - Y))
    tf.print("cost", i+1, ":", cost)

tf.print("H(100) =", float(100*W))
```
