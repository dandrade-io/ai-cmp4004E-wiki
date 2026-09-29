---
title: Breadth-First Search (BFS)
type: concept
tags: [search, uninformed]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Breadth-First Search

**Intuition.** Expand the shallowest nodes first, level by level (slide 7).

**Data structure:** FIFO queue.

## Pseudocode (AIMA Fig. 3.9, p. 95)
```
function BREADTH-FIRST-SEARCH(problem):
  node ← NODE(problem.INITIAL); if IS-GOAL(node.STATE) return node
  frontier ← FIFO queue [node]; reached ← {problem.INITIAL}
  while frontier not empty:
    node ← POP(frontier)
    for child in EXPAND(problem, node):
      s ← child.STATE
      if IS-GOAL(s) return child            # early goal test
      if s ∉ reached: add s to reached; add child to frontier
  return failure
```
Efficiency tricks over generic best-first search: FIFO queue instead of priority queue (new nodes are deeper, so they go to the back); `reached` can be a *set* since the first path to a state is the shallowest; **early goal test** on generation.

## Properties (slide 7; AIMA Fig. 3.15)
- Complete: yes if b is finite — systematic even in infinite spaces.
- Optimal: yes for uniform step costs (fewest steps).
- Time O(b^d); Space O(b^d) — the frontier grows exponentially; memory is the bottleneck.

## AIMA numbers (p. 95)
All 1 + b + b² + … + b^d = O(b^d) nodes stay in memory. With b = 10, 1 million nodes/s and 1 KB/node: depth 10 → < 3 hours but **10 TB** of memory; depth 14 → **3.5 years**. Memory is the bigger problem. BFS finds a solution with the minimal number of actions; cost-optimal only if all actions cost the same (else use [[uniform-cost-search]]).

## Pros / cons
+ Guarantees shallowest solution. − Exponential memory; ignores costs.

## Related
[[depth-first-search]], [[uninformed-search]], [[uniform-cost-search]], [[iterative-deepening-search]], [[a-star-search]] (A* with h = 0 is uniform-cost search; with unit costs, BFS-like), [[search-algorithms-comparison]]

## Exam angles
- Why memory, not time, usually kills BFS.
- Non-uniform costs → BFS not optimal (use uniform-cost search).
