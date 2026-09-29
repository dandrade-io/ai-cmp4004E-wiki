---
title: Multi-Objective Optimization
type: concept
tags: [evolutionary, optimization]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Multi-objective optimisation

Several conflicting objectives (book Ch.12; only §12.1–12.2 read, pp.195–197). A dominates B (A ≽ B, maximisation) iff aᵢ ≥ bᵢ for all i and aᵢ > bᵢ for at least one i. **Non-dominated** solutions form the **Pareto set/front**; improving one objective there hurts another.

**Example (maximise both):** A = (3,5), B = (2,4) ⇒ A dominates B; A = (3,5) and C = (4,2) are mutually non-dominated (both on the front).

EAs suit this because a population can approximate the whole front (non-elitist/elitist approaches, diversity maintenance, decomposition — names only in the book excerpt read: NPGA, SPEA-2, PAES). Real fronts can be non-convex or discontinuous, defeating scalarisation.

Related: [[constraint-handling-in-ea]], [[diversity-and-niching]].
Compare with utility-based agents ([[agent-types]]): a scalar utility is one way to trade off conflicting objectives.
