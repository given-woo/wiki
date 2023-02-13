---
title: Perceptron
use_math: true
---

## How Neurons transfer Information
<img src="assets/Pasted image 20230213120456.png">
*Fig 1. Structure of a single Neuron*

Information from dentrites is stored in cell nucleous, and it is only activated when the signal reaches a certain point. When Activated, the signal goes through Axon and Axon terminal and trigals other neurons.

Some dendrite links can be strong and others can be weak. And when and how the cell nucleous activates the neurons can differ.

## Perceptron

<img src="assets/Pasted image 20230213155608.png">
*Fig 2. A single Perceptron*

Like neurons, perceptrons get many $x$ datas and multiply weight($w$) to them. Weights($w$) acts like the strongness of links on neurons. Also, the bias($b$) plays a key role on the performance of the perceptron.

Perceptron's output($\sum_{i}^{n}{(x_i\times w_i+b)}$) is put into a [[Activation Function]], which decides whether the perceptron is activated.

Multi-Layer of perceptrons can process complex calculations.