---
title: Wumpus World
type: concept
tags: [logic, agents, example]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Wumpus World

Running example of AIMA Ch. 7 and 8 (§7.2, pp. 228–232), [[aima-ch07-logical-agents]]. Not in slides.

- 4×4 cave; the agent starts in [1,1]; hidden wumpus, pits, gold. PEAS description ([[peas]]): percepts Stench, Breeze, Glitter, Bump, Scream; actions Forward/Turn/Grab/Shoot/Climb.
- Partially observable, deterministic, sequential, static, discrete, single-agent ([[task-environment-properties]]).
- A cautious agent moves only to squares *known* to be OK. Breeze at [2,1] ⇒ pit in [2,2] or [3,1]; the agent must combine percepts by logical inference.
- About 21 % of environments are unfair (gold in a pit or surrounded by pits).
- Propositional KB: B₁,₁ ⇔ (P₁,₂ ∨ P₂,₁); with 7 relevant symbols there are 2⁷ = 128 models and KB is true in 3, so ¬P₁,₂ is entailed but P₂,₂ is undetermined ([[model-checking-and-entailment]]).
- Resolution example: KB ∧ ¬α with α = ¬P₁,₂ → empty clause ([[cnf-and-resolution]]).
- Needs **frame axioms** to say what stays unchanged (the frame problem, §7.7).

Exam angle: derive safe squares from a given percept sequence.
