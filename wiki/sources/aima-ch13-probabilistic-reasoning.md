---
title: "AIMA Ch. 13 – Probabilistic Reasoning"
type: source
tags: [source, book, bayesian-networks]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 13: Probabilistic Reasoning

Book pages 429–~475. See [[russell-norvig]].

## Section map
| § | Title | Book p. | Wiki page |
|---|---|---|---|
| 13.1 | Representing knowledge in an uncertain domain (Bayes net syntax, burglary example) | 430 | [[bayesian-networks]] |
| 13.2 | Semantics; construction; compactness; node ordering; Markov blanket; d-separation; canonical distributions (deterministic, CSI, noisy-OR) | 432 | [[bayesian-networks]], [[conditional-independence]] |
| 13.3 | Exact inference: enumeration (ENUMERATION-ASK), variable elimination, complexity, clustering | 445 | [[bayesian-networks]] |
| 13.4 | Approximate inference: direct, rejection, likelihood weighting, Markov chain (Gibbs) simulation | 453 | [[bayesian-networks]] (headings only) |
| 13.5 | Causal networks: structural equations, do-operator, adjustment formula, back-door criterion | 467 | [[causal-models]] |

## Key facts
- P(x₁…xₙ) = ∏ P(xᵢ|parents). Burglary joint entry 0.000628; P(B|j,m) = ⟨0.284,0.716⟩.
- Network sizes by node ordering: 10 (causal), 13, 31 parameters.
- Enumeration is O(2ⁿ) time, linear space; variable elimination removes repeated subcomputations.
- do(S=true) deletes the incoming equation for S ("mutilated network"); intervening ≠ observing.
- Back-door adjustment: P(g|do(S=true)) = Σᵣ P(g|S=true, r)P(r).

## Not read in detail
§13.3.3–13.3.4 (complexity, clustering), §13.4 (sampling algorithms), continuous-variable CPDs, and the chapter's exercises.

## Link to slides
Slide 01, slides 10 and 15 mention Bayesian/Markov networks and Pearl's causal calculus ([[slides-01-introduction-to-ai]], [[judea-pearl]]).
