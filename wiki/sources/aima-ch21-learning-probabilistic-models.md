---
title: "AIMA Ch. 21 – Learning Probabilistic Models (naive Bayes and ML estimation)"
type: source
tags: [source, book, probability, learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 21: Learning Probabilistic Models

> ⚠️ Chapter numbering: in this edition **Ch. 21 is "Learning Probabilistic Models"** and **Deep Learning is Ch. 22** ([[aima-ch22-deep-learning]]). Only §21.2 was read (book p. 775–780).

## What was read
- **§21.2.1 Maximum-likelihood learning (discrete):** for a bag of c cherry / ℓ lime candies, L = c log θ + ℓ log(1−θ) ⇒ θ = c/(c+ℓ) – the observed frequency. Recipe: write likelihood → log → differentiate → set to 0. With complete data, a Bayes net's parameter learning **decomposes** into independent problems; CPT entries = observed conditional frequencies. Zero counts are a problem → initialise counts to 1.
- **§21.2.2 Naive Bayes learning:** 2n+1 parameters for n Boolean attributes; no search; robust to noise/missing data; drawback: overconfident. Covered in [[naive-bayes]].
- **§21.2.3 Generative vs discriminative models:** generative models model P(inputs|class) and can sample (naive Bayes); discriminative model P(class|inputs) directly (only the start of this discussion read).

## Not read
§21.1 statistical learning (Bayesian vs MAP vs ML), §21.2.4+ structure learning, density estimation, §21.3 EM algorithm.

## Related
[[probability-basics]], [[bayesian-networks]], [[supervised-learning]], [[aima-ch12-quantifying-uncertainty]]
