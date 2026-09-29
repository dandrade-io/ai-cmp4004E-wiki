---
title: CNF and Resolution
type: concept
tags: [logic, inference]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# CNF and Resolution

## Definitions (slide 3)
- **Literal** — a symbol or its negation.
- **Clause** — a disjunction of literals.
- **CNF sentence** — a conjunction of clauses.

Every propositional sentence can be rewritten into CNF; the rewrite is an **equivalence**, nothing is lost. (Grammar: R&N Fig. 7.12, see [[russell-norvig]].)

## Why bother
**Resolution** is a single inference rule that is **refutation-complete** for propositional logic, and it needs clause form as input.

## Resolution rule (AIMA §7.5.2, pp. 243–247)
From clauses ℓ₁∨…∨ℓₖ and m₁∨…∨mₙ with complementary literals ℓᵢ, mⱼ derive the clause of all remaining literals (**one pair at a time**; remove duplicates = **factoring**; e.g. (A∨B) with (A∨¬B) gives A). Unit resolution is the special case with a unit clause. Example: `(A ∨ B)` and `(¬A ∨ C)` → `(B ∨ C)`. Clauses with complementary literals are tautologies and can be discarded.

**PL-RESOLUTION (Fig. 7.13)**: to show KB ⊨ α, convert KB ∧ ¬α to CNF and resolve pairs until (a) the **empty clause** appears → entailed, or (b) no new clauses → not entailed. It terminates (finite resolution closure RC(S)) and is complete by the **ground resolution theorem**: if a set of clauses is unsatisfiable, its closure contains the empty clause. CNF conversion: eliminate ⇔, ⇒; push ¬ inward (De Morgan); distribute ∨ over ∧. Every sentence has an equivalent CNF.

First-order version: needs Skolemization for ∃ and unification ([[first-order-inference]], AIMA §9.5).

## Leading to Horn clauses
The CNF grammar names the two clause shapes of interest: definite clauses and goal clauses — see [[horn-clauses]]. Prolog avoids full resolution, using the cheaper [[sld-resolution-and-backtracking]].

## Pitfalls
"Refutation-complete" ≠ "can derive every consequence directly"; it proves by contradiction.

## Related
[[propositional-vs-first-order-logic]], [[forward-and-backward-chaining]].

## Exam angles
- Convert a small implication to CNF.
- Define literal / clause / CNF.
- Why is CNF needed for resolution?

Source: [[aima-ch07-logical-agents]], [[aima-ch09-inference-in-first-order-logic]]. Worked in the wumpus world: [[wumpus-world]].
