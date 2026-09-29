---
title: Bidirectional Search
type: concept
tags: [search]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Bidirectional Search

Not in the slides; AIMA §3.4.5, pp. 100–102 ([[aima-ch03-solving-problems-by-searching]]).

**Idea.** Search forward from the initial state and backward from the goal(s) at once, until the frontiers meet. Motivation: b^(d/2) + b^(d/2) ≪ b^d (50,000× less for b = d = 10).

## Requirements
Two frontiers and two reached tables; ability to reason backwards (predecessors); with multiple goals, load all goal nodes into the backward frontier. AIMA presents **bidirectional best-first search** (Fig. 3.14): expand the node with lowest f across both frontiers; when a state is in both `reached` tables, join the paths. With f = path cost (bidirectional uniform-cost) the first solution is optimal and no node with cost > C*/2 is expanded; with other f the best solution so far must be kept until TERMINATED proves no better exists.

## Properties (Fig. 3.15)
Complete and cost-optimal if both directions are BFS or uniform-cost; time and space O(b^(d/2)) (memory is still the main cost).

## Related
[[uninformed-search]], [[uniform-cost-search]], [[breadth-first-search]], [[search-algorithms-comparison]]

## Exam angles
- Derive the b^(d/2) saving; name the practical obstacles (predecessor function, many goals, memory).
