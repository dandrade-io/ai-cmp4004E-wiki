---
title: "AIMA Ch. 19 – Learning from Examples"
type: source
tags: [source, book, machine-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 19: Learning from Examples

Book pages 669–~740. See [[russell-norvig]].

## Section map
| § | Title | Book p. | Wiki page |
|---|---|---|---|
| 19.1 | Forms of learning | 669 | [[supervised-learning]] |
| 19.2 | Supervised learning; bias/variance | 671 | [[supervised-learning]] |
| 19.3 | Decision trees | 675 | headings only |
| 19.4 | Model selection, loss, regularization, hyperparameters | 683 | [[overfitting-and-generalization]] |
| 19.5 | Theory of learning (PAC) | 690 | headings only |
| 19.6 | Linear regression and classification (GD, perceptron rule, logistic) | 694 | [[linear-classifiers]], [[gradient-descent]] |
| 19.7 | Nonparametric models: kNN, k-d trees, LSH, **SVM**, kernel trick | 704 | [[support-vector-machine]] |
| 19.8 | Ensemble learning (bagging, random forests, stacking, boosting) | 714 | headings only |
| 19.9 | Developing ML systems | 722 | headings only |

## Highlights
- Three splits (train/validation/test), k-fold CV; U-shaped validation curve.
- L2 regression closed form and gradient-descent view; convex loss.
- Perceptron rule converges iff linearly separable; logistic regression is smoother.
- SVM: maximum-margin separator, dual form, support vectors, kernels K(x,z) = (x·z)² etc.
- Ensembles: five independent 75 %-accurate classifiers vote to 89 % (assuming independence, p. 715).
- History notes: SVM soft margin (Cortes & Vapnik 1995), kernel trick (Aizerman 1964), Boser et al. 1992.

## Link to slides
Slide 01 items on the perceptron and SVM ([[slides-01-introduction-to-ai]], [[perceptron]], [[support-vector-machine]]); syllabus topic 10.
