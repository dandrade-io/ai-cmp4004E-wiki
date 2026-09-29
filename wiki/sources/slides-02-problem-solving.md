---
title: Slides 02 — Problem Solving
type: source
tags: [search, csp, games]
sources: [raw/slides/02_Problem Solving.pptx]
updated: 2026-09-29
---
# Slides 02 — Problem Solving

**Source:** `raw/slides/02_Problem Solving.pptx` (25 slides; several slides are figures only: 8, 10, 13, 15, 19, 21, 22, 25).

## Summary
Covers goal-based problem-solving agents and search:
- Problem-solving agents and formulation (slides 2–3) → [[problem-solving-agents]], [[problem-formulation]]
- State space, state graph vs. search tree, frontier/explored set (slides 4–5) → [[state-space]], [[repeated-states-and-explored-set]]
- Uninformed search: BFS, DFS (slides 6–9) → [[uninformed-search]], [[breadth-first-search]], [[depth-first-search]]
- Informed search: heuristics, greedy best-first, A* (slides 11–16) → [[informed-search-and-heuristics]], [[greedy-best-first-search]], [[a-star-search]]
- Adversarial search: minimax, alpha–beta (slides 17–22) → [[adversarial-search]], [[minimax]], [[alpha-beta-pruning]]
- Constraint satisfaction problems (slides 23–24) → [[constraint-satisfaction-problems]]

## Key takeaways
- Solution = sequence of actions; assumes observable, deterministic, discrete, static environment (slide 2).
- Evaluate algorithms by completeness, optimality, time, space (slide 6).
- A* is optimal with admissible/consistent h (slide 14).
- Alpha–beta gives O(b^(m/2)) at best (slide 20).

See the summary table: [[search-algorithms-comparison]].

## Errata / notes
> ⚠️ Slide 20's pruning rule is stated loosely ("value at a MIN node falls below α → prune; value at a MAX node rises above β → prune"); the standard rule is prune when α ≥ β. See [[alpha-beta-pruning]].
> Slide 7 says BFS is optimal "when costs are uniform" — correct (unit step costs).
> Slide 16 "Properties of Heuristics" has no extractable text (probably image); admissibility/consistency definitions are filled in from AIMA background in [[informed-search-and-heuristics]].
