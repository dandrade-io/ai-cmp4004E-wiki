---
title: Overfitting, Generalization and Model Selection
type: concept
tags: [machine-learning, generalization, evaluation]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Overfitting, Generalization and Model Selection

**Intuition.** A model that memorises noise looks perfect on training data and fails on new data. AIMA Fig. 19.1: a degree-12 polynomial fits 13 points exactly (consistent) yet is a poor guess: high variance (p. 672).

## Data splits (§19.4.1, p. 683–685)
- Assume examples are **i.i.d.** (stationarity).
- **Training set** fits models; **validation (dev) set** picks hyperparameters/model; **test set** gives the final unbiased estimate and must stay locked away (else the *researcher* leaks it).
- **k-fold cross-validation:** split into k parts, k rounds using 1/k as validation, average the score (k = 5 or 10; k = n is LOOCV). Still keep a separate test set.
- **Model selection** = choose the hypothesis space/hyperparameter (e.g. tree size, polynomial degree); **optimization/training** = best hypothesis in that space.
- Validation-error curve is often **U-shaped**: training error keeps dropping, validation error bottoms out at the best complexity (decision tree: size 7 in Fig 19.9a). Modern deep nets, kernel machines and boosted ensembles can keep improving with capacity (Fig 19.9b).

## Loss and regularization (p. 687–689)
- Loss: L1, L2, 0/1; empirical loss estimates generalization loss.
- **Regularization:** minimise Cost(h) = EmpLoss(h) + λ·Complexity(h) (e.g. sum of squared coefficients). Also feature selection, MDL.
- Why ĥ ≠ f: unrealizability, variance, noise, computational limits.
- **Hyperparameter tuning:** hand-tuning, grid search, random search, Bayesian optimization, population-based training (genetic-algorithm flavoured; cf. [[genetic-algorithms]]).

## Worked example (own)
Fit 13 noisy points with polynomials of degree 1, 3, 12: training error 20 → 4 → 0 (%), validation error 22 → 6 → 45. Choose degree 3 (bottom of the U). Degree 12 *interpolates* and overfits; degree 1 underfits (illustrative numbers).

## Related
[[supervised-learning]], [[linear-classifiers]], [[support-vector-machine]] (max margin resists overfitting), [[deep-learning]] (dropout, weight decay, ch. 22.5), [[aima-ch19-learning-from-examples]], [[exploration-vs-exploitation]] (Bayesian optimization tradeoff)

## Exam angles
- Diagnose under/overfitting from training vs validation error.
- Why three splits rather than two? Why cross-validation?
- Name three ways to fight overfitting (more data, simpler model/regularization, early stopping/dropout).
