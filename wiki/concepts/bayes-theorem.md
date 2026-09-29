---
title: Bayes' Theorem (Bayes' Rule)
type: concept
tags: [probability, inference, bayes]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Bayes' Theorem

**Intuition.** Turn a causal-direction fact ("disease → symptom") into a diagnostic-direction answer ("symptom → disease"). Syllabus topic 7 ([[slides-00-course-intro]]).

## Formula (AIMA §12.5, p. 417–419)
P(b|a) = P(a|b) P(b) / P(a)
With normalization: **P**(Y|X) = α **P**(X|Y) **P**(Y), where α = 1/P(X).
With background evidence e: P(Y|X,e) = P(X|Y,e)P(Y|e)/P(X|e).
Derivation: equate the two forms of the product rule, P(a∧b) = P(a|b)P(b) = P(b|a)P(a).

Vocabulary: **prior** P(cause), **likelihood** P(effect|cause), **evidence** P(effect), **posterior** P(cause|effect).

## Worked example (AIMA, p. 418)
P(s|m) = 0.7, P(m) = 1/50000, P(s) = 0.01 ⇒ P(m|s) = 0.7 × (1/50000)/0.01 = **0.0014**. A strongly indicative symptom still gives a small posterior because the prior is tiny.

## Extra example (own, standard base-rate problem)
Disease prevalence 1 %, test sensitivity 90 %, false-positive rate 5 %.
P(D|+) = 0.9·0.01 / (0.9·0.01 + 0.05·0.99) = 0.009 / 0.0585 ≈ **0.154**. Most positives are false positives.

## Why use it (p. 419)
- Causal knowledge P(effect|cause) is more **robust** than diagnostic P(cause|effect): if an epidemic raises P(m), the diagnostic number becomes wrong but P(s|m) stays valid.
- Normalised form avoids estimating P(evidence): needs P(s|¬m) instead.
- Multiple evidence: needs [[conditional-independence]] (otherwise O(2ⁿ) conditionals); leads to [[naive-bayes]].

## Pitfalls
- Confusing P(a|b) with P(b|a) (prosecutor's fallacy).
- Ignoring the base rate P(b).

## Related
[[probability-basics]], [[naive-bayes]], [[bayesian-networks]], [[hidden-markov-models]] (filtering is Bayes' rule applied repeatedly), [[judea-pearl]], [[aima-ch12-quantifying-uncertainty]]

## Exam angles
- Compute a posterior from prior, likelihood and false-positive rate; do the normalisation version when P(evidence) is not given.
- Explain in words why a 99 %-accurate test can still yield a low posterior.
