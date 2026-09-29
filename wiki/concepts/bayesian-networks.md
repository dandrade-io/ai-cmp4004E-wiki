---
title: Bayesian Networks
type: concept
tags: [probability, graphical-models, inference]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Bayesian Networks

**Intuition.** A compact way to write a full joint distribution: a DAG says who directly influences whom, and each node stores only a *local* conditional table given its parents (AIMA §13.1, p. 430).

## Definition
1. One node per random variable. 2. Directed links parent → child, no cycles (DAG). 3. Each node has **P**(Xᵢ | Parents(Xᵢ)), a CPT for discrete variables (each row sums to 1; a Boolean node with k Boolean parents needs 2ᵏ numbers).

**Semantics (p. 432):** P(x₁,…,xₙ) = ∏ᵢ P(xᵢ | parents(Xᵢ)).

## Burglary example (Pearl; p. 431–433)
Burglary (0.001), Earthquake (0.002) → Alarm ← ; Alarm → JohnCalls (0.90 | a, 0.05 | ¬a), Alarm → MaryCalls (0.70 | a, 0.01 | ¬a). P(A|B,E)=0.95, P(A|B,¬E)=0.94, P(A|¬B,E)=0.29, P(A|¬B,¬E)=0.001.
- P(j,m,a,¬b,¬e) = 0.90·0.70·0.001·0.999·0.998 = **0.000628**.
- Query by enumeration: P(B | j,m) = α P(b) Σₑ P(e) Σₐ P(a|b,e)P(j|a)P(m|a) → ⟨0.284, 0.716⟩ (p. 446). Verified numerically: 0.00059224 vs 0.0014919.

## Construction (p. 433–436)
Order variables, ideally **causes before effects**; for each Xᵢ choose a minimal parent set among earlier variables such that Xᵢ is conditionally independent of the rest given parents. Bad order ⇒ bushy network: for the burglary domain 10 parameters (causal order) vs 13 (M,J,A,B,E) vs 31 (M,J,E,B,A). All represent the same joint. Compactness: n=30 nodes, k=5 parents → 960 numbers vs >10⁹ for the joint.

## Independence structure
Non-descendants given parents; **Markov blanket**; **d-separation** (see [[conditional-independence]]). Canonical CPTs: deterministic nodes, context-specific independence, **noisy-OR** (p. 438).

## Inference (§13.3–13.4)
- **Enumeration:** sum joint terms; O(2ⁿ) time, linear space (p. 445–447).
- **Variable elimination:** dynamic programming over factors, avoids recomputation (p. 448).
- Exact inference is intractable in general (#P-hard, unverified detail); use **approximate inference**: direct/rejection/likelihood sampling, **Markov chain simulation** (Gibbs) (p. 453–466).

## Causal networks (§13.5)
Arrows read as causal assignments allow interventions with the **do-operator** – see [[causal-models]].

## Pros / cons
+ Compact, modular, transparent; robust causal parameters. − Structure must be built or learned; exact inference can be exponential.

## Related
[[probability-basics]], [[naive-bayes]] (star-shaped special case), [[hidden-markov-models]] (temporal Bayes nets), [[judea-pearl]], [[bayes-and-markov-worked-examples]], [[aima-ch13-probabilistic-reasoning]]

## Exam angles
- Compute a joint entry from CPTs; count parameters of a network vs the full joint.
- Explain why causal ordering gives smaller networks.
- Given a small graph, state which variables are d-separated / conditionally independent.
- Set up (not necessarily finish) an enumeration query.
