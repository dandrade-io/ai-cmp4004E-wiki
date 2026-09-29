---
title: Uninformed (Blind) Search
type: concept
tags: [search]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Uninformed Search

**Slide 6.** The agent knows only the initial state, actions and goal test — no hint about which states are promising. It explores systematically; algorithms differ in **node expansion order**.

## Evaluation criteria
- **Completeness** — finds a solution if one exists?
- **Optimality** — finds the lowest-cost solution?
- **Time complexity** — nodes generated
- **Space complexity** — nodes stored

Parameters: b = branching factor, d = depth of shallowest goal, m = max depth (unverified naming, standard AIMA).

## Algorithms
[[breadth-first-search]] (FIFO), [[depth-first-search]] (LIFO), [[uniform-cost-search]] (priority on g), depth-limited & [[iterative-deepening-search]], [[bidirectional-search]] — all from AIMA §3.4 (pp. 94–102).

## AIMA grounding (§3.3.4, §3.4; [[aima-ch03-solving-problems-by-searching]])
- Criteria: **completeness** (finds a solution when one exists *and correctly reports failure when there is none*), **cost optimality**, time, space. In infinite spaces an algorithm must be **systematic** (e.g. a spiral on an infinite grid) to be complete.
- Parameters: **b** (branching factor), **d** (depth of shallowest solution), **m** (max depth), **ℓ** (depth limit), C* (optimal cost), ε (min action cost).
- Best-first search with different f: BFS f = depth; UCS f = g; DFS f = −depth.

| Criterion | BFS | UCS | DFS | Depth-limited | Iterative deepening | Bidirectional |
|---|---|---|---|---|---|---|
| Complete? | Yes¹ | Yes¹˒² | No | No | Yes¹ | Yes¹˒⁴ |
| Optimal cost? | Yes³ | Yes | No | No | Yes³ | Yes³˒⁴ |
| Time | O(b^d) | O(b^(1+⌊C*/ε⌋)) | O(b^m) | O(b^ℓ) | O(b^d) | O(b^(d/2)) |
| Space | O(b^d) | O(b^(1+⌊C*/ε⌋)) | O(bm) | O(bℓ) | O(bd) | O(b^(d/2)) |
¹ b finite and (space finite or has solution); ² action costs ≥ ε > 0; ³ if all action costs identical; ⁴ if both directions are BFS/UCS. (AIMA Fig. 3.15, p. 102, tree-like versions.)

Uninformed search "cannot solve exponential-complexity problems except the smallest instances": BFS with b = 10, d = 10 needs ~10 TB and < 3 hours; d = 14 takes 3.5 years (p. 95).

## Related
[[informed-search-and-heuristics]], [[repeated-states-and-explored-set]], [[search-algorithms-comparison]]

## Exam angles
- Compare on the four criteria.
- Why blind search fails on large state spaces (exponential).
