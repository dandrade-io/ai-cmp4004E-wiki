---
title: Neural Networks Basics (Feedforward Networks)
type: concept
tags: [machine-learning, neural-networks, deep-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Neural Networks Basics

**Intuition.** Chain many simple *units* (weighted sum + nonlinearity) into layers so that inputs interact along long computation paths; train all weights by gradient descent (AIMA ch. 22, p. 801–807).

## Units and networks (§22.1, p. 802–805)
- **Feedforward** network = DAG from inputs to outputs (recurrent networks feed outputs back → memory).
- Unit j: a_j = g_j(Σᵢ wᵢ,ⱼ aᵢ) = g_j(w·x), with a fixed +1 bias input.
- **Activation functions:** sigmoid σ(x)=1/(1+e⁻ˣ); **ReLU** max(0,x); softplus log(1+eˣ); tanh (= 2σ(2x)−1). Nonlinearity is essential: composing linear units is still linear.
- **Universal approximation theorem:** two layers (one nonlinear hidden, one linear output) can approximate any continuous function arbitrarily well, though possibly exponentially large.
- Whole network: h_w(x) = g⁽²⁾(W⁽²⁾ g⁽¹⁾(W⁽¹⁾x)); best viewed as a **computation graph**; fully connected = each node connects to the whole next layer.
- Example (Fig 22.3): 2 inputs, 2 hidden units, 1 output: ŷ = g₅(w₀,₅ + w₃,₅ g₃(…) + w₄,₅ g₄(…)).

## Input/output encoding (p. 807–808)
Boolean → 0/1; numeric scaled; categorical → **one-hot**; images need structure-aware layers (convolution).

## Learning (§22.1.2, p. 805–807)
Loss (e.g. L2) gradient via the chain rule, see [[backpropagation]]. Vanishing gradients with sigmoid/tanh in deep nets; ReLU and residual connections help. Training: SGD on mini-batches.

## Beyond the basics (skimmed)
Convolutional nets (vision), residual nets, RNN/LSTM (sequences), dropout, weight decay, batch norm, transfer learning, applications (§22.3–22.8).

## Related
[[perceptron]] (single unit, hard threshold), [[linear-classifiers]], [[deep-learning]], [[gradient-descent]], [[overfitting-and-generalization]], [[aima-ch22-deep-learning]]

## Exam angles
- Compute a forward pass for a tiny network.
- Why a nonlinear activation? What does depth buy over a single layer?
- List common activations and one drawback of sigmoid.
