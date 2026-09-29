---
title: Problem Formulation
type: concept
tags: [search]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Problem Formulation

**Slide 3.** A search problem is defined by five components, which together define the [[state-space]]:
| Component | Meaning |
|---|---|
| Initial state | State the agent starts in |
| Actions | Actions available in each state, ACTIONS(s) |
| Transition model | RESULT(s, a) → s' |
| Goal test | Condition deciding if a state is a goal |
| Cost function | Numeric cost of each action; defines solution quality (path cost = sum of step costs) |

## AIMA formal definition (§3.1.1, p. 83; [[aima-ch03-solving-problems-by-searching]])
A search problem = set of **states** (the state space); **initial state**; one or more **goal states** (specified via an `IS-GOAL` method, so a goal can be a single state, a small set, or a property such as "no dirt anywhere"); `ACTIONS(s)` (a finite set of applicable actions); **transition model** `RESULT(s,a)`; **action cost** `c(s,a,s′)`. A *path* is a sequence of actions, a *solution* is a path from initial to goal state, costs are additive, an *optimal solution* has lowest path cost; costs are assumed positive (negative cycles make optimal cost undefined; zero-cost actions are OK if bounded; require costs ≥ ε > 0 to avoid Zeno-type problems, p. 83 footnote 3). The state space is a graph whose vertices are states and directed edges are actions.

## Worked examples
- **Romania route-finding** (Fig. 3.1): states = cities; ACTIONS(Arad) = {ToSibiu, ToTimisoara, ToZerind}; RESULT(Arad, ToZerind) = Zerind; cost = road miles; goal = Bucharest.
- **8-puzzle**: state = tile configuration; actions = move blank; cost = 1 per move; 9!/2 = 181,440 reachable states; shortest solution of the AIMA example is 26 moves (p. 116).
- Standardized vs. real-world problems: grid worlds, vacuum world, sliding-tile puzzles, Knuth's 4 problem; route finding, touring, VLSI layout, robot navigation, assembly (§3.2).

## Abstraction (§3.1.2, p. 84)
Abstraction = removing detail from a representation. A good formulation has the right level of detail: **valid** (every abstract solution can be elaborated into a detailed one) and **useful** (executing each abstract action is easier than the original problem). Without useful abstraction agents would be swamped by the real world.

## Slide vs. book
> ⚠️ Contradiction (naming): the slides list "Goal test" and "Cost function"; AIMA names them IS-GOAL and action-cost function c(s,a,s′), and also includes the *state space* as part of the definition rather than as its output (slide 3: the five components "define the state space").

## Related
[[problem-solving-agents]], [[state-representation]], [[constraint-satisfaction-problems]] (factored alternative)

## Exam angles
- Given a puzzle, write all five components.
- Solution vs. optimal solution: the cost function defines the latter.
