---
title: Linear Classifiers (Threshold, Perceptron Rule, Logistic Regression)
type: concept
tags: [machine-learning, classification, linear-models]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Linear Classifiers

**Intuition.** Draw a line/plane that separates two classes: classify by which side a point lies on (AIMA §19.6, p. 694–704).

## Linear regression first (p. 694–697)
h_w(x) = w₁x + w₀; L2 loss Σ(y − h_w(x))². Closed form: w₁ = [NΣxy − ΣxΣy]/[NΣx² − (Σx)²], w₀ = (Σy − w₁Σx)/N. The loss is **convex** (no local minima). Or use [[gradient-descent]]: wᵢ ← wᵢ − α ∂Loss/∂wᵢ (α = learning rate); for one example wᵢ ← wᵢ + α(y − h_w(x))xᵢ.

## Hard-threshold classifier (p. 700–702)
h_w(x) = 1 if w·x ≥ 0 else 0 (with x₀ = 1 as bias input). The **decision boundary** w·x = 0 is a **linear separator**; data that admit one are **linearly separable**. The gradient is zero almost everywhere so gradient descent fails; use the **perceptron learning rule**
  wᵢ ← wᵢ + α (y − h_w(x)) xᵢ.
- Correct → no change; y=1,h=0 → add x; y=0,h=1 → subtract x.
- Converges to a perfect separator **iff** data are linearly separable (book run: 657 steps for 63 examples). On noisy non-separable data it doesn't settle unless α decays like O(1/t) (e.g. 1000/(1000+t)); minimum-error separator is NP-hard.

## Worked example: learn AND (own; verified by code)
Inputs (1,x₁,x₂), α = 1, w = (0,0,0), cycle in order (0,0),(0,1),(1,0),(1,1):
epoch 1 → w = (0,1,1) after 2 updates; epoch 2 → (−1,2,1); epoch 3 → (−2,2,1); epoch 4 → (−2,2,2); epoch 5 → (−3,2,1); epoch 6 no errors. Result: −3 + 2x₁ + x₂ ≥ 0 ⇔ AND. The same procedure never converges for XOR (not linearly separable).

## Logistic regression (p. 702–704)
Soften the threshold: h_w(x) = Logistic(w·x) = 1/(1+e^(−w·x)) ∈ (0,1), interpreted as P(class 1); g′ = g(1−g).
Update (L2 loss): wᵢ ← wᵢ + α (y − h_w)·h_w(1 − h_w)·xᵢ. Converges predictably even for noisy/non-separable data; widely used (medicine, credit scoring…).

## Pros / cons
+ Simple, fast, interpretable, convex (regression). − Only linear boundaries; hard threshold gives overconfident 0/1 and unstable learning. Fixes: [[support-vector-machine]] (max margin + kernels), [[neural-networks-basics]] (stack nonlinear units).

## Related
[[perceptron]], [[supervised-learning]], [[overfitting-and-generalization]], [[backpropagation]], [[aima-ch19-learning-from-examples]]

## Exam angles
- Run the perceptron rule on a tiny dataset by hand.
- Why can't a single perceptron learn XOR? (not linearly separable)
- Perceptron vs logistic regression: hard vs soft threshold, differentiability.
