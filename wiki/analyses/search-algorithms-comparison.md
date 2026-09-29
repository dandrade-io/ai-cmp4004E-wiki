---
title: Search Algorithms Comparison
type: analysis
tags: [search, study-guide]
sources: [raw/slides/02_Problem Solving.pptx]
updated: 2026-09-29
---
# Search Algorithms Comparison

b = branching factor, d = depth of shallowest goal, m = maximum depth. Values from slides 7, 9, 12, 14, 18, 20 of [[slides-02-problem-solving]].

| Algorithm | Data structure | Complete? | Optimal? | Time | Space |
|---|---|---|---|---|---|
| [[breadth-first-search]] | FIFO queue | Yes | Yes (uniform cost) | O(b^d) | O(b^d) |
| [[depth-first-search]] | LIFO stack | Only if finite space + repeated states controlled | No | O(b^m) | O(b·m) |
| [[greedy-best-first-search]] | Priority queue on h | Only if repeated states controlled | No | O(b^m) worst (unverified) | O(b^m) worst (unverified) |
| [[a-star-search]] | Priority queue on f=g+h | Yes (h admissible) | Yes (h admissible/consistent) | Depends on h | O(b^d) |
| [[minimax]] | Recursive DFS | Yes (finite tree) | Yes vs. optimal opponent | O(b^m) | O(b·m) |
| [[alpha-beta-pruning]] | Recursive DFS + α,β | Yes | Same as minimax | O(b^(m/2)) best case | O(b·m) |

## Quick rules
- Need shortest path, memory OK → BFS (unit costs) or A*.
- Memory tight → DFS (accept non-optimal).
- Have a good admissible h → A*; speed over optimality → greedy.
- Two-player zero-sum → minimax + alpha–beta.

Related: [[uninformed-search]], [[informed-search-and-heuristics]], [[adversarial-search]].

## Exam angles
Most common question: fill in this table from memory and justify each cell.
