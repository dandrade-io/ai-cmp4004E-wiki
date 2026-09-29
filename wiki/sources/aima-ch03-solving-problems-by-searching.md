---
title: "AIMA Ch. 3 — Solving Problems by Searching"
type: source
tags: [search, heuristics, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 3 — Solving Problems by Searching (pp. 81–127)

Book: [[russell-norvig]]. Course slides: [[slides-02-problem-solving]].

## Summary
Problem-solving agents in fully observable, deterministic, known environments: formulate a goal and problem, search for a sequence of actions, execute it. The chapter builds all algorithms on one template, **best-first search** with an evaluation function f(n).

## 3.1 Problem-solving agents (pp. 81–84)
Four phases: **goal formulation → problem formulation → search → execution** (p. 81–82). In fully observable, deterministic, known environments the solution is a fixed sequence, executed *open-loop*; otherwise closed-loop/contingency plans (p. 82). A search problem = states, initial state, goal states (IS-GOAL), ACTIONS(s), transition model RESULT(s,a), action-cost c(s,a,s′); path cost is additive, costs assumed positive (p. 83). **Abstraction** = removing detail; a good formulation is *valid* and *useful* (p. 84). → [[problem-solving-agents]], [[problem-formulation]], [[state-space]].

## 3.2 Example problems (pp. 84–89)
Standardized: grid worlds, vacuum world, 8-puzzle, sliding-tile puzzles, Knuth's "4" problem; real-world: route finding, touring, VLSI layout, robot navigation, assembly.

## 3.3 Search algorithms (pp. 89–94)
- Search tree over the state-space graph; **expand**, **frontier**, **reached** (pp. 89–90; frontier separates expanded interior from unreached exterior, Fig. 3.6).
- **BEST-FIRST-SEARCH** (Fig. 3.7, p. 91): priority queue on f; `reached` table; re-add a node if reached by a cheaper path.
- Node = (STATE, PARENT, ACTION, PATH-COST); queue types: priority (best-first), FIFO (BFS), LIFO (DFS) (pp. 91–92).
- **Redundant paths / cycles**: three remedies — remember all reached states (graph search), ignore (tree-like search), or check only for cycles (pp. 92–93) → [[repeated-states-and-explored-set]].
- Performance: **completeness, cost optimality, time, space**; in implicit spaces measured with b, d, m (pp. 93–94).

## 3.4 Uninformed strategies (pp. 94–102)
[[breadth-first-search]] (FIFO, early goal test, O(b^d); depth 10 with b=10 ≈ 10 TB, 14 → 3.5 years, p. 95); [[uniform-cost-search]] (Dijkstra; O(b^(1+⌊C*/ε⌋)), late goal test essential, p. 96); [[depth-first-search]] (tree-like, O(bm) memory; incomplete on infinite or cyclic spaces, p. 97–98; backtracking variant); depth-limited & [[iterative-deepening-search]] (p. 98–99); [[bidirectional-search]] (b^(d/2) + b^(d/2), p. 100). Comparison table **Fig. 3.15** (p. 102) — see [[search-algorithms-comparison]].

## 3.5 Informed strategies (pp. 102–115)
h(n) = estimated cost to goal. [[greedy-best-first-search]] (f=h; Romania example finds a path 32 miles longer than optimal, p. 103); [[a-star-search]] (f=g+h; Fig. 3.18; **admissible** = never overestimates; **consistent** = h(n) ≤ c(n,a,n′)+h(n′); optimality proof by contradiction, p. 106; consistent ⇒ admissible; A* is *optimally efficient*, p. 108); search contours (p. 107); **weighted A\*** f = g + W·h (W=0 UCS, 1 A*, ∞ greedy; p. 109); memory-bounded search (IDA*, RBFS, SMA*); bidirectional heuristic search. → [[admissible-and-consistent-heuristics]], [[informed-search-and-heuristics]].

## 3.6 Heuristic functions (pp. 115–123)
8-puzzle: h1 = misplaced tiles, h2 = Manhattan distance (start state: h1 = 8, h2 = 18, true cost 26, p. 116). **Effective branching factor** b*; Fig. 3.26 (p. 117): at d = 24, BFS generates 290,082 nodes, A*(h1) 53,039, A*(h2) 5,733. **Dominance**: h2 ≥ h1 ⇒ A* with h2 expands no more nodes. Heuristics from **relaxed problems** (optimal relaxed cost is admissible *and* consistent, p. 118), max of several heuristics, **pattern databases**, landmarks, learning heuristics.

## Slide vs. book discrepancies
> ⚠️ Contradiction: [[slides-02-problem-solving]] (slide 14) says A* is complete "if h is admissible". In AIMA, **A\* is complete regardless** (assuming finite branching factor and action costs ≥ ε > 0); admissibility/consistency is needed for *cost-optimality* (p. 104 and footnote 11).

> ⚠️ Contradiction (precision): slide 7 says BFS is "complete: always" and slide 12 says greedy needs repeated-state control. AIMA: BFS is complete if b is finite (Fig. 3.15); greedy graph search is complete in *finite* state spaces but not infinite ones (p. 103).

> ⚠️ Contradiction (terminology): slides call the data structures *frontier* and *explored set*; AIMA 4th ed. uses *frontier* and *reached* (reached = expanded ∪ frontier), noting the older "open/closed list" terms (footnote p. 90). Also the slides' "transition model Result(s,a) → s′" matches AIMA; the slide's *Goal test* is AIMA's IS-GOAL.

> ⚠️ Contradiction (complexity of greedy): slide 12 gives no complexity; the wiki earlier assumed O(b^m). AIMA: greedy graph search worst case O(|V|), tree-like O(b^m); a good heuristic reduces it substantially (p. 103).

## Pages updated / created
[[problem-solving-agents]], [[problem-formulation]], [[state-space]], [[repeated-states-and-explored-set]], [[uninformed-search]], [[breadth-first-search]], [[depth-first-search]], [[informed-search-and-heuristics]], [[greedy-best-first-search]], [[a-star-search]]; new: [[uniform-cost-search]], [[iterative-deepening-search]], [[bidirectional-search]], [[admissible-and-consistent-heuristics]].
