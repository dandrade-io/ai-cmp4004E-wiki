---
title: Horn Clauses
type: concept
tags: [logic, prolog]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Horn Clauses

## Definition (slide 4)
A clause with **at most one positive literal**. That restriction buys three things (slides 4–5):
1. Clauses read as implications: `¬L ∨ ¬B ∨ M` ≡ `L ∧ B ⇒ M`.
2. Inference by chaining, forward or backward ([[forward-and-backward-chaining]]).
3. Cheap entailment: linear in a propositional definite-clause KB; first-order stays semi-decidable but far cheaper than full resolution.

## Three shapes
| Kind | Logic | Implication | Prolog |
|---|---|---|---|
| Definite clause (rule) | `¬A ∨ ¬B ∨ C` | `A ∧ B ⇒ C` | `c :- a, b.` |
| Fact | `C` | `True ⇒ C` | `c.` |
| Goal clause (query) | `¬A ∨ ¬B` | `A ∧ B ⇒ False` | `?- a, b.` |

## AIMA precision (§7.5.3, p. 247)
- **Definite clause** = exactly one positive literal; **Horn** = at most one; **goal clause** = none; a **k-CNF** sentence has ≤ k literals per clause. In implication form the premise is the **body**, the conclusion the **head**; a single positive literal is a **fact**.
- Horn clauses are **closed under resolution** (resolving two Horn clauses gives a Horn clause).
- The three benefits on slides 4–5 are exactly AIMA's three reasons: implication reading, chaining, and **entailment linear in the KB size** (propositional case).
- Note: the intro deck (slide 9) says Prolog programs are "positive clauses"; AIMA says **definite clauses** (Prolog queries are the goal clauses).

## Not everything is Horn
`P ∨ Q` has two positive literals — no Horn form. Price of tractability: Prolog cannot say "one of these, I don't know which".

## AND–OR graph (slide 5)
Seven Horn clauses drawn as a graph (R&N Fig. 7.16): links joined by an arc = conjunction; separate links = alternatives. Prolog explores exactly this graph depth-first, left to right.

## Related
[[cnf-and-resolution]], [[prolog]], [[logic-programming]].

## Exam angles
- Classify a clause as fact/rule/goal/non-Horn.
- Why can't Prolog express disjunctive facts?
- Convert `¬A ∨ ¬B ∨ C` to implication form.

Source: [[aima-ch07-logical-agents]].
