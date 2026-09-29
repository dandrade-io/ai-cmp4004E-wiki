---
title: Evolution Strategies (ES)
type: concept
tags: [evolutionary, continuous]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Evolution Strategies (ES)

## Intuition
Evolution of **real-valued vectors** with Gaussian mutation whose step size σ is itself evolved. Invented in the early 1960s by **Rechenberg and Schwefel** (TU Berlin, shape optimisation); multi-membered (μ+λ)/(μ,λ) ES in the 1970s (book p.101).

## Algorithm sketch (Table 6.2)
Representation ⟨x, σ⟩ real vectors; recombination discrete (object variables) / intermediate (strategy parameters), often *global* (multi-parent); Gaussian mutation with self-adaptive σ; parents chosen uniformly; survivors by (μ,λ) or (μ+λ).
- **(1+1)-ES**: mutate x' = x + N(0,σ); keep if better. **(1,1)-ES**: always replace.
- **1/5 success rule** (Rechenberg): if the fraction of successful mutations p_s > 1/5 increase σ (σ' = σ/c); if < 1/5 decrease (σ' = σ·c), 0.817 ≤ c ≤ 1 (book p.133). Derived from analysing (1+1)-ES on the sphere.
- Modern ES self-adapt σ (and rotation angles) — [[self-adaptive-mutation]]; **CMA-ES** is a leading algorithm for hard real-valued problems.

## Selection
(μ,λ) preferred; λ/μ traditionally 7 (recently ~4); takeover time ≈ 2 for (15,100) ⇒ very aggressive ([[selection-mechanisms]]).

## Related
[[evolutionary-programming]], [[differential-evolution]], [[evolutionary-computation]], [[survivor-selection-and-elitism]], [[parameter-control]].

## Exam angles
- Notation (μ,λ) vs (μ+λ): what is kept?
- Apply the 1/5 rule: σ = 1, c = 0.9, p_s = 0.3 > 0.2 ⇒ σ' = 1/0.9 ≈ 1.11.
- Why is σ mutated before x?
