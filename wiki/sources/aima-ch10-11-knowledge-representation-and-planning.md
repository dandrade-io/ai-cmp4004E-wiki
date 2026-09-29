---
title: "AIMA Ch. 10–11 — Knowledge Representation and Automated Planning"
type: source
tags: [knowledge-representation, planning, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapters 10–11 (brief)

Book: [[russell-norvig]]. **Not covered by any slide deck yet** (syllabus topic 5 in [[slides-00-course-intro]] is "Knowledge, reasoning, and planning"); skimmed by section heads only — study depth is a TODO.

## Ch. 10 Knowledge Representation (~pp. 314–360)
10.1 Ontological engineering (upper ontologies); 10.2 categories and objects (inheritance, physical composition); 10.3 events; 10.4 mental objects and modal logic; 10.5 **reasoning systems for categories**: semantic networks and **description logics** (subsumption, classification; emphasis on tractability); 10.6 **reasoning with default information** — nonmonotonic logics (circumscription, default logic), truth maintenance. Contrast with the *monotonicity* of ordinary FOL (§7.5.1, p. 242).

## Ch. 11 Automated Planning (~pp. 362–412)
11.1 **Classical planning**: PDDL (Lisp-like syntax; states as conjunctions of fluents, actions with preconditions/effects); 11.2 algorithms — forward state-space search, backward (**regression**) search, SAT-based planning, **Graphplan** planning graph, partial-order plans; 11.3 heuristics — **ignore-preconditions**, ignore-delete-lists, state abstraction; 11.4 hierarchical planning (HTN, high-level actions); 11.5 planning in nondeterministic domains; 11.6 time, schedules, resources; 11.7 comparison of approaches.

## Links
Planning is search ([[problem-formulation]], [[a-star-search]], [[informed-search-and-heuristics]]) over a factored representation ([[state-representation]]); constraint-based scheduling ties to [[constraint-satisfaction-problems]]; logical planning to [[model-checking-and-entailment]].
