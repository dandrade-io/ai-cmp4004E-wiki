---
title: Differential Evolution (DE)
type: concept
tags: [evolutionary, continuous]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Differential Evolution (DE)

Storn & Price, 1995: heuristic for minimising non-linear, non-differentiable continuous functions (book §6.6, pp.110–112).

## Operators
- **Differential mutation**: mutant v = x + F·(y − z), with y, z random population members, scale F > 0 (variant: base vector randomly chosen).
- **Uniform crossover** with probability Cr between mutant and x; one random position always taken from the mutant (child ≠ x).
- **Selection**: trial vector u replaces x if f(u) ≤ f(x) (deterministic, parent vs child).
- Parameters: F, population size NP (μ), Cr. Notation **DE/a/b/c**: base vector (rand/best), number of difference vectors, crossover (bin). Basic = **DE/rand/1/bin**; two differences: p = F·(y − z + y' − z').

## Worked example
x = (1,2), y = (3,4), z = (2,1), F = 0.5 ⇒ p = 0.5·(1,3) = (0.5,1.5); mutant = x + p = (1.5, 3.5). With Cr = 0.5 each coordinate is taken from the mutant w.p. 0.5 (one forced).

Related: [[particle-swarm-optimization]], [[evolution-strategies]], [[evolutionary-computation]].

## Exam angles
- Do one DE generation for a single individual; interpret F and Cr.
