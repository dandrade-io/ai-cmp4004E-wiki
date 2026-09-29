---
title: AIMA Notes on Local Search, Annealing, GAs and Gradients
type: concept
tags: [optimization, local-search, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA Notes on Optimization Topics

Cross-reference page: things AIMA Ch. 4 ([[aima-ch04-search-in-complex-environments]]) says that the optimization pages owned by other ingests ([[simulated-annealing]], [[genetic-algorithms]], [[crossover-and-mutation]], [[gradient-descent]], [[evolutionary-computation]], [[exploration-vs-exploitation]]) may want to absorb. Suggested during lint: merge and delete this page.

## Simulated annealing (AIMA pp. 132–134)
- Metallurgy metaphor: heat, then cool slowly → low-energy crystal. "Ping-pong ball in the deepest crevice of a bumpy surface": shake hard, then less.
- Picks a *random* move; better → accept; worse → accept with probability < 1 that decreases exponentially with badness ΔE and as T falls.
- If T is lowered to 0 **slowly enough**, the Boltzmann distribution concentrates on global optima and SA finds one with probability → 1 (an asymptotic guarantee; no finite-time guarantee).
- History: Kirkpatrick et al. (1983) from the Metropolis algorithm (1953); used for VLSI layout from the 1980s and factory scheduling.
- Compare with the course code: geometric cooling `T *= 0.8` is far too aggressive for the "slowly enough" condition (see [[code-simulated-annealing]]).

## Genetic algorithms (AIMA pp. 133–137)
- Design choices: population size; representation (GA = strings over finite alphabet, evolution strategies = real vectors, genetic programming = programs); **mixing number ρ** (ρ = 2 typical; ρ = 1 ↔ stochastic beam search); selection (fitness-proportional, or tournament — pick n > ρ, keep best ρ); recombination (single crossover point); **mutation rate** (each bit flips with that probability); next generation (offspring only, or **elitism**; culling).
- Fig. 4.6 example: 8-queens as 8-digit strings; fitness = non-attacking pairs (28 for a solution); population fitness 24, 23, 20, 11 (sum 78) → selection probabilities 31 %, 29 %, 26 %, 14 % (fitness ÷ sum; the figure's percentages are printed out of order in the PDF extraction).
- **Schema** theory: a schema is a partial string (e.g. `246*****`); if instances' average fitness exceeds the mean, their count grows. Crossover helps only if blocks are meaningful; GA success depends on careful representation.
- Early on the population is diverse so crossover makes large steps; later small steps.
- Caveat: unclear how much GA appeal is due to the metaphor (p. 137).
- Fig. 4.8 gives a compact algorithm: weighted selection of two parents → REPRODUCE (single crossover point) → mutate with small probability → replace whole population.
- Turing (1950) already suggested genetic algorithms (AIMA p. 36).

## Gradient methods (AIMA pp. 137–140)
- Update x ← x + α∇f(x) (ascent) — [[gradient-descent]] is the same with a minus sign. Step size trade-off; line search; **Newton–Raphson** uses the Hessian: x ← x − H⁻¹∇f.
- **Empirical gradient** = hill climbing on a discretized space; local optima, ridges and plateaus persist in continuous spaces; random restarts and SA help.
- Constrained/convex optimization: linear programming and convex problems are polynomial-time (contrast with heuristics that can't guarantee optimality).

## Related
[[local-search]], [[hill-climbing]], [[metaheuristics]], [[optimization-landscape]]
