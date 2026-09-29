---
title: First-Order Inference
type: concept
tags: [logic, inference]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf, raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# First-Order Inference

AIMA Ch. 9 ([[aima-ch09-inference-in-first-order-logic]]). Bridges the propositional material to [[prolog]].

## Approaches
1. **Propositionalization**: apply Universal Instantiation (substitute ground terms) / Existential Instantiation (new Skolem constant) and use propositional methods. Herbrand: works but ground terms can be infinite (function symbols).
2. **Lifted inference**: **Generalized Modus Ponens** + [[unification]] (find the MGU) — apply rules directly with variables.
3. **Forward chaining** on first-order definite clauses: data-driven, sound and complete for definite clauses; terminates on **Datalog** (no function symbols); rule matching is NP-hard in general (a CSP, [[constraint-satisfaction-problems]]).
4. **Backward chaining** (FOL-BC-ASK): goal-driven depth-first AND/OR search — the Prolog engine ([[sld-resolution-and-backtracking]]).
5. **Resolution**: works for arbitrary CNF; **refutation-complete**; needs Skolemization ([[cnf-and-resolution]]).

## Decidability
Entailment in FOL (and even in definite clauses with function symbols) is **semidecidable**; for Datalog it is decidable (p. 305, 322).

## Running example
Criminal(West): American(x) ∧ Weapon(y) ∧ Sells(x,y,z) ∧ Hostile(z) ⇒ Criminal(x), with Owns(Nono,M1), Missile(M1), etc. — the Prolog rules on slide 7 encode exactly this.

Exam angles: state the differences among the 3 inference families; why Prolog is incomplete; when forward chaining is preferable (repeated subgoals, e.g. path problems).
