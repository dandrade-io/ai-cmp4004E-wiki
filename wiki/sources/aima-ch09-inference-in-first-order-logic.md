---
title: "AIMA Ch. 9 — Inference in First-Order Logic"
type: source
tags: [logic, inference, prolog, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 9 — Inference in First-Order Logic (pp. ~298–335)

Book: [[russell-norvig]]. Course slides: [[slides-xx-logic-programming-prolog]] (slides 2–8, 14–15, 23). Slide 31 cites "Chapter 9.4 for backward chaining and logic programming" — confirmed (pp. 311–316).

## 9.1 Propositional vs. first-order inference (pp. 298–300)
**Universal / Existential Instantiation** and **propositionalization** (reduce to ground sentences). Herbrand's theorem: complete but can be infinite; first-order entailment is **semidecidable** (algorithms answer "yes" for every entailed sentence but none answers "no" for every non-entailed one; Turing and Church, 1936). → [[first-order-inference]].

## 9.2 Unification and lifting (pp. 300–304)
**Generalized Modus Ponens**; UNIFY returns a unifier θ with SUBST(θ,p) = SUBST(θ,q); **standardizing apart**; **most general unifier (MGU)** is unique up to renaming; **occurs check**; predicate indexing, subsumption lattice. Examples: UNIFY(Knows(John,x), Knows(y,Bill)) = {x/Bill, y/John}; UNIFY(Knows(John,x), Knows(x,Elizabeth)) fails until variables are standardized apart. → [[unification]].

## 9.3 Forward chaining (pp. 304–311)
First-order definite clauses (exactly one positive literal, implicit ∀); the crime example (American/Weapon/Sells/Hostile ⇒ Criminal); FOL-FC-ASK; **fixed point**; **Datalog** (function-free definite clauses) → entailment decidable, forward chaining terminates; pattern matching is **NP-hard** in general (link to [[constraint-satisfaction-problems]] — rule matching is a CSP); incremental forward chaining, Rete, magic sets. → [[forward-and-backward-chaining]].

## 9.4 Backward chaining (pp. 311–316)
- **FOL-BC-ASK** (Fig. 9.6): an AND/OR search implemented with generators; **depth-first**, **linear space in proof size**, suffers repeated states and incompleteness (p. 311).
- **Logic programming** (p. 312): Kowalski's Algorithm = Logic + Control; [[prolog]] facts: uppercase variables, C :- A, B; `append(X,Y,[1,2,3])` runs backwards. Prolog departures from pure logic: database semantics, built-in arithmetic (`X is 4+3`; `5 is X+Y` fails), side-effecting predicates (assert/retract), **no occurs check**, depth-first search with no infinite-recursion check.
- **Redundant inference and infinite loops** (p. 313): `path` with left recursion → infinite proof tree; Prolog is **incomplete even for Datalog**; forward chaining halts on the same program (n² facts; 62 vs 877 inferences in the layered-graph example). **Tabled logic programming** = backward chaining + dynamic programming; complete for Datalog. → [[sld-resolution-and-backtracking]].
- **Database semantics of Prolog** (p. 315): closed-world negation as failure, unique names ([[negation-as-failure]]). **Constraint logic programming (CLP)** (p. 316): variables are *constrained* rather than bound (e.g. answer 7 > Z > 1), integrates [[backtracking-search-csp]] techniques — the SWI `library(clpfd)` of slide 9.

## 9.5 Resolution (pp. 316–330)
FOL → CNF (Skolemization eliminates ∃), binary resolution with unification, example proofs, **refutation completeness** (via Herbrand / ground resolution lifting), equality (demodulation, paramodulation), resolution strategies (unit preference, set of support, input resolution, subsumption). Works for *any* KB, not only definite clauses. → [[cnf-and-resolution]], [[first-order-inference]].

## Slide vs. book
- Slide 5 ("first-order entailment stays semi-decidable") ✓ p. 299/305; slide 2's plain "Undecidable" for FOL is imprecise: **validity/entailment is semidecidable** (undecidable = no algorithm that always halts).
- Slides 14–15, 23: no-occurs-check, depth-first control and closed-world negation all confirmed as *departures of Prolog from logic* (p. 312, 315).
