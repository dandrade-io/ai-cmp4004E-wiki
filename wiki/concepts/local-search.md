---
title: Local Search
type: concept
tags: [search, optimization]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Local Search

**Idea (AIMA §4.1, p. 128).** When only the *final state* matters (8-queens, chip layout, scheduling), keep just a current state, move to neighbors, and don't store paths or a reached set. Not *systematic* (may never visit the region containing the solution), but uses very little memory and copes with large or infinite spaces. Also solves **optimization problems**: find the best state under an **objective function**.

## State-space landscape (Fig. 4.1)
Elevation = objective value. Features: **global maximum**, **local maximum**, **flat local maximum**, **shoulder**, **ridge**, **plateau**. If elevation = cost, the aim is a global minimum and the process is called **gradient descent** ([[gradient-descent]]). This is the same picture as [[optimization-landscape]] in the slides.

## Algorithms
| Algorithm | Key idea | Weakness |
|---|---|---|
| [[hill-climbing]] | greedy move to best neighbor | stuck at local optima, ridges, plateaus |
| [[simulated-annealing]] | accept worse moves with prob. that falls with badness and T | needs a good cooling schedule |
| Local beam search | keep k states; pool all successors, keep best k (info shared, unlike k restarts) | loss of diversity; stochastic beam search picks ∝ value |
| [[genetic-algorithms]] / [[evolutionary-computation]] | population + selection + crossover + mutation | representation engineering |
| Continuous: gradient/Newton–Raphson | x ← x + α∇f, x ← x − H⁻¹∇f | step size; local optima |

Local beam search with ρ = 1 parent ↔ evolutionary algorithm (asexual); GAs are stochastic beam search plus crossover (p. 136).

## Related
[[metaheuristics]], [[exploration-vs-exploitation]], [[aima-local-search-notes]], [[aima-ch04-search-in-complex-environments]]

## Exam angles
- Local vs. systematic search: trade-offs.
- List the ways hill climbing gets stuck and remedies (sideways moves, restarts, annealing).
