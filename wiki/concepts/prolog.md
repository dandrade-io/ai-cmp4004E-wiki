---
title: Prolog
type: concept
tags: [prolog, logic-programming]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog

## What it is
*Programmation en logique*: the most widely used [[logic-programming]] language (slide 8). Born in Marseille, 1972 — [[alain-colmerauer]] and Philippe Roussel — on theory from [[robert-kowalski]] (Edinburgh).

> ⚠️ Errata: [[slides-01-introduction-to-ai]] says it was created by Dennis Ritchie and is imperative/compiled. Wrong (that is C); see [[slides-xx-logic-programming-prolog]].

## Formula
Prolog = [[horn-clauses]] + backward chaining ([[forward-and-backward-chaining]]) + [[unification]], executed by [[sld-resolution-and-backtracking]] (slide 2).

## Programming model
- Programs are facts and rules; you ask queries.
- A predicate is a relation, not a function — can run "backwards" (`append(X,Y,[1,2,3])`).
- Data structures are terms ([[prolog-binary-search-tree]]).

## Used for
Expert systems, rule engines, legal/medical reasoning, DCG parsing, compilers, program analysis, constraints.

## Implementation
[[swi-prolog]] (course choice).

## Limits
Search is depth-first with no occurs check by default; left recursion loops; cut and negation break declarative reading ([[prolog-cut]], [[negation-as-failure]]).

## Exam angles
- Who/when/where created Prolog?
- What does the interpreter return? The substitution that made the proof work.
- Cheat sheet: [[prolog-cheatsheet]].
