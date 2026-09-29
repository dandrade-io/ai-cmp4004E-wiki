---
title: Bayes, Bayesian Network, Markov/HMM and Linear-Classifier Worked Examples
type: analysis
tags: [exam-prep, probability, hmm, machine-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Worked Examples (Exam-Style Practice)

Numbers marked (AIMA) come from the book; others are my own and were checked with a short Python script. Try each before reading the solution.

## 1. Full joint table (AIMA Fig. 12.3)
| | toothache, catch | toothache, ¬catch | ¬toothache, catch | ¬toothache, ¬catch |
|---|---|---|---|---|
| cavity | 0.108 | 0.012 | 0.072 | 0.008 |
| ¬cavity | 0.016 | 0.064 | 0.144 | 0.576 |

a) P(cavity ∨ toothache)? b) P(cavity | toothache)? c) P(cavity | toothache ∧ catch)?
**Solution.** a) 0.108+0.012+0.072+0.008+0.016+0.064 = **0.28**. b) 0.12/0.20 = **0.6**. c) α⟨0.108, 0.016⟩ → 0.108/0.124 ≈ **0.871**.
See [[probability-basics]].

## 2. Bayes' rule with a false-positive rate
Prevalence 1 %, sensitivity 90 %, false-positive 5 %. P(disease | positive)?
**Solution.** 0.009 / (0.009 + 0.0495) = **0.154**. [[bayes-theorem]]

## 3. Naive Bayes (two words)
P(spam)=0.4; P(w₁|spam)=0.6, P(w₁|ham)=0.1; P(w₂|spam)=0.5, P(w₂|ham)=0.2. Classify a message containing both.
**Solution.** spam ∝ 0.4·0.6·0.5 = 0.12; ham ∝ 0.6·0.1·0.2 = 0.012 → P(spam) = 0.12/0.132 = **0.909**. [[naive-bayes]]

## 4. Bayesian network parameter counting and a joint entry (AIMA Fig. 13.2)
a) Parameters for the burglary net vs the full joint over 5 Boolean variables? b) P(j, m, a, ¬b, ¬e)?
**Solution.** a) B:1, E:1, A:4, J:2, M:2 = **10** vs 2⁵−1 = **31**. b) 0.90·0.70·0.001·0.999·0.998 = **0.000628**. c) Enumeration gives P(B | j,m) = ⟨0.284, 0.716⟩. [[bayesian-networks]]

## 5. HMM filtering (umbrella world)
Transition: stay 0.7, switch 0.3. Sensor: P(u|rain)=0.9, P(u|¬rain)=0.2. Prior ⟨0.5,0.5⟩. Observations: umbrella, umbrella, no umbrella. Filter P(Rain₃ | u₁,u₂,¬u₃).
**Solution.**
- t=1: predict ⟨0.5,0.5⟩ → ⟨0.45, 0.10⟩ → **⟨0.818, 0.182⟩**
- t=2: predict ⟨0.627, 0.373⟩ → ⟨0.565, 0.075⟩ → **⟨0.883, 0.117⟩**
- t=3: predict ⟨0.653, 0.347⟩; ¬u likelihoods 0.1 / 0.8 → ⟨0.0653, 0.2773⟩ → **⟨0.191, 0.809⟩**. [[hidden-markov-models]]

## 6. Smoothing
Smoothed P(R₁ | u₁,u₂)?
**Solution.** backward message b₂:₂ = ⟨0.9·0.7+0.2·0.3, 0.9·0.3+0.2·0.7⟩ = ⟨0.69, 0.41⟩; α⟨0.818·0.69, 0.182·0.41⟩ = **⟨0.883, 0.117⟩** (higher than filtered 0.818).

## 7. Viterbi (two steps)
Same model, u₁=u₂=true, prior ⟨0.5,0.5⟩. Most likely (R₁,R₂)?
**Solution.** m₁ = ⟨0.9·max(0.7·0.5, 0.3·0.5), 0.2·max(0.3·0.5, 0.7·0.5)⟩ = ⟨0.315, 0.070⟩. m₂(rain) = 0.9·max(0.7·0.315, 0.3·0.07) = 0.19845; m₂(¬rain) = 0.2·max(0.3·0.315, 0.7·0.07) = 0.0189. Best: **rain, rain** (back-pointers both to rain). For the 5-day sequence [T,T,F,T,T] the answer is rain, rain, ¬rain, rain, rain (AIMA Fig. 14.5).

## 8. Prediction and stationary distribution
Given P(R₁)=⟨0.8,0.2⟩ and no more evidence, what happens to P(rain)?
**Solution.** 0.62 → 0.548 → 0.5192 → … → 0.5 (error shrinks by 0.4 each step). [[markov-models]]

## 9. Perceptron rule
Learn AND with inputs (1,x₁,x₂), α=1, w₀ = (0,0,0). **Solution.** Converges after 5 epochs with updates to w = (−3, 2, 1). XOR never converges (not linearly separable). [[linear-classifiers]]

## 10. Kernel identity
With F(x) = (x₁², x₂², √2 x₁x₂), show F(x)·F(z) = (x·z)². **Solution.** x₁²z₁² + x₂²z₂² + 2x₁x₂z₁z₂ = (x₁z₁ + x₂z₂)². For x=(1,2), z=(3,1): both sides = 25. [[support-vector-machine]]

## Related
[[aima-ch12-quantifying-uncertainty]], [[aima-ch13-probabilistic-reasoning]], [[aima-ch14-reasoning-over-time]], [[aima-ch19-learning-from-examples]]
