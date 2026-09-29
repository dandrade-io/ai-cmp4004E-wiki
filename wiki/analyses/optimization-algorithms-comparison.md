---
title: Optimization Algorithms — Comparison
type: analysis
tags: [optimization, comparison, study-guide]
sources: [raw/slides/04_Optimization.pptx, raw/code/gd_functions.py, raw/code/sa_functions.py, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Optimization Algorithms — Comparison

| | [[gradient-descent]] | [[simulated-annealing]] | [[genetic-algorithms]] | [[particle-swarm-optimization]] | [[ant-colony-optimization]] | [[artificial-bee-colony]] |
|---|---|---|---|---|---|---|
| **Inspiration** | calculus / steepest descent | metal annealing | natural selection | bird flocks, fish schools | ant pheromone trails | honeybee foraging |
| **Year / author** | classical | Kirkpatrick et al. 1983 (unverified) | Holland 1975 | Kennedy & Eberhart 1995 | Dorigo ~1996 | Karaboga 2007 |
| **Representation** | real vector w | any (vector in course code) | bit string (classic) | real vector + velocity | paths/tours on a graph | real vector (food source) |
| **Population?** | single | single | population | swarm | colony of ants | colony of bees |
| **Gradient needed?** | **Yes** | No | No | No | No | No |
| **Key parameters** | η, iterations | T0, cooling α, step | pop size, p_c, p_m | swarm size, w, c1, c2 | α, β, ρ, #ants | BN/SN, limit, MCN |
| **Explore / exploit** | pure exploitation (local) | temperature: high→explore | mutation vs selection/crossover | inertia/φ vs p_best/g_best | evaporation vs reinforcement | scouts vs employed/onlookers |
| **Typical use** | smooth, differentiable (ML training) | discrete/continuous, escaping local minima | discrete/combinatorial, design | continuous tuning | TSP, routing | continuous numeric optimization |

## Rules of thumb (background)
- Differentiable and (near) convex → gradient descent.
- Multimodal, cheap evaluations → SA/PSO/GA.
- Graph/path problems → ACO.
- Discrete encodings, recombination meaningful → GA.

Concepts: [[exploration-vs-exploitation]], [[metaheuristics]], [[optimization-landscape]], [[swarm-intelligence]], [[evolutionary-computation]], [[benchmark-functions]]. Source: [[slides-04-optimization]].

## Exam angles
Be able to fill this table from memory and justify which algorithm suits a given problem.

## Evolutionary variants (Eiben & Smith Ch.6) — add to the picture
| | Representation | Variation | Selection | Speciality |
|---|---|---|---|---|
| [[genetic-algorithms]] | bit strings | 1-pt crossover + bit flip | FPS/tournament, generational | building blocks |
| [[evolution-strategies]] | real vectors | Gaussian (+recomb.) | (μ,λ)/(μ+λ) | self-adaptive σ, 1/5 rule |
| [[evolutionary-programming]] | real vectors / FSM | Gaussian only | round-robin (μ+μ) | no crossover |
| [[genetic-programming]] | trees | subtree crossover/mutation | FPS + over-selection | bloat |
| [[differential-evolution]] | real vectors | F·(y−z) + uniform crossover | parent vs child | 3 parameters F, Cr, NP |
| [[particle-swarm-optimization]] | real vectors | velocity with p_best/g_best | none (all move) | inertia w |
| [[memetic-algorithms]] | any | EA + local search | — | fine-tuning |
NFL warning: no row wins everywhere — [[no-free-lunch-theorem]]. Book also notes 1980s "EAs are uniformly good" belief is outdated.
