---
title: Hill Climbing
type: concept
tags: [search, optimization, local-search]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Hill Climbing (Greedy Local Search)

Not in the slides directly, but the course's [[gradient-descent]] and the degenerate behavior of [[code-simulated-annealing]] are both hill climbing in disguise. Source: AIMA §4.1.1, pp. 129–132 ([[aima-ch04-search-in-complex-environments]]).

## Algorithm (Fig. 4.2)
```
current ← problem.INITIAL
loop:
  neighbor ← highest-valued successor of current
  if VALUE(neighbor) ≤ VALUE(current): return current
  current ← neighbor
```
"Trying to find the top of Mount Everest in a thick fog while suffering from amnesia." Using the negative of a heuristic cost as objective climbs toward the goal.

## 8-queens example
Complete-state formulation: one queen per column, random start; successors = move one queen within its column (8×7 = 56); h = number of attacking pairs. Steepest ascent **gets stuck 86 %** of the time (solves 14 %), ~4 steps on success; allowing up to 100 consecutive **sideways moves** raises success to **94 %** (≈21 steps on success, 64 on failure).

## Ways to get stuck
Local maxima, ridges (sequences of local maxima), plateaus (flat local maxima or shoulders).

## Variants
Stochastic hill climbing (random uphill move, prob. by steepness); **first-choice** (generate successors randomly until one is better — good with thousands of successors); **random-restart** (complete with probability 1; expected restarts 1/p, p ≈ 0.14 → ≈ 7 iterations, ≈ 22 steps; with sideways moves ≈ 25 steps); [[simulated-annealing]] (allows downhill moves).

## Landscape
Few local maxima → random restarts work well; NP-hard problems often have exponentially many local maxima ("balding porcupines") but a decent local maximum is usually found after few restarts (p. 132).

## Related
[[local-search]], [[optimization-landscape]], [[greedy-best-first-search]] (analogous greed in path search), [[exploration-vs-exploitation]]

## Exam angles
- Explain why hill climbing fails on ridges/plateaus; compute expected number of restarts 1/p.
- Compare with simulated annealing (when T → 0 SA becomes hill climbing).
