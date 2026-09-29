---
title: "AIMA Ch. 14 – Probabilistic Reasoning over Time"
type: source
tags: [source, book, markov, hmm]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 14: Probabilistic Reasoning over Time

Book pages ~478–~520. See [[russell-norvig]].

## Section map
| § | Title | Book p. | Wiki page |
|---|---|---|---|
| 14.1 | Time and uncertainty: states/observations, transition & sensor models, Markov assumptions | 479 | [[markov-models]] |
| 14.2 | Inference: filtering, prediction, smoothing (forward–backward), most likely sequence (Viterbi) | 483 | [[hidden-markov-models]] |
| 14.3 | Hidden Markov models: matrix algorithms, fixed-lag smoothing, localization example | 491 | [[hidden-markov-models]] |
| 14.4 | Kalman filters (Gaussian, continuous) | 497 | headings only |
| 14.5 | Dynamic Bayesian networks | 503 | headings only |

## Key results
- Filtering recursion: **P**(Xₜ₊₁|e₁:ₜ₊₁) = α **P**(eₜ₊₁|Xₜ₊₁) Σ **P**(Xₜ₊₁|xₜ) **P**(xₜ|e₁:ₜ).
- Umbrella world numbers: ⟨0.818,0.182⟩ → ⟨0.883,0.117⟩; prediction converges to stationary ⟨0.5,0.5⟩.
- Smoothing via f×b; whole-sequence smoothing O(t) by forward–backward.
- Viterbi = filtering with max; O(t) time and space; watch underflow.
- HMM matrix form: f = α O Tᵀ f; cost O(S²t).

## Link to slides
Course syllabus item 8, "Temporal reasoning and dynamic models: Markov" ([[slides-00-course-intro]]). No slides yet in `raw/`.

## Worked examples derived
See [[bayes-and-markov-worked-examples]].
