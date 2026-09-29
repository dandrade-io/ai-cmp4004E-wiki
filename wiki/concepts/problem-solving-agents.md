---
title: Problem-Solving Agents
type: concept
tags: [search, agents]
sources: [raw/slides/02_Problem Solving.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Problem-Solving Agents

**Intuition.** A goal-based agent that plans a whole sequence of actions before acting.

**Slide 2.** Operates in *search and execution* mode:
1. Formulate the problem ([[problem-formulation]])
2. Search for an action sequence reaching the goal ([[uninformed-search]], [[informed-search-and-heuristics]])
3. Execute the plan

Assumes an **observable, deterministic, discrete, static** environment ([[task-environment-properties]]), so the plan can be executed open-loop ("eyes closed"). The solution is always a *sequence* of actions.

## AIMA grounding ([[aima-ch03-solving-problems-by-searching]], §3.1, pp. 81–84)
AIMA's cycle has **four** phases (the slides merge the first two into "formulate the problem"):
1. **Goal formulation** — adopt a goal (e.g. reach Bucharest); goals organize behavior by limiting the actions considered.
2. **Problem formulation** — an abstract model of states and actions ([[problem-formulation]]).
3. **Search** — simulate action sequences in the model until one reaches the goal (a *solution*), or fail.
4. **Execution** — carry out the actions one at a time.

In a fully observable, deterministic, *known* environment the solution is a fixed sequence, so the agent can ignore percepts while executing — an **open-loop** system (control theory term). If the model may be wrong or the environment is nondeterministic, use **closed-loop** execution (monitor percepts) or a branching contingency plan (Ch. 4: AND–OR search, [[aima-ch04-search-in-complex-environments]]). The running example is a touring agent in Arad, Romania, with a nonrefundable flight from Bucharest (Fig. 3.1).

Note: AIMA's problem-solving agent assumes a *known* environment too; in an unknown environment it can only act randomly or use online search (Ch. 4).

## Limits
Breaks if the environment is partially observable, stochastic or dynamic (needs contingency plans, replanning) — see [[agent-types]] (goal-based).

## Related
[[state-space]], [[rational-agents]]

## Exam angles
- Three phases; why the assumptions are needed.
- Difference between the agent's *goal* and the *problem formulation*.
