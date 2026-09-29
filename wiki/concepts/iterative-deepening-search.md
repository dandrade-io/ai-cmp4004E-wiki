---
title: Depth-Limited and Iterative Deepening Search
type: concept
tags: [search, uninformed]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Depth-Limited & Iterative Deepening Search (IDS)

Not in the slides (they only hint at "depth-limited"/ID as fixes); content from AIMA §3.4.4, pp. 98–99 ([[aima-ch03-solving-problems-by-searching]]).

## Depth-limited search
[[depth-first-search]] with a limit ℓ: nodes at depth ℓ are treated as having no successors. Returns *cutoff* (limit reached) vs. *failure* (no solution). Time O(b^ℓ), space O(bℓ); incomplete if ℓ < d. A good ℓ can come from the **diameter** of the state graph (Romania: 20 cities, ℓ = 19 valid, but diameter 9 is better).

## Iterative deepening
Run depth-limited search for ℓ = 0, 1, 2, … until the result is not *cutoff*.
```
function ITERATIVE-DEEPENING-SEARCH(problem):
  for depth = 0 to ∞:
    result ← DEPTH-LIMITED-SEARCH(problem, depth)
    if result ≠ cutoff: return result
```
- Memory O(bd) (like DFS); optimal for equal step costs and complete on finite acyclic spaces or with full cycle checking (like BFS).
- Time O(b^d): re-generating shallow levels is cheap because most nodes are at the deepest level (unverified numeric argument, standard).
- Preferred uninformed method when the space is large and the solution depth unknown (AIMA states the combined benefits; the "preferred" claim is standard background, unverified).

## Related
[[uninformed-search]], [[breadth-first-search]], [[search-algorithms-comparison]]

## Exam angles
- Why is repeating work in IDS acceptable? Space/time trade vs. BFS.
- Depth-limited: difference between cutoff and failure.
