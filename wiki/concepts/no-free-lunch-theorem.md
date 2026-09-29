---
title: No Free Lunch Theorem
type: concept
tags: [theory, optimization]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# No Free Lunch (NFL) theorem

Wolpert & Macready: averaged over **all possible problems**, all **non-revisiting black-box** algorithms perform identically (book §16.10, p.243; [[eiben-ch16-theory-no-free-lunch]]). "Non-revisiting" = never re-evaluates a point (an archive can enforce it); "black-box" = no problem-specific knowledge.

## Lessons (p.244)
1. An algorithm that shines on one problem class pays on others → evaluate new operators carefully (Ch.9).
2. For a *given* problem you can beat NFL by adding problem-specific knowledge → hybrids/[[memetic-algorithms]].
3. It overturns the 1980s picture of EAs as uniformly good (Goldberg's curve, Fig. 3.8) — the claim "EA always above random search" is fundamentally incorrect (p.44). Debate: real-world problems may be a special subset of all problems.

Related: [[metaheuristics]], [[optimization-algorithms-comparison]], [[genetic-algorithms]].

## Exam angles
- State NFL in one sentence and say why it doesn't forbid using GAs.
