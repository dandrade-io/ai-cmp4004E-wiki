---
title: Constraint Handling in EAs
type: concept
tags: [evolutionary, constraints]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Constraint handling in EAs

Variation operators are *blind* to constraints, so offspring of feasible parents may be infeasible (book Ch.13, pp.203–208). Problem types: FOP (fitness only), CSP (constraints only — see [[constraint-satisfaction-problems]]), COP (both).

| Approach | Modifies | Idea |
|---|---|---|
| **Penalty functions** (indirect) | fitness | f'(x) = f(x) + P(d(x,F)); P = Σ wᵢ·dᵢ^κ, κ = 1 or 2. Static (extinctive, binary, distance-based — distance best), dynamic (e.g. (C·t)^α), adaptive (SAW: raise weights of constraints violated by the best individual) |
| **Specialised representation/operators** (direct) | genotype space | e.g. permutations for 8-queens |
| **Repair** | genotype→phenotype mapping | turn infeasible into nearby feasible; **Lamarckian** (overwrite) vs **Baldwinian** (only give the fitness) |
| **Decoder** | mapping | every genotype decodes to a feasible solution (e.g. knapsack: "include item IF it fits") |

**Knapsack penalty example**: capacity 10, chosen items weigh 14 ⇒ e(x) = 4; with w = 5, P = 20 is subtracted from the value. Too severe a penalty blocks exploring the feasible boundary where optima often lie; too weak lets infeasible solutions dominate.

Related: [[parameter-control]], [[memetic-algorithms]], [[genetic-algorithms]].

## Exam angles
- Classify a method (penalty/repair/decoder); design a decoder for the knapsack.
