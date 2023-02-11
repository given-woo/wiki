---
title: XOR Problem
---

# XOR Problem

The famous pioneers in AI Marvin Minsky and Seymour Papert claimed in their book [Perceptrons](https://mitpress.mit.edu/9780262630221/perceptrons/), that the simple XOR cannot be resolved by two-layer of feedforward neural networks, which "drove reasearch away from neural networks and contributed to the so-called AI winter".

## The XOR Problem
XOR is a classification problem and one for which the expected outputs are known in advance. It is therefore appropriate to use a supervised learning approach.

With a Single Perceptron, We can only classify with a single line.

| Input 1 | Input 2 | output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 1      |
| 1       | 1       | 0      |
| 1       | 0       | 1       |

*Fig 1. Input and Output of XOR*

<img src="assets/Pasted image 20230208140659.png">
*Fig 2. Classification with a Single Perceptron*

As the picture above, AND and OR operation can be classified with a single line, but XOR can't be classified. This was mathematically proved by Marvin Minsky and Seymor Paper.

## How to Solve it
You can use multi-layered perceptrons to solved this problem. You can [[Deep Learning on XOR problem|train it]] with [[Deep Learning]].

## Reference
- [Solving XOR Problem with MLP](https://ynebula.tistory.com/22)
- [Demystifying the XOR problem - DEV Community 👩‍💻👨‍💻](https://dev.to/jbahire/demystifying-the-xor-problem-1blk)

