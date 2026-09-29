---
title: Repeated States and the Explored Set
type: concept
tags: [search, graph-search]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Repeated States & the Explored Set

**Slide 5.** Expanding the search tree can generate the same state via multiple paths, producing infinite cycles if uncontrolled. Solution: keep two structures:
- **Frontier** — generated but not yet expanded states
- **Explored set** — states already expanded, never generated again

Without control the algorithm may not terminate even when a solution exists; with control each state is expanded at most once. This is *graph search* (vs. *tree search*).

## AIMA grounding (§3.3.3, pp. 92–93; [[aima-ch03-solving-problems-by-searching]])
Terminology: AIMA 4th ed. says **frontier** and **reached** (reached = frontier ∪ expanded), not "open/closed list" (p. 90 footnote). A **repeated state** arises from a **cycle** (loopy path); a cycle is a special case of a **redundant path** (e.g. Arad–Sibiu 140 vs. Arad–Zerind–Oradea–Sibiu 297). Redundancy is severe: in a 10×10 grid with 8 moves, >100 million paths of length 9 reach only 100 squares — "algorithms that cannot remember the past are doomed to repeat it".
Three approaches:
1. **Remember all reached states** (graph search; keeps only the best path to each state; best-first search does this; preferred when the table fits in memory).
2. **Ignore** redundancy (*tree-like search*) — OK when paths rarely coincide (e.g. assembly problems with an ordering of parts); less memory but slower otherwise.
3. **Check for cycles only** by following parent pointers (all the way, or only a few links) — no extra memory.

```
BEST-FIRST-SEARCH(problem, f):            # AIMA Fig. 3.7
  frontier ← priority queue on f; reached ← {initial: node}
  while frontier not empty:
    node ← POP(frontier); if IS-GOAL(node.STATE) return node
    for child in EXPAND(problem, node):
      s ← child.STATE
      if s ∉ reached or child.PATH-COST < reached[s].PATH-COST:
        reached[s] ← child; add child to frontier
  return failure
```

## Caveats
- A cheaper path to an already-reached state *replaces* the old entry (needed for UCS and A*); with a **consistent** heuristic the first path to a state is already optimal, so this never happens ([[admissible-and-consistent-heuristics]]).
- Costs memory: `reached` is O(#states). DFS is normally run **tree-like** (no reached table) precisely to keep O(bm) memory; with a table it loses that advantage but becomes complete on finite spaces ([[depth-first-search]]).
- BFS may use an *early goal test* (test on generation) and a `reached` **set**; UCS/A* must use a *late* goal test.

## Related
[[state-space]], [[uninformed-search]]

## Exam angles
- Why DFS/greedy are complete "only when repeated states are controlled".
- Difference between frontier and explored.
