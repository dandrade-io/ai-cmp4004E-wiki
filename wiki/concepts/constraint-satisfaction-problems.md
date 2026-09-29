---
title: Constraint Satisfaction Problems (CSP)
type: concept
tags: [search, csp]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Constraint Satisfaction Problems

**Slide 23.** In standard search states are black boxes and only reaching the goal matters. In a CSP, states have **internal structure** (a [[state-representation]] of the *factored* kind): variables with values that must satisfy constraints. Solved when a **complete and consistent assignment** is found. Examples: Sudoku (no repeats in rows/columns/boxes), school scheduling (sports not after lunch).

## Components (slide 24)
- Variables X = {X₁…Xₙ}
- Domains D = {D₁…Dₙ}
- Constraints C
- *Consistent* = violates no constraint; *complete* = every variable assigned.

## Constraint propagation (slide 24)
Reduce domains before/during assignment: **Forward Checking**, **Arc Consistency** → [[arc-consistency-ac3]]. **Minimum Remaining Values** (MRV, "fail-first") is listed with them on the slide, but in AIMA it is a *variable-ordering heuristic* for [[backtracking-search-csp]], not propagation.

> ⚠️ Contradiction (classification): slide 24 groups MRV under constraint propagation; AIMA §5.3.1 (p. 177) treats it as a search heuristic. The heuristic itself is described identically.

## Background (AIMA Ch. 5)
- General CSP solving is **NP-complete** (p. 165); tractable subclasses exist (tree-structured: O(n·d²), p. 185).
- Solve with [[backtracking-search-csp]]: MRV, degree heuristic, least-constraining value, forward checking / MAC, backjumping; or **min-conflicts** local search.
- Formulation extras: unary/binary/global constraints (Alldiff, Atmost), constraint graph and hypergraph, preference constraints → **constrained optimisation problem (COP)**.
- Examples in the book: map colouring (SA has degree 5), job-shop scheduling (T₁ + d₁ ≤ T₂), cryptarithmetic, Sudoku (81 variables, 27 Alldiff).
- Why CSP beats atomic search: fixing SA = blue leaves 2⁵ = 32 instead of 3⁵ = 243 assignments for its five neighbours (–87 %).
- Prolog: `library(clpfd)` = constraint logic programming, AIMA §9.4.5 ([[prolog]], [[first-order-inference]]).

## Related
[[problem-formulation]], [[depth-first-search]]

## Exam angles
- Formulate map colouring / Sudoku / N-queens as a CSP.
- Define consistent vs. complete; explain arc consistency and MRV.

## Source
[[aima-ch05-constraint-satisfaction]].
