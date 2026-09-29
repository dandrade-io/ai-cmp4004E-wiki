---
title: Survivor Selection and Elitism
type: concept
tags: [evolutionary, selection]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Survivor selection (replacement) and elitism

## Intuition
After offspring are created, decide which μ individuals form the next generation. Often **deterministic** (unlike parent selection). Terminology: "survivor selection" when many offspring are produced; "replacement" when few (steady state) — book §3.2.6, p.33.

## Strategies ([[eiben-ch05-selection-and-population-management]], pp.87–90)
- **Age-based:** generational (μ = λ, Simple GA) or FIFO in steady state; random replacement is *not recommended* (may lose the best; Smith & Vavak).
- **Fitness-based:** *replace worst* (GENITOR: fast but premature convergence; pair with big populations / no-duplicates); **elitism** (always keep the current best; combine with age-based schemes); round-robin tournament (EP, q ≈ 10); **(μ+λ)**; **(μ,λ)**.
- **(μ,λ) vs (μ+λ)** in [[evolution-strategies]]: (μ,λ) discards all parents ⇒ can leave local optima, tracks moving optima, does not preserve mis-adapted step sizes (needed for [[self-adaptive-mutation]]); rule of thumb λ/μ ≈ 5–7.

## Example
Book's 8-queens EA (Table 3.4): pop 100, 2 offspring per cycle, merge and delete the worst two ("replace worst"). Knapsack EA: generational, pop 500.

## Related
[[selection-mechanisms]], [[genetic-algorithms]], [[exploration-vs-exploitation]].

## Exam angles
- Distinguish generational vs steady-state and give the generational gap λ/μ.
- Why does (μ+λ) hinder self-adaptation?
