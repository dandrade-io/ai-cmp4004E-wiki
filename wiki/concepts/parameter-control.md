---
title: Parameter Control
type: concept
tags: [evolutionary, parameters]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Parameter control (and tuning)

**Tuning** = choose parameter values *before* the run and keep them fixed; **control** = change them *during* the run (book Ch.7–8, [[eiben-ch07-09-parameters-control-and-experiments]]). Fixed values contradict the dynamic nature of a run: large mutation early (exploration), small late (exploitation).

## Three styles (with the mutation step-size example, p.133)
1. **Deterministic**: σ(t) = 1 − 0.9·t/T — blind to the search state. (Cooling schedules in [[simulated-annealing]] are of this kind.)
2. **Adaptive** (feedback): **1/5 success rule** — every k iterations σ' = σ/c if p_s > 1/5, σ·c if p_s < 1/5 (0.817 ≤ c ≤ 1).
3. **Self-adaptive**: parameters in the genome co-evolve → [[self-adaptive-mutation]].

Other classification axes: what is changed (representation, fitness function, mutation, crossover, selection, population), what evidence drives it, scope (gene / individual / population). Example: penalty weight W(t) = (C·t)^α in constrained problems ([[constraint-handling-in-ea]]); GAVaPS removes population size and gives individuals fitness-biased lifetimes.

Related: [[evolution-strategies]], [[exploration-vs-exploitation]], [[genetic-algorithms]].

## Exam angles
- Classify a given scheme as deterministic/adaptive/self-adaptive; apply the 1/5 rule.
