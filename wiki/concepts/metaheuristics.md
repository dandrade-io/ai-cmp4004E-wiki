---
title: Metaheuristics
type: concept
tags: [optimization, heuristics]
sources: [raw/slides/04_Optimization.pptx, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Metaheuristics

## Definition
High-level, problem-independent search strategies that guide lower-level heuristics to find good (not provably optimal) solutions to hard optimization problems. Slide 12 describes ACO as "based on metaheuristic optimization" for combinatorial problems.

## Taxonomy (background; EA-book context below)
- **Trajectory-based (single solution):** [[simulated-annealing]], hill climbing, tabu search.
- **Population-based:** [[genetic-algorithms]] / [[evolutionary-computation]]; [[swarm-intelligence]] ([[particle-swarm-optimization]], [[ant-colony-optimization]], [[artificial-bee-colony]]).
Contrast with exact/gradient methods ([[gradient-descent]]).

## Common traits
Stochastic, gradient-free, need only an objective evaluation, balance [[exploration-vs-exploitation]], no optimality guarantee, several tunable parameters.

## Relation to search
Heuristic idea parallels [[informed-search-and-heuristics]] (h(n) guides A*), but here the heuristic guides randomized moves across an [[optimization-landscape]] rather than expanding a tree.

## Exam angles
- Why use a metaheuristic instead of exact search? (NP-hard, huge spaces)
- Classify each algorithm as trajectory or population based.
- See the [[optimization-algorithms-comparison]] table.

## In Eiben & Smith (§3.7, pp.46–48)
Exact methods (enumeration, branch & bound) blow up on NP-hard problems (TSP has n!/2 tours); **heuristics** define which candidate to test next. **Local search / hill climbing** explores a neighbourhood N(x) and stops at a *local optimum* (neighbourhood structure changes which points are local optima; the global optimum is optimal under every neighbourhood). Escape ideas: variable-neighbourhood search, tabu search, [[simulated-annealing]] (convergence proofs exist but they do not certify optimality). EAs differ by using a **population** to define a non-uniform sampling distribution via recombination and by keeping diversity. **NFL:** no metaheuristic wins on all problems — [[no-free-lunch-theorem]]; add problem knowledge via [[memetic-algorithms]].
