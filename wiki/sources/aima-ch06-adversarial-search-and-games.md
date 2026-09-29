---
title: "AIMA Ch. 6 — Adversarial Search and Games"
type: source
tags: [games, search, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 6 — Adversarial Search and Games (pp. ~192–216)

Book: [[russell-norvig]]. Course slides: [[slides-02-problem-solving]] (slides 17–20).

## Summary
Three stances on multi-agent environments: economy, adversaries as part of a nondeterministic environment, or explicit **game-tree search** (chosen here). Focus: deterministic, two-player, turn-taking, perfect-information, zero-sum games (§6.1).

## 6.1–6.2 Games and optimal decisions (pp. ~192–198)
- Game = S₀, TO-MOVE, ACTIONS, RESULT, IS-TERMINAL, UTILITY (p. ~193). Tic-tac-toe < 9! = 362,880 terminal nodes (5,478 distinct states); chess > 10⁴⁰ nodes.
- **MINIMAX** (Fig. 6.3): time O(bᵐ); space O(bm) (all actions at once) or **O(m)** (one at a time). Chess: b ≈ 35, ≈ 80 ply → 35⁸⁰ ≈ 10¹²³ states (p. ~196). → [[minimax]].
- Multiplayer: value **vectors**; alliances can emerge from selfish play (p. ~196–197).
- **Alpha–beta** (Fig. 6.7, p. ~198): α = best (highest) choice found so far for MAX along the path, β = best (lowest) for MIN; MAX-VALUE returns when v ≥ β, MIN-VALUE when v ≤ α. Perfect ordering O(b^(m/2)); random ordering ≈ O(b^(3m/4)); killer-move heuristic, iterative deepening for ordering, transposition tables (≈ double the depth in chess). → [[alpha-beta-pruning]].

## 6.3 Heuristic alpha–beta tree search (pp. ~202–206)
Shannon's Type A (wide/shallow) vs Type B (deep/narrow) strategies. Replace UTILITY by **EVAL** and terminal test by a **cutoff test**; EVAL must equal UTILITY on terminals and correlate with winning chances; weighted linear function Σ wᵢfᵢ (pawn 1, knight/bishop 3, rook 5, queen 9); forward pruning; search vs lookup (endgame tables). Go: b starts at 361 and no good EVAL → alpha–beta only 4–5 ply.

## 6.4 Monte Carlo tree search (pp. ~207–210)
Value = average utility of playouts; four steps **selection, expansion, simulation, back-propagation**; UCB1 selection; return the most-played move. → [[monte-carlo-tree-search]].

## 6.5–6.7 Stochastic and partially observable games (pp. ~210–218)
Chance nodes, **expectiminimax**, evaluation functions must behave like a positive linear transformation of win probability or expected utility (order alone is no longer enough); partially observable games (Kriegspiel, card games); limitations of game search. → [[expectiminimax-and-stochastic-games]].

## Derived / updated pages
[[adversarial-search]], [[minimax]], [[alpha-beta-pruning]], [[monte-carlo-tree-search]], [[expectiminimax-and-stochastic-games]].

## Slide vs. book
- Slide 20's pruning rule ("MIN value falls below α → prune; MAX value rises above β → prune") **agrees** with Fig. 6.7 except that the book also prunes on *equality* (v ≥ β, v ≤ α). See [[alpha-beta-pruning]].
- Slides never mention evaluation-function cutoffs, MCTS or chance nodes; these are exam-relevant extensions.
