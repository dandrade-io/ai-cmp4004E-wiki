---
title: Forward and Backward Chaining
type: concept
tags: [logic, inference, prolog]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Forward and Backward Chaining

Two inference strategies over [[horn-clauses]] (slide 5): **forward** goes from facts toward the query; **backward** goes from the query toward facts.

## Backward chaining (slide 6)
From the query, prove the body of any matching clause; recurse down to facts, **depth first, left to right**. Only facts relevant to the query are touched, and space is linear in the size of the proof. Example: proof tree for `Criminal(West)` (R&N Fig. 9.7, [[russell-norvig]]).

```prolog
criminal(X) :- american(X), weapon(Y), sells(X, Y, Z), hostile(Z).
weapon(X)  :- missile(X).
hostile(X) :- enemy(X, america).
sells(west, X, nono) :- missile(X), owns(nono, X).
american(west).  missile(m1).  owns(nono, m1).  enemy(nono, america).
?- criminal(west).   % true.
```

## Forward chaining
Fire rules whose premises are known, add conclusions, repeat until the query appears or nothing new (AIMA §7.5.4, pp. 248–250). **PL-FC-ENTAILS?** (Fig. 7.15) keeps a `count` of unproven premises per clause, an `inferred` table and an agenda queue: **linear time**, sound (each step is Modus Ponens) and complete (the fixed point is a model of the KB). **Data-driven** — good for incremental reasoning from percepts, but may derive many irrelevant facts. In first-order logic it terminates for **Datalog**; with function symbols it can generate infinitely many facts (NatNum(S(S(0))), …) ([[first-order-inference]]).

## Comparison
| | Forward | Backward |
|---|---|---|
| Direction | facts → query | query → facts |
| Driven by | data | goal |
| Relevance | derives irrelevant facts | focused |
| Used by | deductive databases, production/rule systems | [[prolog]] |
| Cost | linear (propositional) | often much less than linear: touches only relevant facts |
| Weakness | irrelevant facts; NP-hard rule matching in FOL | repeated subgoals, infinite loops, incompleteness in Prolog |
| Goal-directed? | no (data-driven) | yes (answers "what shall I do now?") |

## Backward chaining in AIMA (§9.4, p. 311)
FOL-BC-ASK is AND/OR search: OR = any matching rule, AND = all body conjuncts, each with the accumulated substitution; **depth-first**, **linear space in proof size**, but suffers repeated states and incompleteness. Forward chaining halts on the graph `path` program where Prolog loops, and needs only ≤ n² path facts (62 vs 877 inferences in the book's example).

## Pitfalls
Prolog's backward chaining with fixed clause order can loop ([[sld-resolution-and-backtracking]]). Tabling combines goal-direction with forward chaining's dynamic-programming efficiency.

## Exam angles
- Trace backward chaining for `criminal(west)`.
- Which is Prolog? Backward chaining + [[unification]].

Source: [[aima-ch07-logical-agents]], [[aima-ch09-inference-in-first-order-logic]].
