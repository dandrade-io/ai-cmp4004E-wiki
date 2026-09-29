---
title: "AIMA Ch. 7 — Logical Agents"
type: source
tags: [logic, inference, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 7 — Logical Agents (pp. ~226–270)

Book: [[russell-norvig]]. Course slides: [[slides-xx-logic-programming-prolog]] (slides 2–6 rely on §7.5). Slide 31 points to "Chapter 7.5 for Horn clauses and chaining" — confirmed: §7.5.3–7.5.4 (pp. 247–250).

## Summary
Knowledge-based agents TELL/ASK a knowledge base (KB) of sentences and infer by logic. Uses the **wumpus world** as a running example.

## 7.1–7.2 Knowledge-based agents, wumpus world (pp. 227–232)
→ [[wumpus-world]].

## 7.3 Logic (p. 232)
Syntax vs **semantics**; a *model* is a possible world; **entailment** α ⊨ β iff M(α) ⊆ M(β) (in every model where α holds, β holds). Soundness, completeness. → [[model-checking-and-entailment]].

## 7.4 Propositional logic (pp. 235–240)
Syntax (symbols, ¬ ∧ ∨ ⇒ ⇔), truth-table semantics, wumpus KB, **TT-ENTAILS?** enumeration (2ⁿ models; 7 symbols → 128 models, KB true in 3, p. 238).

## 7.5 Propositional theorem proving (pp. 240–250)
- Inference rules Modus Ponens, And-Elimination; **monotonicity** (p. 242); proof = search.
- **Resolution**: unit resolution → full resolution; factoring; CNF conversion; PL-RESOLUTION (Fig. 7.13): prove KB ⊨ α by showing KB ∧ ¬α unsatisfiable; stops at the **empty clause** or when no new clauses arise; **ground resolution theorem** = completeness (pp. 243–247). → [[cnf-and-resolution]].
- **Horn / definite clauses** (p. 247): definite = exactly one positive literal; Horn = at most one; goal clause = none; Horn clauses **closed under resolution**; entailment **linear-time**. → [[horn-clauses]].
- **Forward chaining** (PL-FC-ENTAILS?, Fig. 7.15, data-driven, sound and complete, linear) and **backward chaining** (goal-directed, often sub-linear) over the AND–OR graph, Fig. 7.16 (pp. 248–250). → [[forward-and-backward-chaining]].

## 7.6 Effective model checking (pp. 250–255)
**DPLL** (early termination, pure-symbol heuristic, unit-clause heuristic; on definite clauses it replicates forward chaining), component analysis, variable/value ordering, clause learning, restarts; **WalkSAT** local search; random 3-SAT phase transition at clause/symbol ≈ 4.3. → [[model-checking-and-entailment]].

## 7.7 Agents based on propositional logic (pp. 255–270)
Fluents, state-transition axioms, frame problem, hybrid agent, logical state estimation, planning by propositional inference (§7.7.4); limitation: propositional logic cannot express "every" concisely → motivates [[propositional-vs-first-order-logic]].

## Slide vs. book
- Slide 4's three benefits of Horn clauses match the book's three reasons (p. 247) exactly.
- Slide 3's "resolution is refutation-complete" is correct; the book calls the result the ground resolution theorem (p. 246–247).
