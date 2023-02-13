---
title: Logistic Regression
use_math: true
---

$$
H(X)=\cfrac{1}{e^{-WX}}
$$

<img src="assets/Pasted image 20230213203331.png">
*Fig 1. Sample Hypothesis of a Logistic Regression*

We can use Logistic Regression to Classify between two objects. This is called "Binary Classification". 

If we apply [[MSE (Mean Squared Error)|MSE]] on Logistic Regression, It becomes a [[Convex Function|Non-Convex Function]]. So, We use [[Binary Cross Entropy]] to make it into a [[Convex Function]].

## Source Code
```python

import os
import math
import tensorflow as tf
import numpy as np
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

x_data = [[1, 2],
          [2, 3],
          [3, 1],
          [4, 3],
          [5, 3],
          [6, 2]]
y_data = [[0],
          [0],
          [0],
          [1],
          [1],
          [1]]

model = tf.keras.Sequential()
# use sigmoid as activation function
model.add(tf.keras.layers.Dense(units=1, input_dim=2, activation='sigmoid'))

# initial lr : 0.1 / total epoch : 5000
e = 5000
cos_decay = tf.keras.optimizers.schedules.CosineDecay(0.1, e, alpha=0.0)
sgd = tf.keras.optimizers.SGD(learning_rate=cos_decay)
model.compile(loss='binary_crossentropy', optimizer=sgd, metrics=['accuracy'])
model.summary()

history = model.fit(x_data, y_data, epochs=e)
print("Accuracy: ", history.history['accuracy'][-1])
```
