---
title: "AIMA Ch. 22 – Deep Learning"
type: source
tags: [source, book, deep-learning, neural-networks]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 22: Deep Learning

Book pages 801–~840. (The assignment brief called this "Ch. 21"; in this edition it is Ch. 22 – see [[aima-ch21-learning-probabilistic-models]].) See [[russell-norvig]].

## Section map
| § | Title | Book p. | Wiki page |
|---|---|---|---|
| 22.1 | Simple feedforward networks; units; activation functions; gradients and back-propagation | 802 | [[neural-networks-basics]], [[backpropagation]] |
| 22.2 | Computation graphs: input encoding, output layers/losses, hidden layers | 807 | [[neural-networks-basics]] |
| 22.3 | Convolutional networks, pooling, residual networks | 811 | headings only |
| 22.4 | Learning algorithms: gradients in computation graphs, batch norm | 816 | headings only |
| 22.5 | Generalization: architecture choice, weight decay, dropout | 819 | [[overfitting-and-generalization]] (brief) |
| 22.6 | Recurrent networks, LSTM | 823 | headings only |
| 22.7 | Unsupervised and transfer learning | 826 | headings only |
| 22.8 | Applications: vision, NLP, reinforcement learning | 833 | headings only |
| Notes | Bibliographical and historical notes | 836 | [[deep-learning]], [[backpropagation]], [[perceptron]] |

## Key points
- Deep = many layers = long computation paths so all inputs interact (Fig 22.1).
- Unit: a = g(Σ w a); activations sigmoid/ReLU/softplus/tanh; universal approximation with 2 layers.
- Gradient for output weight w₃,₅: −2(y−ŷ) g′₅(in₅) a₃; hidden weight w₁,₃: −2(y−ŷ) g′₅(in₅) w₃,₅ g′₃(in₃) x₁. Δ-terms propagate backwards = **back-propagation**; general form = reverse-mode automatic differentiation.
- Vanishing gradient when g′ ≈ 0; ReLU and residual nets mitigate.
- **History (p. 836–837):** McCulloch–Pitts 1943; Minsky's hardware net 1951; Rosenblatt perceptron 1957/58 (NYT hype), convergence theorem 1960; Minsky & Papert *Perceptrons* 1969; backprop discovered repeatedly (Kelley 1960, Bryson 1962, Bryson & Ho 1969, Werbos 1974, Parker 1985) and popularised by **Rumelhart, Hinton & Williams 1986**; deep-model revival with Hinton et al. 2006; **AlexNet won ImageNet 2012** (15.3 % top-5 error vs >25 % for runner-up, p. 837/§22.8.1); ReLU, residual nets, SGD mini-batches, GPUs and big data as enablers.

## Errata resolved
Slide 01 dates backprop to 1975 and "deep learning" to 1986/2000 – see [[backpropagation]] and [[deep-learning]].
