---
title: Depth-First Search (DFS)
type: concept
tags: [search, uninformed]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Depth-First Search

**Intuition.** Follow one branch to the end, then backtrack (slide 9).

**Data structure:** LIFO stack (or recursion).

## Properties (slide 9)
- Complete: only if repeated states are controlled and the space is finite.
- Not optimal.
- Time O(b^m); Space O(b·m) — low memory compared to BFS.

m can be much larger than d, or infinite, so DFS can be very slow on deep/infinite spaces.

## AIMA grounding (§3.4.3, pp. 96–98; [[aima-ch03-solving-problems-by-searching]])
- Usually implemented **tree-like** (no `reached` table); as best-first search it has f = −depth. Not cost-optimal (returns the first solution found).
- Complete for finite tree-shaped or acyclic spaces (may re-expand states via different paths); in **cyclic** spaces it can loop forever (check for cycles up the parent chain); in **infinite** spaces it is **not systematic** and can follow an infinite path even with no cycles → incomplete.
- Memory: frontier is "a radius of the sphere" vs. BFS's surface; O(bm). Some problems needing exabytes with BFS take kilobytes with DFS. DFS is the "workhorse" of constraint satisfaction, propositional satisfiability and logic programming.
- **Backtracking search**: generates one successor at a time and mutates the state in place → memory of one state description plus an O(m) path; needs undoable actions; cycle check in O(1) with a set.
- Fixes: depth-limited / [[iterative-deepening-search]].

## Pros / cons
+ Tiny memory. − May go down infinite branches; non-optimal.

## Related
[[breadth-first-search]], [[repeated-states-and-explored-set]], [[uninformed-search]]. Prolog's execution is depth-first backtracking ([[sld-resolution-and-backtracking]]). Depth-limited/iterative deepening (unverified) fix incompleteness.

## Exam angles
- Compare memory O(bm) vs BFS O(b^d).
- Why is DFS incomplete in cyclic graphs without an explored set?
