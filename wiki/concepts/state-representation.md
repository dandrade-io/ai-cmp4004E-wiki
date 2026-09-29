---
title: State Representation
type: concept
tags: [agents, representation]
sources: [raw/slides/03_Intelligent Agents.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# State Representation

**Slide 18.** Three levels of expressiveness:
- **Atomic** — each state is an indivisible black box (used by [[uninformed-search]], [[breadth-first-search]], plain search)
- **Factored** — a set of variables/attributes with values (used by [[constraint-satisfaction-problems]], propositional logic, Bayesian networks (unverified))
- **Structured** — objects and relationships between them (first-order logic, [[prolog]]) — see [[propositional-vs-first-order-logic]]

**Trade-off:** greater expressiveness enables more reasoning but increases computational complexity.

## AIMA grounding (§2.4.7, pp. 76–78, Fig. 2.16; [[aima-ch02-intelligent-agents]])
- **Atomic** (black box, identical/different only): search and game-playing (Ch. 3, 4, 6), hidden Markov models (Ch. 14), MDPs (Ch. 16). Example: state = name of the city.
- **Factored** (fixed set of variables/attributes with values): CSPs (Ch. 5), propositional logic (Ch. 7), planning (Ch. 11), Bayesian networks (Ch. 12–15, 18), many ML algorithms. Two factored states can share some attribute values → easier to turn one state into another.
- **Structured** (objects with attributes and relationships): relational databases, first-order logic (Ch. 8–10), first-order probability models, much of natural language. Needed for things like "a truck backing into a driveway blocked by a loose cow" where no fixed attribute exists.
- **Expressiveness ↔ complexity:** chess rules take 1–2 pages in FOL (structured), thousands in propositional logic (factored), ~10^38 pages as an atomic finite-state automaton. Reasoning and learning get harder as expressiveness rises; real systems may need all levels simultaneously.
- Orthogonal axis: **localist** (one concept ↔ one memory location) vs. **distributed** representations (robust to noise; nearby points have similar meaning, e.g. neural nets).

## Related
[[problem-formulation]], [[agent-types]]

## Exam angles
- Classify a representation (e.g. 8-puzzle as atomic vs. factored) and defend it.
- Why richer representations cost more.
