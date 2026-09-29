---
title: Perceptron
type: concept
tags: [ml, neural-networks]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Perceptron (Rosenblatt, 1958)

**Intuition.** A computational model of a biological neuron: weighted inputs are summed and thresholded to produce a class.

**From the slides (slide 8).** A neural network is "a distributed parallel processor made up of simple processing units that can store knowledge based on experience". It acquires knowledge from the environment through learning; synaptic weights store the knowledge.

## Definition (AIMA §19.6.4, p. 700–702; §22 notes p. 836)
h_w(x) = 1 if w·x ≥ 0 else 0 (bias as x₀ = 1). **Perceptron learning rule:** wᵢ ← wᵢ + α (y − h_w(x)) xᵢ (no change if correct; add x if it should have fired; subtract if it fired wrongly). It converges to a perfect separator **iff** the data are linearly separable; on noisy data it needs a decaying α(t) = O(1/t). Full treatment, an AND worked example and logistic regression: [[linear-classifiers]].

**History (AIMA p. 836):** popularised by Frank Rosenblatt (1957; NYT hype after the July 1958 demo); convergence theorem 1960; Minsky & Papert, *Perceptrons* (1969) stressed that single-layer perceptrons represent only linearly separable concepts and that no learning algorithm for multilayer nets existed; Rosenblatt himself had acknowledged this (1962). This matches the slide's date of 1958 (slide 8).

## Pros / cons
+ Simple, online learning. − Only linear decision boundaries; cannot solve XOR alone → motivates multi-layer nets and [[backpropagation]].

## Related
[[linear-classifiers]], [[neural-networks-basics]], [[aima-ch19-learning-from-examples]], [[aima-ch22-deep-learning]], [[support-vector-machine]] (also a linear classifier, maximizes margin), [[deep-learning]], [[gradient-descent]], [[history-of-ai]]. Syllabus topic 10 covers perceptron ([[slides-00-course-intro]]).

## Exam angles
- Why XOR fails for a single perceptron.
- Role of weights as stored knowledge.
