---
title: Monte Carlo Tree Search (MCTS)
type: concept
tags: [games, search, reinforcement-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Monte Carlo Tree Search

Not in the slides. Source: AIMA §6.4 (pp. ~207–210), [[aima-ch06-adversarial-search-and-games]].

## Motivation
Heuristic [[alpha-beta-pruning]] fails for Go: branching factor starts at 361 (only 4–5 ply) and no good evaluation function exists. MCTS needs **no EVAL**: a state's value is the average utility of many **playouts** (rollouts) to the end of the game, using a **playout policy**.

## The four steps (Fig. 6.10)
1. **Selection** – descend the tree using a *selection policy* balancing [[exploration-vs-exploitation]].
2. **Expansion** – add a new child.
3. **Simulation** – playout to a terminal state with the playout policy.
4. **Back-propagation** – update win/visit counts up to the root (winner's nodes +1 win +1 playout; loser's nodes +1 playout).

## UCB1 / UCT
UCB1(n) = U(n)/N(n) + C · √( ln N(PARENT(n)) / N(n) ), with U = total utility through n, N = playouts through n (p. ~209). Example: with C = 1.4 the 60/79 node wins; with C = 1.5 the under-explored 2/11 node is chosen. Return the move with the **most playouts**, not highest mean.

## Pros / cons
+ Works on new games given only the rules; playout cost is linear in depth; policies can be learned by self-play (AlphaZero).
− May miss a single decisive move (Type B pruning); slow to verify "obvious" wins/losses.
Pure Monte Carlo search (N playouts from root, no tree) is the simplest variant.

Related: [[adversarial-search]], [[minimax]]. Exam angle: describe the four phases and what UCB1's two terms mean.
