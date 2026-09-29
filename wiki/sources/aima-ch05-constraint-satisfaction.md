---
title: "AIMA Ch. 5 — Constraint Satisfaction Problems"
type: source
tags: [csp, search, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 5 — Constraint Satisfaction Problems (pp. 164–~190)

Book: [[russell-norvig]]. Course slides: [[slides-02-problem-solving]] (slides 23–24). Note: in this edition CSPs are **Ch. 5** and adversarial search is **Ch. 6** (the order is the reverse of the slide deck's).

## Summary
Breaks open the "black box" state: a **factored** representation ([[state-representation]]) of variables, domains and constraints lets general-purpose (not domain-specific) methods prune whole regions of the search space at once (p. 164).

## 5.1 Defining CSPs (pp. 164–170)
- CSP = ⟨X, D, C⟩; constraint = ⟨scope, rel⟩ (p. 164). *Consistent/legal* assignment violates nothing; *complete* assigns every variable; *solution* = consistent + complete; solving a general CSP is **NP-complete** (p. 165).
- Examples: Australia map colouring (7 variables, 9 constraints, Fig. 5.1), job-shop scheduling with precedence T1 + d1 ≤ T2 and disjunctive constraints (pp. 166–167), 8-queens, cryptarithmetic (Alldiff + carry variables, Fig. 5.2), Sudoku (81 variables, 27 Alldiff units).
- Why CSP? Once SA = blue, five neighbours have 2^5 = 32 options instead of 3^5 = 243 (–87 %) (p. 165).
- Variations: discrete finite / infinite / continuous domains (linear programming is polynomial); unary, binary, ternary, **global** (Alldiff, Atmost) constraints; hypergraph and dual-graph transformations; **preference constraints → constrained optimisation problem (COP)** (pp. 167–169).

## 5.2 Constraint propagation (pp. 169–175)
Node consistency, **arc consistency + AC-3** (O(c·d³)), path consistency, k-consistency, global constraints (Alldiff inconsistency test m > n; Atmost; bounds propagation), Sudoku (AC-3 solves only the easiest puzzles). → [[arc-consistency-ac3]].

## 5.3 Backtracking search (pp. 175–183)
Commutativity (n!·dⁿ leaves → dⁿ), SELECT-UNASSIGNED-VARIABLE (**MRV**, degree heuristic), ORDER-DOMAIN-VALUES (**least-constraining value**), INFERENCE (**forward checking**, **MAC**), conflict-directed backjumping, constraint learning (no-goods). → [[backtracking-search-csp]].

## 5.3.5 Local search for CSPs (p. 182–183)
**Min-conflicts**: pick a conflicted variable, choose the value that minimises conflicts; solves million-queens in ≈ 50 steps after initial placement. Related to [[simulated-annealing]] / hill climbing ([[optimization-landscape]]).

## 5.4 Structure of problems (pp. 183–188)
Independent subproblems (e.g. Tasmania); **tree-structured CSPs solved in O(n·d²)** (arc-consistency + assignment in topological order); cutset conditioning O(d^c·(n−c)d²); tree decomposition also O(n·d²) per tree (tree-width matters).

## Derived / updated pages
[[constraint-satisfaction-problems]], [[arc-consistency-ac3]], [[backtracking-search-csp]], [[n-queens-prolog]] (same problem, different formulation).

## Slide vs. book
> ⚠️ Contradiction (classification): [[slides-02-problem-solving]] slide 24 lists "Forward Checking, Arc Consistency, Minimum Remaining Values" together under "constraint propagation". In the book only forward checking / arc consistency / MAC are *inference* (propagation); **MRV is a variable-ordering heuristic** used inside backtracking (§5.3.1, p. 177).
