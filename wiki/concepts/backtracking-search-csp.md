---
title: Backtracking Search for CSPs
type: concept
tags: [csp, search, heuristics]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Backtracking Search for CSPs

Source: AIMA §5.3–5.4 (pp. 175–188), [[aima-ch05-constraint-satisfaction]]. Slides only name the ingredients (slide 24).

## Why backtracking
A naive search over partial assignments has n!·dⁿ leaves; **commutativity** (order of assignments is irrelevant) means only one variable per node is chosen → **dⁿ** leaves (p. 175). BACKTRACKING-SEARCH (Fig. 5.5) is recursive [[depth-first-search]] that assigns one variable at a time, tries values, and undoes on failure.

```
BACKTRACK(csp, assignment):
  if complete: return assignment
  var ← SELECT-UNASSIGNED-VARIABLE
  for value in ORDER-DOMAIN-VALUES(var):
      if consistent: add; inferences ← INFERENCE(...)
         if no failure: result ← BACKTRACK(...); if ok return
      remove var=value and inferences
  return failure
```

## Domain-independent heuristics (pp. 177–178)
| Choice | Heuristic | Idea |
|---|---|---|
| Variable | **MRV** (fewest legal values; "fail-first") | detect failure early |
| Variable (tie-break) | **Degree** (most constraints on unassigned vars) | reduce branching |
| Value | **Least-constraining value** | leave most freedom; only one solution needed ("fail-last") |

## Inference during search (pp. 178–179)
- **Forward checking**: after X = v, delete inconsistent values from unassigned neighbours; backtrack when a domain empties.
- **MAC**: run [[arc-consistency-ac3]] from the neighbours of X; catches conflicts FC misses.

## Looking backward (pp. 179–181)
Chronological backtracking wastes effort (recolouring Tasmania). **Conflict sets** → **backjumping**; **conflict-directed backjumping**; **constraint learning / no-goods**. Simple backjumping is redundant when FC or MAC is used.

## Local search: min-conflicts (pp. 182–183)
Complete assignment; repeatedly pick a conflicted variable and reassign it the value with fewest conflicts. Near-constant time on n-queens (million queens in ≈ 50 steps) because solutions are dense. Cf. [[simulated-annealing]] and plateau search in [[optimization-landscape]].

## Problem structure (pp. 183–188)
Independent components; **tree-structured CSP** solved in O(n d²) (make arcs consistent in reverse topological order, then assign forward); **cutset conditioning** O(d^c (n−c) d²); **tree decomposition**.

## Exam angles
- Order variables with MRV then degree on the Australia map (SA first? — MRV ties initially, degree picks SA with degree 5).
- Explain fail-first vs fail-last.
- Compare FC and MAC; give the AC-3 complexity.

Related: [[constraint-satisfaction-problems]], [[n-queens-prolog]] (Prolog's interleaved generate-and-test ≈ backtracking with early pruning).
