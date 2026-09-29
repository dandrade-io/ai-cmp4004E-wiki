---
title: Logic Programming
type: concept
tags: [prolog, logic, paradigm]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Logic Programming

## Intuition
You state **what holds** (facts and rules), not **how to compute it**. The interpreter searches for a proof; the answer is the substitution that made the proof work (slide 8).

## Key idea: Algorithm = Logic + Control
Kowalski's slogan (slide 2): the programmer writes the *logic* (clauses); the system supplies the *control* (search strategy). In [[prolog]] the control is fixed: depth-first, left-to-right [[sld-resolution-and-backtracking]] over [[horn-clauses]] using [[unification]].

## Ladder of logics (slide 2)
1. Propositional calculus — decidable, cannot say "every".
2. First-order calculus — objects/quantifiers, undecidable.
3. Horn clauses — ≤1 positive literal, cheap entailment.
4. Prolog — Horn clauses + backward chaining + unification.
See [[propositional-vs-first-order-logic]].

## AIMA view (§9.4.2, p. 312)
Logic programming "comes close to embodying the declarative ideal" of Ch. 7: express knowledge formally and solve problems by running inference. Prolog is a *compromise between declarativeness and efficiency*: it departs from pure logic in five ways — database semantics, built-in arithmetic (`X is 4+3` works; `5 is X+Y` fails), side-effecting predicates (I/O, assert/retract), no occurs check, and depth-first search without loop checks. **Constraint logic programming (CLP)** generalises binding to *constraining* variables (answer like `7 > Z > 1`) and reuses CSP techniques ([[backtracking-search-csp]], p. 316). See [[aima-ch09-inference-in-first-order-logic]], [[first-order-inference]].

## Declarative reading
```prolog
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```
"X is an ancestor of Y if X is a parent of Y, or a parent of some Z who is an ancestor of Y."

## Uses (slide 8)
Expert systems, rule engines, legal/medical reasoning, NL parsing (DCGs), compilers, program analysis, constraint problems. The intro deck notes expert systems in legal/medical/financial domains ([[slides-01-introduction-to-ai]]).

## Pitfalls
Prolog's control is *not* logically complete: clause/goal order changes behaviour. "SLD resolution is complete; Prolog's search rule is not" (slide 15).

## Exam angles
- Explain Algorithm = Logic + Control and who said it (Kowalski, 1979).
- Relation vs function: one query can succeed once per solution.
- Why restrict to Horn clauses? Tractability.
