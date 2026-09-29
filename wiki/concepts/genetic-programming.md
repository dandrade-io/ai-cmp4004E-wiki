---
title: Genetic Programming (GP)
type: concept
tags: [evolutionary, machine-learning]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Genetic Programming (GP)

Evolutionary algorithm whose individuals are **parse trees** (expressions, formulas, programs) — positioned in machine learning: it seeks *models with maximum fit* rather than inputs with maximum payoff (book §6.4, p.104). "Programming of computers by means of natural selection" (Koza).

## Representation
Function set F (internal nodes, e.g. {+,−,·,/}) and terminal set T (leaves, e.g. ℝ ∪ {x,y}); **closure property** (any function accepts any argument); strongly-typed GP adds types. Example: 2·π + ((x+3) − y/(5+1)) ↔ Lisp `(+ (* 2 π) (- (+ x 3) (/ y (+ 5 1))))`.

## Operators (Sect. 4.6)
- **Subtree crossover**: swap subtrees at two random nodes; children can be deeper than parents.
- **Subtree mutation**: replace subtree at a random node by a random tree.
- GP creates offspring by **either** crossover **or** mutation (not both in sequence); Koza recommended mutation rate 0, later ~5 %.
- **Initialisation**: ramped half-and-half (full + grow methods to max depth D_max).
- **Over-selection** for populations of thousands ([[selection-mechanisms]]).
- **Bloat** ("survival of the fattest"): trees grow; counter with maximum tree size or **parsimony pressure** (fitness penalty for size).

Related: [[learning-classifier-systems]], [[evolutionary-computation]], [[eiben-ch04-representation-variation]].

## Exam angles
- Define function/terminal sets for a given problem; do a subtree crossover; explain bloat.
