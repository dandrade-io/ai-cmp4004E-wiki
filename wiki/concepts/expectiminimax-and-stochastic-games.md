---
title: Expectiminimax and Stochastic Games
type: concept
tags: [games, search, uncertainty]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Expectiminimax and Stochastic Games

Not in the slides; AIMA §6.5–6.6 (pp. ~210–218), [[aima-ch06-adversarial-search-and-games]].

## Chance nodes
Games with dice (backgammon) add **chance nodes** to the tree. Positions have no definite minimax value, only an **expected** one. Backgammon: 36 rolls, 21 distinct (6 doubles at 1/36, 15 others at 1/18).

EXPECTIMINIMAX(s) =
- UTILITY(s) if terminal
- max_a EXPECTIMINIMAX(RESULT(s,a)) if MAX
- min_a … if MIN
- Σ_r P(r) · EXPECTIMINIMAX(RESULT(s,r)) if CHANCE

## Evaluation functions
With chance nodes the *scale* of EVAL matters: it must be a **positive linear transformation** of win probability / expected utility, not merely order-preserving as in [[minimax]] (p. ~211).

## Partially observable games
Kriegspiel (partially observable chess) and card games (Bridge, poker): play with uncertainty about the state; cf. partial observability in [[task-environment-properties]].

Related: [[adversarial-search]], [[monte-carlo-tree-search]]. Exam angle: compute an expectiminimax value on a small tree.
