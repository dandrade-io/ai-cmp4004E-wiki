---
title: Naive Bayes
type: concept
tags: [probability, classification, machine-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Naive Bayes

**Intuition.** One hidden *cause/class* produces many *effects/features*; assume the features are independent **given the class**. Then evidence combines by simple multiplication. Syllabus topic 7 ([[slides-00-course-intro]]).

## Model (AIMA §12.6, p. 420–422)
P(Cause, E₁…Eₙ) = P(Cause) ∏ᵢ P(Eᵢ | Cause)
Classification: **P**(Cause | e) = α **P**(Cause) ∏ⱼ P(eⱼ | Cause), over *observed* effects only; unobserved ones sum out to 1. Run time is linear in the number of observed features.

Learning (§21.2.2, p. 778): maximum-likelihood parameters = observed frequencies. With n Boolean attributes there are only **2n + 1** parameters and no search. Avoid zeros: initialise counts to 1 (Laplace-style smoothing) since a zero wipes out all other evidence.

## Worked example (own numbers)
Classes spam (prior 0.4) and ham (0.6). P(w₁|spam)=0.6, P(w₁|ham)=0.1, P(w₂|spam)=0.5, P(w₂|ham)=0.2. Both words present:
- spam: 0.4·0.6·0.5 = 0.12; ham: 0.6·0.1·0.2 = 0.012
- normalise: P(spam|w₁,w₂) = 0.12/0.132 ≈ **0.909**.

## Text classification (p. 421)
Category = cause, HasWordᵢ = effects; P(Category) = fraction of documents, P(HasWordᵢ|Category) = fraction of documents in the class containing the word.

## Pros / cons
+ Fast, scales to huge feature sets, handles noisy/missing data, works well in spam filtering, language ID, retrieval.
− Independence assumption rarely true → posteriors **overconfident** (close to 0/1), though the *ranking* of classes is often right; unsuitable when actual probabilities matter (e.g. medical decisions – use [[bayesian-networks]]).

## Related
[[bayes-theorem]], [[conditional-independence]], [[bayesian-networks]] (naive Bayes is a Bayes net with the class as the only parent), [[supervised-learning]], [[aima-ch12-quantifying-uncertainty]], [[aima-ch21-learning-probabilistic-models]]

## Exam angles
- Compute a posterior with 2–3 features and normalise.
- State the assumption precisely (conditional, not absolute, independence).
- Why is it "naive", and what goes wrong when features are correlated?
- Why smoothing is needed for unseen feature/class combinations.
