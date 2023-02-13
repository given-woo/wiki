---
title: Linear Regression
use_math: true
---

$$
\begin{align}
H(x)=Wx+b\\
H(X)=W\cdot X+b
\end{align}
$$
We will assume that there is a linear relationship between $x$ and $y$ column and try to choose hypothesis with the least cost. (In this case, we use [[MSE (Mean Squared Error)]] to calculate the cost)

Becuase Linear Regression's Weight-Cost graph is convex, we can use [[Gradient Descent Algorithm]] to optimize weights.


## Source Code
### a. Single Variable
```python

mport os
import numpy as np
import tensorflow as tf
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

# X and Y data
n = int(input('Number of Train Data Set : '))
x_input = []
y_input = []
for i in range(n):
    x_input.append(float(input('%d - x : ' % (i+1))))
    y_input.append(float(input('%d - y : ' % (i+1))))
e = int(input('Number of epochs : '))

# SGD : Stochastic Gradient Descent
cos_decay = tf.keras.optimizers.schedules.CosineDecay(0.01, e, alpha=0.0)
sgd = tf.keras.optimizers.SGD(learning_rate=cos_decay)

# Make Sequential Layer : multi-layered model of Keras
model = tf.keras.Sequential()

# Add Dense layer
# units : output shape, input_dim : input shape
model.add(tf.keras.layers.Dense(units=1, input_dim=1))

# Set Loss Function to mse
# use SGD as optimizer
# mse : mean_squared_error
model.compile(loss='mse', optimizer=sgd)

# Prints summary of the model to the terminal
model.summary()

# Execute Training
# epoch :One Epoch is when an ENTIRE dataset is passed forward and backward through the neural network only ONCE
# batch : Total number of training examples present in a single batch.
# iteration : The number of passes to complete one epoch.
model.fit(x_input, y_input, epochs=e)

print(model.predict(np.array([10, 20])))
```

### b. Multi-Variable
```python

import os
import math
import tensorflow as tf
import numpy as np
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

x_data = [[73., 80., 75.],
          [93., 88., 93.],
          [89., 91., 90.],
          [96., 98., 100.],
          [73., 66., 70.]]
y_data = [[152.],
          [185.],
          [180.],
          [196.],
          [142.]]

model = tf.keras.Sequential()

# input shape : [3] / output shape : [1]
model.add(tf.keras.layers.Dense(units=1, input_dim=3))
model.add(tf.keras.layers.Activation('linear'))
# model.add(tf.keras.Activation('relu'))

# set cosine decay
# initial lr : 2e-5=0.00002 / total epoch : 5000
e = 5000
cos_decay = tf.keras.optimizers.schedules.CosineDecay(2e-5, e, alpha=0.0)
sgd = tf.keras.optimizers.SGD(learning_rate=cos_decay)

model.compile(loss='mse', optimizer=sgd)
model.summary()
model.fit(x_data, y_data, epochs=e)

y_predict = model.predict(np.array(x_data))
print(y_predict)
```