---
title: Support Vector Machine
type: concept
tags: [ml, classification]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Support Vector Machine (SVM)

**Slides (slide 12, 1995).** Vladimir Vapnik and colleagues at AT&T Bell Labs proposed a linear classification algorithm, similar to the [[perceptron]], that tries to **maximize the margin** between two subspaces. (The slide shows the objective as an image; not extractable.)

## What AIMA says (§19.7.5–19.7.6, p. 710–714)
SVM (popular "off-the-shelf" in the early 2000s; now overtaken by deep nets and random forests) has three attractive properties:
1. **Maximum-margin separator** – the boundary farthest from the nearest examples (margin = twice that distance), motivated by minimising *generalization* loss rather than training loss; logistic regression's line depends on all points, SVM's on a few.
2. **Kernel trick** – embed data in a higher-dimensional space where it becomes linearly separable.
3. **Nonparametric but compact** – the separator is defined by the **support vectors** only (points closest to it, usually few).

Convention: labels ±1, separator {x : w·x + b = 0}. Dual form: maximise Σⱼαⱼ − ½Σⱼₖ αⱼαₖ yⱼyₖ (xⱼ·xₖ) subject to αⱼ ≥ 0, Σαⱼyⱼ = 0 (quadratic programming, convex → single global optimum). Classifier h(x) = sign(Σⱼ αⱼ yⱼ (x·xⱼ) − b); αⱼ ≠ 0 only for support vectors. Data enter only via **dot products**.

**Kernel trick worked example (p. 713):** map (x₁,x₂) ↦ F(x) = (x₁², x₂², √2·x₁x₂). A circle x₁²+x₂² ≤ 1 becomes a plane in 3-D. And F(x)·F(z) = (x·z)², so K(x,z) = (x·z)² can be computed without computing F. Check: x=(1,2), z=(3,1): 25 both ways. Other kernels: polynomial (1+x·z)^d, Gaussian exp(−γ‖x−z‖²) (Mercer's theorem: any positive-definite kernel corresponds to a feature space).
**Soft margin:** allow misclassified points with a penalty proportional to their distance → handles noisy data.

History (p. 736): kernel trick Aizerman et al. 1964; SVM theory Boser, Guyon, Vapnik 1992; soft margin Cortes & Vapnik 1995 (matches slide's 1995).

## Pros / cons
+ Strong generalization, convex optimization. − Scales poorly to huge datasets; kernel choice matters.

## Related
[[perceptron]], [[linear-classifiers]], [[overfitting-and-generalization]], [[deep-learning]], [[history-of-ai]], [[aima-ch19-learning-from-examples]]

## Exam angles
- Difference from perceptron: any separating line vs. the maximum-margin line.
- What are support vectors?
