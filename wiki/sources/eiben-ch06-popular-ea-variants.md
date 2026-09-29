---
title: Eiben & Smith Ch.6 — Popular EA Variants
type: source
tags: [book, evolutionary, variants]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Eiben & Smith, Ch. 6 (pp. 99–116)

Book: [[eiben-smith]]. Each variant is presented as a "sketch" table (representation, recombination, mutation, parent selection, survivor selection).

| Variant (book §) | Representation | Recombination | Mutation | Parent sel. | Survivor sel. | Page |
|---|---|---|---|---|---|---|
| Simple GA (6.1) | bit strings | 1-point | bit flip | fitness prop. (roulette) | generational | [[genetic-algorithms]] |
| Evolution strategies (6.2) | real vectors | discrete / intermediate | Gaussian, self-adaptive σ | uniform random | (μ,λ) or (μ+λ) | [[evolution-strategies]] |
| Evolutionary programming (6.3) | real vectors (orig. FSMs) | none | Gaussian | deterministic (each parent → 1 child) | probabilistic (μ+μ) round-robin | [[evolutionary-programming]] |
| Genetic programming (6.4) | trees | subtree exchange | random subtree change | fitness prop. | generational | [[genetic-programming]] |
| Learning classifier systems (6.5) | rule sets {condition:action:payoff} | 1-point | reset | fitness prop. w/ sharing | stochastic | [[learning-classifier-systems]] |
| Differential evolution (6.6) | real vectors | uniform crossover | **differential mutation** | uniform, 3 vectors | parent vs child | [[differential-evolution]] |
| Particle swarm (6.7) | real vectors | none | add velocity | deterministic | generational | [[particle-swarm-optimization]] |
| Estimation of distribution (6.8) | any (model) | none | sample a fitted model | truncation | generational | [[estimation-of-distribution-algorithms]] |

## Notable statements
- GA: recommended mutation rate between 1/l and 1/μ, p_c ≈ 0.6–0.8, populations "in the fifties or low hundreds" (p.100, reflecting 1980s–90s hardware). SGA lacks elitism; SUS preferred to roulette; tournament is the usual selection; OneMax is "the Drosophila" of combinatorial problems and the SGA "the Drosophila of EAs".
- The book does **not** treat [[ant-colony-optimization]] or [[artificial-bee-colony]]; PSO and DE are placed inside the EA framework.

## Slide comparison
> ⚠️ Contradiction: slide 9 of [[slides-04-optimization]] says φ₁, φ₂ are random variables uniform on [0,1]. The book (p.113) writes v' = w·v + φ₁U₁(y−x) + φ₂U₂(z−x) with **φ_i as weights (learning rates)** and **U_i as the uniform random factors**, plus an **inertia weight w** — see [[particle-swarm-optimization]].
