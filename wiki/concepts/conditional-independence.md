---
title: Independence and Conditional Independence
type: concept
tags: [probability, bayesian-networks]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Independence and Conditional Independence

**Intuition.** Independence lets you factor a huge joint into small pieces. Absolute independence is rare; *conditional* independence ("independent once you know the cause") is common and is what makes probabilistic AI scale (AIMA p. 415–420).

## Definitions
- **Independence:** P(a|b) = P(a), or P(a∧b) = P(a)P(b); for variables **P**(X,Y) = **P**(X)**P**(Y). Example: Weather is independent of dental variables → 32-entry table = 8-entry × 4-entry (p. 416).
- **Conditional independence:** **P**(X,Y|Z) = **P**(X|Z)**P**(Y|Z), equivalently **P**(X|Y,Z) = **P**(X|Z).
- Dentist: Toothache and Catch are *not* independent, but are conditionally independent given Cavity (Eq. 12.19).

## Payoff
**P**(Toothache,Catch,Cavity) = **P**(Toothache|Cavity)**P**(Catch|Cavity)**P**(Cavity): 2+2+1 = 5 independent numbers instead of 7. For n symptoms all conditionally independent given the cause, size grows **O(n) instead of O(2ⁿ)** (p. 420).

## In Bayesian networks
A node is conditionally independent of its non-descendants given its parents, and of everything else given its **Markov blanket** (parents, children, children's parents). **d-separation** tests general claims: take ancestral subgraph, "moralize" (marry common parents), drop directions, check whether Z blocks all paths (p. 437).
In [[hidden-markov-models]] the Markov and sensor assumptions are conditional independences.

## Related
[[probability-basics]], [[naive-bayes]], [[bayesian-networks]], [[markov-models]], [[causal-models]]

## Exam angles
- Show that a table shrinks under a conditional-independence assumption (count parameters).
- Give an example where two variables are dependent but conditionally independent given a third.
- Explain the "explaining away" contrast: Burglary and Earthquake are independent, but *not* conditionally independent given Alarm (p. 438).
