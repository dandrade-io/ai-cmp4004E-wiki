---
title: Adversarial Search and Games
type: concept
tags: [search, games]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Adversarial Search

**Slide 17.** Earlier: one agent searching in a cooperative/neutral environment. In games: two or more agents with **opposing objectives**. The task is no longer a path but an **optimal strategy**, assuming the opponent also plays optimally.

## Setting (slide 17)
- Two players: MAX and MIN
- Zero-sum: one's gain is the other's loss
- Perfect information (fully observable), deterministic

## Game formulation (AIMA §6.1, p. ~193)
S₀ (initial state), TO-MOVE(s), ACTIONS(s), RESULT(s,a), IS-TERMINAL(s), UTILITY(s,p). Together they define a state-space graph and a **game tree** (tic-tac-toe: < 9! = 362,880 terminal nodes, only 5,478 distinct states; chess: > 10⁴⁰ nodes, so the tree is a theoretical construct). "Move"/"position" = action/state. Chess counts as zero-sum although outcomes sum to 1 (constant-sum).

AIMA's three stances toward other agents: (1) aggregate them as an economy, (2) treat them as nondeterministic environment, (3) model them explicitly — adversarial search (p. ~192).

## Algorithms
[[minimax]] → [[alpha-beta-pruning]] → heuristic alpha–beta (below) / [[monte-carlo-tree-search]]; chance nodes → [[expectiminimax-and-stochastic-games]].

### Cutting off search (AIMA §6.3, pp. ~202–206)
Shannon's **Type A** (wide, shallow + evaluation function) vs **Type B** (deep, narrow) strategies. Replace UTILITY by **EVAL** and the terminal test by a **cutoff test** (fixed depth limit or iterative deepening). A good EVAL is fast, equals UTILITY on terminals and correlates with winning chances; typically a weighted linear function Σ wᵢfᵢ of features (chess: pawn 1, knight/bishop 3, rook 5, queen 9). Also forward pruning and endgame lookup tables. Go defeats this approach (b starts at 361, no good EVAL) → MCTS.

### Multiplayer and non-zero-sum
Use utility **vectors**; alliances can emerge from selfish play; in non-zero-sum games cooperation can be optimal (p. ~196–197).

## Related
[[task-environment-properties]] (multi-agent, competitive), [[search-algorithms-comparison]]

## Exam angles
- State the assumptions of minimax games.
- Solution is a strategy (contingency plan), not a fixed sequence.

## Source
AIMA §6.1–6.7: [[aima-ch06-adversarial-search-and-games]].
