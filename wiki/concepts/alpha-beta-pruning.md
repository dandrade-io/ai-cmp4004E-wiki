---
title: Alpha–Beta Pruning
type: concept
tags: [search, games]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Alpha–Beta Pruning

**Slide 20.** Eliminates branches that cannot influence the final decision; returns the **same result as [[minimax]]** while exploring far fewer nodes. Best-case complexity **O(b^(m/2))** (effectively doubles searchable depth).

- **α**: best value found so far for MAX (lower bound)
- **β**: best value found so far for MIN (upper bound)

## Slide rule
- MIN node value falls below α → prune (MAX would never choose it)
- MAX node value rises above β → prune (MIN would never choose it)

> ✅ Checked against AIMA Fig. 6.7 (§6.2.3, p. ~198): the slide rule is **correct**. The book states it on the returned value v: MAX-VALUE returns when **v ≥ β**, MIN-VALUE returns when **v ≤ α** (so ties also prune; the slide's "below/above" reads strict). The earlier note "prune when α ≥ β" is an equivalent way of saying the same thing (the window is empty) — it is not a different rule. α = value of the best (highest) choice found so far for MAX along the path; β = best (lowest) for MIN. α is updated only in MAX nodes and β only in MIN nodes.

## Pseudocode (AIMA Fig. 6.7)
```
MAX-VALUE(s,α,β): if terminal return UTILITY; v ← -∞
  for a in ACTIONS(s):
     v2 ← MIN-VALUE(RESULT(s,a),α,β)
     if v2 > v: v,move ← v2,a; α ← MAX(α,v)
     if v ≥ β: return v,move
  return v,move
MIN-VALUE(s,α,β): v ← +∞; ... if v2<v: β ← MIN(β,v); if v ≤ α: return v,move
```
Worked example (Fig. 6.5): root = max(min(3,12,8), min(2,x,y), min(14,5,2)) = 3, independent of x and y, so two leaves are pruned.

## Notes
Pruning effectiveness depends on **move ordering** (AIMA §6.2.4): with perfect ordering O(b^(m/2)) (effective branching factor √b: ≈ 6 instead of 35 in chess, i.e. roughly twice the depth); random ordering ≈ O(b^(3m/4)); worst case O(b^m). Ordering tricks: captures/threats first, **iterative deepening** to rank moves, **killer moves**. **Transposition tables** cache values of repeated positions (≈ doubles reachable depth in chess). Alpha–beta with a depth cutoff + EVAL = heuristic alpha–beta ([[adversarial-search]]).

## Related
[[adversarial-search]], [[search-algorithms-comparison]]

## Exam angles
- Trace α/β values on a tree and mark pruned branches.
- Does pruning change the minimax value? No.

## Source
AIMA §6.2.3–6.2.4: [[aima-ch06-adversarial-search-and-games]].
