---
title: Arc Consistency and AC-3
type: concept
tags: [csp, inference, propagation]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Arc Consistency and AC-3

Slide 24 names "constraint propagation: forward checking, arc consistency" ([[slides-02-problem-solving]]); AIMA §5.2 (pp. 169–175) gives the details ([[aima-ch05-constraint-satisfaction]]).

## Local consistency levels
- **Node consistency** (1-consistency): every value satisfies the variable's unary constraints (p. 170).
- **Arc consistency** (2-consistency): X_i is arc-consistent w.r.t. X_j if every value in D_i has some supporting value in D_j (p. 170). Example Y = X² over digits: D_X → {0,1,2,3}, D_Y → {0,1,4,9}. It does *nothing* for map colouring with ≠ constraints.
- **Path consistency** (3-consistency for binary graphs): pairs vs. a third variable; detects that Australia is not 2-colourable, which AC cannot (p. 171–172).
- **k-consistency**; strongly n-consistent CSPs need no backtracking (O(n²d)) but establishing it is exponential (p. 172).

## AC-3 (Fig. 5.3, p. 171)
```
queue ← all arcs
while queue: (Xi,Xj) ← pop
  if REVISE(Xi,Xj):            # delete x∈Di with no support in Dj
      if Di empty: return false
      for Xk in neighbors(Xi)−{Xj}: push (Xk,Xi)
return true
```
Worst case **O(c·d³)** (c arcs, domain size d; each arc re-enters ≤ d times, each check O(d²)). Result is an equivalent CSP with smaller domains; may solve it (all domains size 1) or refute it (empty domain).

## Global constraints
**Alldiff**: if m variables share n < m values → inconsistent; remove singleton values iteratively. **Atmost** (resource) and **bounds propagation** (e.g. F1+F2=420 with D1=[0,165], D2=[0,385] → D1=[35,165], D2=[255,385]).

## Role in search
Run as preprocessing, or after each assignment: **forward checking** = arc consistency from the assigned variable only; **MAC** (maintaining arc consistency) = AC-3 seeded with arcs into the assigned variable — strictly stronger ([[backtracking-search-csp]]).

## Exam angles
- Run AC-3 on a small CSP and show domain reductions.
- Give a CSP that is arc-consistent yet unsolvable (2-colour triangle).
- Why does AC-3 re-add arcs (X_k, X_i) after revising D_i?

Related: [[constraint-satisfaction-problems]].
