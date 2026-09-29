---
title: Benchmark Functions
type: concept
tags: [optimization, testing]
sources: [raw/code/sa_functions.py, raw/code/gd_functions.py, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Benchmark Functions

Standard test surfaces for comparing optimizers. Known optimum ⇒ error is measurable.

| Function | Formula (n dims) | Global min | Landscape |
|---|---|---|---|
| **Sphere / quadratic** | Σ xᵢ² (course: (x−2)²+(y+2)²) | 0 at center (course: (2,−2)) | convex, unimodal |
| **Rastrigin** | 10n + Σ(xᵢ² − 10cos(2πxᵢ)) | 0 at origin | highly multimodal, regular grid of local minima; domain ±5.12 |
| **Ackley** | −20e^{−0.2√(½Σxᵢ²)} − e^{½Σcos(2πxᵢ)} + e + 20 | 0 at origin | nearly flat outer region, one deep central funnel, many small ripples |

Sources: Rastrigin and Ackley in [[code-simulated-annealing]] (Ackley defined but unused); quadratic in [[code-gradient-descent]]. Formulas for Rastrigin/Ackley match the code; domain notes are background. Book guidance below.

## Use
Sphere tests basic convergence speed ([[gradient-descent]] excels). Rastrigin/Ackley punish greedy methods that fall into local minima and reward [[simulated-annealing]], [[genetic-algorithms]], [[particle-swarm-optimization]]. See [[optimization-landscape]].

## Exam angles
- Which function would gradient descent solve easily, and which trap it?
- Evaluate Rastrigin at (0,0) → 0; at (1,1) → 2.

## Good practice (Eiben & Smith §9.3, pp.158–160)
Ackley, Griewank and Rastrigin are now "obligatory" test functions; the older **De Jong five-function suite** is outdated. Bäck & Michalewicz: a suite should contain a few **unimodal** functions (speed), several **multimodal** functions with exponentially many local optima, a **noisy** function, **constrained** problems, and **high-dimensional, scalable** functions (2-D toy problems are solvable by classical methods). Risk: the community over-fits algorithms to the same functions; report SR (success rate) and MBF over many runs and test significance (t-test/ANOVA/rank tests). See [[eiben-ch07-09-parameters-control-and-experiments]].
