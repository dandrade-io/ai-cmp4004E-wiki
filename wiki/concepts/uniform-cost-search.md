---
title: Uniform-Cost Search (Dijkstra)
type: concept
tags: [search, uninformed]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Uniform-Cost Search (UCS)

**Intuition.** BFS spreads in waves of equal *depth*; UCS spreads in waves of equal *path cost g(n)*. Called **Dijkstra's algorithm** in theoretical CS (AIMA §3.4.2, p. 96). Not in the course slides — background from [[aima-ch03-solving-problems-by-searching]].

## Algorithm
Best-first search with f(n) = g(n) = PATH-COST (`BEST-FIRST-SEARCH(problem, PATH-COST)`, Fig. 3.9). Frontier = priority queue on g. Crucially the goal test is applied **when a node is expanded (popped)**, not when generated: in the Sibiu → Bucharest example the first path found via Fagaras costs 310, but the path via Rimnicu Vilcea and Pitesti (80+97+101 = 278) is found later and is cheaper (Fig. 3.10, p. 97).

## Properties (AIMA Fig. 3.15)
- Complete if all action costs ≥ ε > 0.
- Cost-optimal (first goal popped has minimal cost).
- Time and space O(b^(1+⌊C*/ε⌋)) with C* the optimal cost; can exceed b^d because many cheap steps are explored before one expensive useful step. With equal costs it is b^(d+1) — like [[breadth-first-search]].

## Relations
- [[a-star-search]] with h = 0 is UCS; weighted A* with W = 0 (p. 109).
- Contours are "circular" in g, with no bias toward the goal, unlike A*'s stretched contours (p. 107).

## Related
[[uninformed-search]], [[breadth-first-search]], [[search-algorithms-comparison]]

## Exam angles
- Trace UCS on a weighted graph; explain why the late goal test is required for optimality.
- BFS vs. UCS: when are they identical?
