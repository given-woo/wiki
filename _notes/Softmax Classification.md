---
title: Softmax Classification
use_math: true
---

When we do a multi-class classification, rather than using many binary classification, it is more efficient to use matrix.

$$
\begin{align}
Z=
\begin{pmatrix}
w_{A1}&w_{A2}&w_{A3}\\
w_{B1}&w_{B2}&w_{B3}\\
w_{C1}&w_{C2}&w_{C3}\\
\end{pmatrix}
\cdot
\begin{pmatrix}
x_1\\
x_2\\
x_3
\end{pmatrix}
=
\begin{pmatrix}
w_{A1}x_1+w_{A2}x_2+w_{A3}x_3\\
w_{B1}x_1+w_{B2}x_2+w_{B3}x_3\\
w_{C1}x_1+w_{C2}x_2+w_{C3}x_3\\
\end{pmatrix} \\[10pt]
H(Z)=
\begin{pmatrix}
\overline{y_A}\\
\overline{y_B}\\
\overline{y_C}\\
\end{pmatrix} \\
\end{align}
$$

By using matrix, we can interpret the result of the sigmoid function as a key factor deciding whether the input is A/B/C or not. To make the value of $H(Z)$ into a range of 0 to 1 and classify the input, we use [[Softmax Function]]. In Softmax classification, we use [[Categorial Cross Entropy]] as a cost function.

## Source Code
```python

import os
import math
import tensorflow as tf
import numpy as np
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

# datasets
x_raw = [[1, 2, 1, 1],
         [2, 1, 3, 2],
         [3, 1, 3, 4],
         [4, 1, 5, 5],
         [1, 7, 5, 5],
         [1, 2, 5, 6],
         [1, 6, 6, 6],
         [1, 7, 7, 7]]
y_raw = [[0, 0, 1],
         [0, 0, 1],
         [0, 0, 1],
         [0, 1, 0],
         [0, 1, 0],
         [0, 1, 0],
         [1, 0, 0],
         [1, 0, 0]]

x_data = np.array(x_raw, dtype=np.float32)
y_data = np.array(y_raw, dtype=np.float32)

model = tf.keras.Sequential()

# 4 inputs, 3 outputs
model.add(tf.keras.layers.Dense(input_dim=4, units=3, activation='softmax'))

# initail lr : 0.2 / total epochs : 2000
cosine_decay = tf.keras.optimizers.schedules.CosineDecay(0.2, 2000, alpha=0.0)
sgd = tf.keras.optimizers.SGD(learning_rate=cosine_decay)
model.compile(loss='categorical_crossentropy', optimizer=sgd, metrics=['accuracy'])
model.summary()

history = model.fit(x_data, y_data, epochs=2000)

print('--------------')
a = model.predict(np.array([[1, 11, 7, 9]]))
print(a, tf.keras.backend.eval(tf.argmax(a, axis=1)))
```