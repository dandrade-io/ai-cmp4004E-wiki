---
title: Backpropagation
type: concept
tags: [ml, neural-networks]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Backpropagation

**Intuition.** Efficiently compute how much each weight contributes to the error so every weight can be nudged downhill.

**Slides (slide 11).** The algorithm computes the gradient of the loss with respect to the weights of each neuron. It made it possible to train several neurons connected in series; nonlinearity let networks solve XOR. Slide date: 1975.

> ⚠️ Contradiction (resolved by AIMA, p. 837): the slide dates backprop to 1975, but AIMA says it was discovered independently several times (Kelley 1960, Bryson 1962, Dreyfus 1962, Bryson & Ho 1969, **Werbos 1974**, Parker 1985) and became widely known through **Rumelhart, Hinton & Williams (1986, *Nature*)**. So 1975 is close to Werbos's application to neural nets but not the popularising date; the standard date to remember is **1986**.

## How it works (AIMA §22.1.2, p. 805–807)
Network: 2 inputs x₁,x₂ → hidden units 3,4 → output 5, squared loss (y−ŷ)².
1. Forward pass: in_j = Σ w_ij a_i, a_j = g_j(in_j); ŷ = a₅.
2. Output weight: ∂Loss/∂w₃,₅ = −2(y−ŷ) g′₅(in₅) a₃.
3. Hidden weight (extra chain-rule step): ∂Loss/∂w₁,₃ = −2(y−ŷ) g′₅(in₅) w₃,₅ g′₃(in₃) x₁.
4. Define the "perceived error" Δ₅ = 2(ŷ−y)g′₅(in₅) and Δ₃ = Δ₅ w₃,₅ g′₃(in₃): the gradient is Δ·(input activation) and Δ is **passed back** through the network – hence *back*-propagation.
5. Update with [[gradient-descent]]: w ← w − α ∂Loss/∂w.
General statement: backprop is **reverse-mode automatic differentiation** on a computation graph; deep-learning frameworks do it for you (end-to-end learning).

**Vanishing gradient:** the factors g′(in) are ≥ 0 but can be ≈ 0 (sigmoid/tanh saturation) or exactly 0 (ReLU dead region); in deep nets the error signal can fade. Fix: ReLU, residual networks (p. 807).

## Pros / cons
+ Scales to deep networks. − Vanishing/exploding gradients; local minima ([[optimization-landscape]]).

## Related
[[perceptron]], [[neural-networks-basics]], [[deep-learning]], [[history-of-ai]], [[aima-ch22-deep-learning]]

## Exam angles
- What is being differentiated and why the chain rule is needed.
- Why single-layer perceptrons cannot solve XOR but multi-layer nets trained with backprop can.
