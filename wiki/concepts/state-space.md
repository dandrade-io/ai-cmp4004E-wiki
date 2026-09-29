---
title: State Space
type: concept
tags: [search]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# State Space

**Slide 4.** The set of all states reachable from the initial state via any sequence of actions. Represented as a graph: **nodes** = world states, **edges** = actions, each edge with a cost. It is **not built explicitly** (too large); the agent explores it progressively during search.

## Graph vs. tree
The state graph represents the problem (each state once); the search tree represents the search process (a state may appear several times) — see [[repeated-states-and-explored-set]].

## AIMA grounding ([[aima-ch03-solving-problems-by-searching]], §3.3, pp. 89–94)
- **State space vs. search tree**: the state space describes the (possibly infinite) set of world states and actions; the *search tree* describes paths between them. A state may appear in many tree nodes but each node has a unique path to the root. Even Romania's 20-state graph gives an **infinite** search tree because of cycles.
- **Frontier / reached / interior / exterior:** the frontier (generated but not expanded) *separates* the expanded interior from the unreached exterior (separation property, Fig. 3.6).
- **Measuring size:** for an *explicit* graph use |V| + |E|; for an *implicit* graph (initial state + ACTIONS + RESULT) use **b** (branching factor), **d** (depth of the shallowest/optimal solution) and **m** (maximum path length).

## Size
Typically exponential in problem size: 8-puzzle 9!/2 = 181,440 reachable states, 15-puzzle 16!/2 > 10 trillion (AIMA p. 115). Branching factor b, solution depth d, max depth m govern complexity ([[uninformed-search]]).

## Related
[[problem-formulation]], [[breadth-first-search]], [[a-star-search]]

## Exam angles
- Distinguish state space, state graph, search tree.
- Why implicit generation matters for memory.
