---
title: A* Search
type: concept
tags: [search, informed]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# A* Search

**Intuition.** Balance cost so far and estimated cost to go.

**Slide 14.** Expand the node with lowest **f(n) = g(n) + h(n)**, using a priority queue on f.
- g(n): actual cost from start to n
- h(n): heuristic estimate from n to goal
- f(n): estimated total cost of the cheapest path through n

## Pseudocode (AIMA §3.5.2: best-first search with f = g + h)
```
A*(problem, h): BEST-FIRST-SEARCH(problem, f = λn. g(n) + h(n))
  # frontier = priority queue on f; reached table; re-add a state if reached by a cheaper path
  # late goal test: a goal is only returned when popped
```
Romania trace (AIMA Fig. 3.18, p. 106): Bucharest first appears on the frontier via Fagaras with f = 450 but is **not** returned because Pitesti has f = 417; expanding Pitesti yields a Bucharest node with f = 418 (= 418 + 0), which is then popped and is the optimal path (Arad–Sibiu–Rimnicu Vilcea–Pitesti–Bucharest). Timisoara (447) and Zerind (449) are never expanded — **pruning**.

## Properties (slide 14; AIMA §3.5.2–3.5.3, pp. 103–109)
- Complete (finite b, action costs ≥ ε > 0, solution exists or finite space).
> ⚠️ Contradiction: the slide says "complete … if h is admissible"; in AIMA completeness holds regardless of h (footnote 11); admissibility/consistency is what guarantees **cost-optimality** ([[aima-ch03-solving-problems-by-searching]]).
- Cost-optimal if h is **admissible** (proof by contradiction, p. 106). With a **consistent** h each state is reached first via an optimal path so it is never re-added ([[admissible-and-consistent-heuristics]]).
- **Optimally efficient** with a consistent h: any algorithm using the same heuristic must expand every node A* surely expands (all nodes with f < C*).
- Expands: all nodes on paths with f < C*; maybe some with f = C*; none with f > C*. **Search contours** stretch toward the goal (UCS contours are circles in g).
- Still exponential in the worst case (e.g. a vacuum world with N dirty squares: all 2^N cleaned-subsets have f < C*).
- Space O(b^d) — stores all nodes; time depends on quality of h.
- Special cases (unverified): h = 0 → uniform-cost search; g = 0 → greedy best-first.

## Variants (AIMA §3.5.4–3.5.5)
- **Weighted A\***: f = g + W·h, W > 1 — explores far fewer nodes (7× fewer, path 5 % costlier in Fig. 3.21) and returns cost between C* and W·C*. Special cases: W=0 → [[uniform-cost-search]], W=1 → A*, W=∞ → [[greedy-best-first-search]].
- **Memory-bounded:** IDA*, recursive best-first search, SMA*; reference counts; bidirectional heuristic search.
- With an inadmissible h A* may or may not be optimal (optimal if one optimal path has admissible h at every node, or if overestimates ≤ C₂ − C*).

## Pros / cons
+ Optimal, optimally efficient among algorithms using the same h. − Memory-hungry (IDA*, RBFS are memory-bounded fixes).

## Related
[[informed-search-and-heuristics]], [[greedy-best-first-search]], [[breadth-first-search]], [[search-algorithms-comparison]]

## Exam angles
- Hand-trace A* on a graph, listing frontier and f-values.
- What breaks if h overestimates? (may return suboptimal path)
- Why A* is memory bound.
