---
title: Admissible and Consistent Heuristics
type: concept
tags: [search, heuristics]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Admissible and Consistent Heuristics

The slides' "Properties of Heuristics" slide (slide 16 of [[slides-02-problem-solving]]) is image-only; this page grounds the content in AIMA §3.5–3.6 ([[aima-ch03-solving-problems-by-searching]]).

## Definitions (AIMA pp. 104–106)
- **Admissible:** h(n) ≤ h*(n), the true cheapest cost from n to a goal — never overestimates ("optimistic"). With an admissible h, [[a-star-search]] is cost-optimal.
- **Consistent (monotonic):** h(n) ≤ c(n, a, n′) + h(n′) for every successor n′ — a **triangle inequality**. *Every consistent heuristic is admissible; not vice versa.* "Monotonic" and "consistent" are synonyms (footnote 13, Pearl 1984).
- Consistency ⇔ f = g + h is non-decreasing along any path (p. 108); the first time a state is reached it is via an optimal path, so no state is ever re-added to the frontier.
- Example: straight-line distance h_SLD is consistent (Romania, Fig. 3.16).

## A* optimality proof sketch (p. 106)
Suppose A* returns cost C > C*. Some node n on the optimal path is unexpanded, so f(n) > C*. But f(n) = g*(n) + h(n) ≤ g*(n) + h*(n) = C* by admissibility — contradiction.

## Inadmissible heuristics
May overestimate; A* may lose optimality but expand fewer nodes. Optimal anyway if one optimal path has admissible h at every node, or if overestimation never exceeds C₂ − C* (second-best minus best cost) (p. 108). **Weighted A\***: f = g + W·h, W > 1, returns cost between C* and W·C* (p. 109).

## Heuristic quality (pp. 115–118)
- 8-puzzle: **h1 = misplaced tiles** (start state: 8), **h2 = Manhattan distance** (start: 18); true cost 26; both admissible.
- **Effective branching factor** b*: N + 1 = 1 + b* + (b*)² + … + (b*)^d; good heuristics have b* near 1. Fig. 3.26: at d = 24, BFS 290,082 nodes (b* 1.62); A*(h1) 53,039 (1.50); A*(h2) 5,733 (1.36).
- **Dominance:** h2(n) ≥ h1(n) for all n ⇒ A* with h2 never expands more nodes than with h1 (except ties); prefer larger consistent heuristics if cheap to compute.
- **Relaxed problems:** the exact cost of a relaxed problem (fewer restrictions on actions) is admissible and consistent. Rule "a tile can move from X to Y if X is adjacent to Y **and** Y is blank": (a) drop "blank" → Manhattan distance h2; (c) drop both conditions → misplaced tiles h1; (b) drop "adjacent" is left as an exercise (p. 118). The relaxed problems must be solvable essentially without search.
- **max of admissible heuristics** is admissible and dominates each component; **pattern databases** use subproblem costs; landmarks; learned heuristics.

## Slide check
> ⚠️ Contradiction (refinement): [[slides-02-problem-solving]] slide 14 says "optimal if h is admissible/consistent" and the earlier wiki text said consistency is *needed* for A* graph search. In AIMA's formulation (best-first search with a `reached` table that re-adds a state when a cheaper path is found) A* is cost-optimal with an **admissible** h; with an *inconsistent* h it may re-reach states through cheaper paths, costing extra time and space (p. 106). Consistency is thus about efficiency (each state expanded once), not correctness. Classic explored-set (no re-opening) graph search *does* require consistency (unverified — standard result from earlier AIMA editions).

## Related
[[informed-search-and-heuristics]], [[greedy-best-first-search]], [[metaheuristics]] (different meaning of "heuristic")

## Exam angles
- Prove that a consistent heuristic is admissible (induction on distance to goal — (unverified) standard proof).
- Show h2 dominates h1 for the 8-puzzle and interpret the table.
- Give a relaxed problem that yields a given heuristic.
