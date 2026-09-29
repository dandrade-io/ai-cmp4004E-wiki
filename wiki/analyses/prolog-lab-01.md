---
title: Prolog Lab 01 — Spec and Study Plan
type: analysis
tags: [prolog, assignment, exam-prep]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Lab 01 (slides 29–30)

## Spec (100 pts + 10 bonus)
| # | Task | Pts |
|---|---|---|
| 1 | Bigger KB from `01_Code/family.pl`: ≥16 people, four generations, new `spouse/2`. Both parents for every child; a couple with ≥3 children; someone with none | 20 |
| 2 | ≥8 rules: `mother/2, sister/2, grandmother/2, uncle/2, cousin/2, father_in_law/2` + one recursive rule of your own (not `ancestor/2`) | 35 |
| 3 | ≥20 plunit tests, ≥6 negative; one shows nobody is their own sibling; `?- run_tests.` all pass | 25 |
| 4 | Analysis, half a page: why `sibling/2` needs `X \= Y`; which rules return the same answer twice and why; what the closed-world assumption claims that you never wrote | 20 |
| Bonus | `related(X,Y)`: connected by any chain of parent/child/marriage links; must terminate (naive version walks up a parent link and back down forever) | +10 |

## Deliverables
`lastname_firstname_lab01.pl` (KB, rules, tests; one section per exercise) and `.pdf` (≤2 pages: `run_tests` output + analysis). Must load cleanly: `swipl -g true -t halt file.pl` — errors and singleton warnings cost points. Invent your own family. If an AI assistant was used, say so in a header comment and state what you changed. Due same day 23:59.

## Study plan (concepts to master first)
1. Facts/rules/queries: [[prolog-syntax-and-terms]] (read the family.pl example).
2. Why duplicates appear: multiple proof paths — [[sld-resolution-and-backtracking]], dedupe with `setof` ([[prolog-built-ins]]).
3. `X \= Y` and [[unification]] (two siblings via same parent unify with themselves).
4. Negative tests and CWA: [[negation-as-failure]].
5. Recursive rule (e.g. descendant-style, or a chain over spouse/parent) — base case first, avoid left recursion.
6. Bonus: think about a visited-list or tabling ([[swi-prolog]] `:- table`) to stop loops.
7. Tests: plunit syntax in [[swi-prolog]]; mistakes in [[prolog-debugging-and-common-mistakes]].

Cheat sheet: [[prolog-cheatsheet]]. Source: [[slides-xx-logic-programming-prolog]].
