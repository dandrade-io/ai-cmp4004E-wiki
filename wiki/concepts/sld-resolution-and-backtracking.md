---
title: SLD Resolution and Backtracking
type: concept
tags: [prolog, search, inference]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# SLD Resolution and Backtracking

## Execution model (slide 15)
Prolog answers by SLD resolution = depth-first [[forward-and-backward-chaining|backward chaining]] with [[unification]]:
1. Take the **leftmost** goal.
2. Scan clauses **in file order** for a matching head.
3. Replace the goal by that clause's body.
4. On failure, **backtrack**: undo bindings, try next clause.
5. Succeed when no goals remain.

This is the same as [[depth-first-search]] over the AND–OR graph of [[horn-clauses]]. Consequence: **clause order and goal order change what a logically identical program does.**

## Left recursion
```prolog
link(a, b).   link(b, c).
% base case first: an answer comes back
path(X, Z) :- link(X, Z).
path(X, Z) :- path(X, Y), link(Y, Z).
?- path(a, c).       % true.  (but ; still loops)

% left recursion first: no answer at all
path(X, Z) :- path(X, Y), link(Y, Z).
path(X, Z) :- link(X, Z).
?- path(a, c).       % ERROR: Stack limit (1.0Gb) exceeded
```
"SLD resolution is complete; Prolog's search rule is not."

**AIMA confirmation (§9.4.3, p. 313):** with the clauses in the second order Prolog follows an infinite path, so it is **incomplete as a theorem prover for definite clauses — even for Datalog**. Forward chaining halts on the same program (once path(a,b), path(b,c), path(a,c) are inferred). Depth-first backward chaining also repeats work (877 inferences vs 62 for forward chaining on the layered-graph example; forward chaining ≤ n² path facts). This is dynamic programming: cache subproblem results. **Tabled logic programming** = backward chaining's goal-directedness + dynamic-programming efficiency, and is **complete for Datalog** (an infinite loop is still possible with predicates like `father(X,Y)` that refer to a potentially unbounded number of objects).

## Fix: tabling
`:- table path/2.` memoises subgoals and stops the loop (slides 9, 15, 18) — also fixes naive `fibo` ([[prolog-lists-and-recursion]]).

## Pitfalls
- Put base cases first, recursive call last, and consume input before recursing.
- Surviving choicepoints show as `false.` after `;`.
- Analogy to [[state-space]] search: repeated states cause infinite cycles unless controlled.

## Exam angles
- Trace execution with backtracking on a small KB.
- Explain why the second `path` loops; give three fixes (reorder, tabling, explicit visited list (unverified)).
- Compare with [[prolog-cut]] which prunes choicepoints.

Source: [[aima-ch09-inference-in-first-order-logic]]; execution as AND/OR search: [[first-order-inference]].
