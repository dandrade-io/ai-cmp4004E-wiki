---
title: Informed Search and Heuristics
type: concept
tags: [search, heuristics]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Informed Search & Heuristics

**Slide 11.** Uses problem-specific knowledge, encoded in a function, to guide exploration toward the goal. A heuristic is an *estimate*, not a guarantee; a good one dramatically reduces nodes explored.

**h(n)** = estimated cost from n to the goal; h(goal) = 0; h(n) ≥ 0.

## Admissible and consistent (slide 16 is image-only; grounded in AIMA §3.5–3.6)
Full treatment in [[admissible-and-consistent-heuristics]]. In brief:
- **Admissible:** h(n) ≤ h*(n) — never overestimates; A* is then cost-optimal.
- **Consistent (monotonic):** h(n) ≤ c(n,a,n′) + h(n′) — triangle inequality; consistent ⇒ admissible; f non-decreasing along paths (AIMA pp. 104–108).
- **Dominance:** h₂(n) ≥ h₁(n) for all n ⇒ A* with h₂ never expands more nodes. 8-puzzle: h1 (misplaced tiles) vs. h2 (Manhattan) — at d = 24, 53,039 vs. 5,733 nodes (Fig. 3.26).
- **Creating heuristics:** optimal cost of a **relaxed problem**, pattern databases, landmarks, max of several admissible heuristics, learning from experience (§3.6).
- **Effective branching factor** b* measures heuristic quality (close to 1 is best).

AIMA definition (p. 102): *"h(n) = estimated cost of the cheapest path from the state at node n to a goal state."* A heuristic needs world knowledge (h_SLD cannot be computed from ACTIONS/RESULT alone); it operates on a node only by tradition (really on the state).

## Algorithms
[[greedy-best-first-search]] (orders by h), [[a-star-search]] (orders by g+h), weighted A* (g + W·h, W > 1; bounded-suboptimal; W = 0 UCS, W = ∞ greedy, p. 109), speedy search (unbounded-cost variant: greedy on estimated number of actions), memory-bounded variants (IDA*, RBFS, SMA*) — [[aima-ch03-solving-problems-by-searching]].

## Related
[[uninformed-search]], [[search-algorithms-comparison]], [[metaheuristics]] (different sense of "heuristic")

## Exam angles
- Prove/check admissibility of a given h; compare two heuristics by dominance.
- Why straight-line distance is admissible.
