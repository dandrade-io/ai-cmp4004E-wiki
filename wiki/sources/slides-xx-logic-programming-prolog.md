---
title: Slides XX — Logic Programming with Prolog
type: source
tags: [prolog, logic, slides]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Slides XX — Logic Programming with Prolog (31 slides)

Lecture + lab on going from logic that can only be *checked* to logic that can be *run*. Thesis: **Algorithm = Logic + Control** (Kowalski, 1979) — you write the clauses (logic); Prolog supplies the control ([[sld-resolution-and-backtracking]]). See [[logic-programming]].

## Slide map
| Slides | Topic | Page |
|---|---|---|
| 2 | Roadmap: propositional → FOL → Horn → Prolog | [[propositional-vs-first-order-logic]] |
| 3 | CNF, literals, clauses, resolution | [[cnf-and-resolution]] |
| 4–5 | Horn clauses; AND–OR graph | [[horn-clauses]] |
| 6 | Backward chaining, Criminal(West) proof tree | [[forward-and-backward-chaining]] |
| 7 | FOL → Prolog syntax conventions | [[prolog-syntax-and-terms]] |
| 8 | What is Prolog, history | [[prolog]], [[alain-colmerauer]], [[robert-kowalski]] |
| 9–11 | SWI-Prolog, install, first session | [[swi-prolog]] |
| 12–13 | Anatomy of a program, querying, findall/setof | [[prolog-syntax-and-terms]], [[prolog-built-ins]] |
| 14 | Unification | [[unification]] |
| 15 | SLD resolution, clause order, tabling | [[sld-resolution-and-backtracking]] |
| 16 | `is/2` vs `=/2` | [[prolog-arithmetic]] |
| 17–21 | factorial, fibonacci, lists, isEven, isPerm | [[prolog-lists-and-recursion]] |
| 22 | Binary search tree | [[prolog-binary-search-tree]] |
| 23 | Negation as failure, cut | [[negation-as-failure]], [[prolog-cut]] |
| 24 | Built-ins worth memorising | [[prolog-built-ins]] |
| 25–27 | N-Queens case study | [[n-queens-prolog]] |
| 28 | Debugging, common mistakes | [[prolog-debugging-and-common-mistakes]] |
| 29–30 | Prolog Lab 01 + grading | [[prolog-lab-01]] |
| 31 | Further reading | below |

Cheat sheet: [[prolog-cheatsheet]].

## Further reading (slide 31)
Russell & Norvig 4th ed. ch. 7.5 (Horn clauses/chaining) and 9.4 (backward chaining, logic programming) — see [[russell-norvig]]; Luger 6th ed. §14.2–14.3; Bratko *Prolog Programming for AI*; Sterling & Shapiro *The Art of Prolog*; swi-prolog.org, swish.swi-prolog.org, learnprolognow.org, metalevel.at/prolog.

## Errata / cross-source conflict
> ⚠️ Errata: [[slides-01-introduction-to-ai]] (slide 9) says Prolog was "created by Dennis Ritchie at Bell Labs" and is an "imperative, compiled language". That describes C, not Prolog. This deck (slide 8) is correct: Prolog was born in Marseille in 1972 (Colmerauer and Roussel), on theory from Kowalski, and is declarative.

Also: the fenced-code slide 23 example `max(X,Y,X) :- X >= Y, !.` is deliberately wrong (see [[prolog-cut]]); slide 21's `isPerm` is deliberately buggy (see [[prolog-lists-and-recursion]]).
