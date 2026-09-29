---
title: Minimax
type: concept
tags: [search, games]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Minimax

**Slide 18.** MAX maximizes the value of the final state, MIN minimizes it; both assumed optimal. Explores the full tree to terminal nodes.

## Definition
MINIMAX(s) =
- UTILITY(s) if s is terminal
- max over successors of MINIMAX(child) if MAX to move
- min over successors of MINIMAX(child) if MIN to move

## Pseudocode (AIMA Fig. 6.3, §6.2.1)
```
MINIMAX-SEARCH(game,state): (value,move) ← MAX-VALUE(game,state); return move
MAX-VALUE: if terminal return UTILITY; v ← -∞
   for a in ACTIONS: v2 ← MIN-VALUE(RESULT(s,a)); if v2>v: v,move ← v2,a
   return v,move
MIN-VALUE: symmetric with +∞ and <
```
Worked example (Fig. 6.2, two-ply tree): MIN nodes B, C, D get 3, 2, 2 → root MAX value 3, best move a₁.

## Properties (slide 18)
Time O(b^m); space O(b·m) if all actions are generated at once, **O(m)** if generated one at a time (AIMA p. ~196). Complete for finite trees; optimal against an optimal opponent — against a suboptimal opponent MAX does at least as well, but the minimax move is not necessarily best (a risky move can beat a weak opponent).

## Cons
Infeasible for real games (chess: b ≈ 35, ≈ 80 ply per game → 35⁸⁰ ≈ 10¹²³ states, AIMA p. ~196; note the slides don't give m) without pruning/evaluation functions → [[alpha-beta-pruning]].

## Related
[[adversarial-search]], [[depth-first-search]], [[search-algorithms-comparison]]

## Exam angles
- Compute minimax values on a given tree (bottom-up).
- Why space is linear while time is exponential.

## Source
AIMA §6.2: [[aima-ch06-adversarial-search-and-games]]. Extensions: [[expectiminimax-and-stochastic-games]], multiplayer value vectors ([[adversarial-search]]).
