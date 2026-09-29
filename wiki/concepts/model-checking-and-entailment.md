---
title: Entailment, Model Checking and SAT Solving
type: concept
tags: [logic, inference, sat]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Entailment, Model Checking and SAT

AIMA §7.3–7.6 (pp. 232–255), [[aima-ch07-logical-agents]].

## Definitions
- **Model** = assignment of truth values (a possible world); M(α) = set of models of α.
- **Entailment** α ⊨ β iff M(α) ⊆ M(β). A sound algorithm derives only entailed sentences; a complete one derives all of them.
- **Monotonicity**: adding to the KB never invalidates earlier conclusions (p. 242).

## Model checking
**TT-ENTAILS?** enumerates all 2ⁿ models: complete but exponential. Proof by contradiction: KB ⊨ α iff KB ∧ ¬α is **unsatisfiable**, so entailment reduces to SAT.

## DPLL (Fig. 7.17)
Backtracking over partial models of a CNF with: **early termination**, **pure-symbol** heuristic, **unit-clause** heuristic (unit propagation). On definite clauses it replicates forward chaining. Improvements: component analysis, variable/value ordering, intelligent backtracking, **clause learning**, **random restarts**.

## Local search: WalkSAT
Flip a symbol in an unsatisfied clause — either random walk or minimise unsatisfied clauses. Incomplete (cannot prove unsatisfiability). Compare [[simulated-annealing]] and min-conflicts ([[backtracking-search-csp]]).

## Random 3-SAT landscape
Hardest problems at clause/symbol ratio ≈ **4.3** (satisfiability probability drops sharply there).

## Relation to the Prolog deck
Propositional entailment is **decidable** (finite models) but co-NP-hard in general; for [[horn-clauses]] it is **linear** ([[forward-and-backward-chaining]]). Resolution alternative: [[cnf-and-resolution]].

Exam angles: enumerate models to check an entailment; explain why SAT ↔ entailment; state the DPLL heuristics.
