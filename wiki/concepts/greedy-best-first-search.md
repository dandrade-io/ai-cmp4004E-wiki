---
title: Greedy Best-First Search
type: concept
tags: [search, informed]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Greedy Best-First Search

**Slide 12.** Always expands the node that *appears* closest to the goal according to h(n). Priority queue ordered by h(n). It is **greedy**: locally optimal decisions, ignoring accumulated cost g(n).

## Properties (slide 12)
- Complete only when repeated states are controlled.
- Not optimal; can be trapped in suboptimal paths when h misleads.
- AIMA (p. 103): greedy graph search is complete in *finite* state spaces but not in infinite ones; worst-case time and space O(|V|); tree-like O(b^m); a good heuristic can reduce this to about O(bm) on some problems.

## Worked example (AIMA Fig. 3.16–3.17, p. 103)
Romania with h_SLD to Bucharest (Arad 366, Sibiu 253, Fagaras 176, Rimnicu Vilcea 193, Zerind 374, Timisoara 329, Pitesti 100, …): from Arad expand Sibiu (253 < 329, 374), then Fagaras (176), which generates Bucharest — no off-path node is expanded, but the path Arad–Sibiu–Fagaras–Bucharest is **32 miles longer** than the optimal one via Rimnicu Vilcea and Pitesti ("greediness can lead to worse results than being careful"). f(n) = h(n).

## Pros / cons
+ Fast, often finds a solution quickly. − Not optimal; can wander (dead ends, local traps).

## Related
[[a-star-search]] (adds g), [[informed-search-and-heuristics]], [[repeated-states-and-explored-set]]; conceptual analogue of hill climbing in [[optimization-landscape]] (unverified).

## Exam angles
- Trace with f = h and show a suboptimal result vs A*.
- Explain "greedy".
