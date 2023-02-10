---
title: Deep Learning on XOR problem
---

# Deep Learning on XOR problem

Can solve [[XOR Problem]] by training Neural Network using [[Deep Learning]]

## Source Code

### a. Single Layer

```python
import tensorflow as tf
import numpy as np

x_data = np.array([[0, 0], [0, 1], [1, 0], [1, 1]], dtype=np.float32)
y_data = np.array([[0], [1], [1], [0]], dtype=np.float32)

model = tf.keras.Sequential()
model.add(tf.keras.layers.Dense(units=1, input_dim=2, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer=tf.optimizers.SGD(lr=0.01), metrics=['accuracy'])
model.summary()

history = model.fit(x_data, y_data, epochs=1000)

score = model.evaluate(x_data, y_data)
print('Accuracy: ', score[1])
```

>[!quote] Result
>Accuracy:  0.5

The Result shows that the XOR problem can't be solved with a single layer of perceptron.

### b. Neural Network

```python
import tensorflow as tf
import numpy as np

x_data = np.array([[0, 0], [0, 1], [1, 0], [1, 1]], dtype=np.float32)
y_data = np.array([[0], [1], [1], [0]], dtype=np.float32)

model = tf.keras.Sequential()
model.add(tf.keras.layers.Dense(units=2, input_dim=2))
model.add(tf.keras.layers.Activation('sigmoid'))
model.add(tf.keras.layers.Dense(units=1, input_dim=2))
model.add(tf.keras.layers.Activation('sigmoid'))
model.compile(loss='binary_crossentropy', optimizer=tf.optimizers.SGD(lr=0.1),  metrics=['accuracy'])
model.summary()

history = model.fit(x_data, y_data, epochs=10000)

score = model.evaluate(x_data, y_data)
print('Accuracy: ', score[1])
```

>[!quote] Result
>Accuracy: 1.0

### c. Deep & Wide Neural Network

```python
import tensorflow as tf
import numpy as np

x_data = np.array([[0, 0], [0, 1], [1, 0], [1, 1]], dtype=np.float32)
y_data = np.array([[0], [1], [1], [0]], dtype=np.float32)

model = tf.keras.Sequential()

# input layer
model.add(tf.keras.layers.Dense(units=10, input_dim=2, activation='sigmoid'))

# hidden layer
model.add(tf.keras.layers.Dense(units=10, activation='sigmoid'))
model.add(tf.keras.layers.Dense(units=10, activation='sigmoid'))
model.add(tf.keras.layers.Dense(units=10, activation='sigmoid'))

# output layer
model.add(tf.keras.layers.Dense(units=1, activation='sigmoid'))

# used Adam to avoid vanishing gradient
model.compile(loss='binary_crossentropy', optimizer=tf.optimizers.Adam(lr=0.1),  metrics=['accuracy'])
model.summary()

history = model.fit(x_data, y_data, epochs=5000)

predictions = model.predict(x_data)
print('Prediction: \n', predictions)

score = model.evaluate(x_data, y_data)
print('Accuracy: ', score[1])
```

>[!quote]
>Accuracy:  1.0

## Reference
- [lec9-2: 딥넷트웍 학습 시키기 (backpropagation) - YouTube](https://www.youtube.com/watch?v=573EZkzfnZ0&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm&index=27&ab_channel=SungKim)
