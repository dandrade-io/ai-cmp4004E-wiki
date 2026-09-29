---
title: Evolutionary Programming (EP)
type: concept
tags: [evolutionary]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Evolutionary Programming (EP)

Developed by **L. Fogel et al. in the 1960s** to simulate evolution as a learning process aiming at artificial intelligence: intelligence = adapting behaviour to meet goals in many environments; classic individuals were **finite-state machines** (book p.103; see [[lawrence-fogel]]).

## Modern EP (Table 6.3)
Real-valued vectors; **no recombination** (each individual represents a *species*); Gaussian mutation; each parent creates exactly one child (λ = μ); parents + offspring compete in **stochastic round-robin tournaments** ((μ+μ), q ≈ 10). *Meta-EP* self-adapts step sizes (lognormal, σ first). Practically merged with [[evolution-strategies]].
- Mutation-only vs recombination debate (Fogel & Atmar 1990s): current view — mutation better early, crossover gains later; constant operator probabilities are limiting.
- **IFEP** (Yao): one Gaussian and one Cauchy offspring per parent — fat tail escapes local minima, Gaussian fine-tunes.

Related: [[evolutionary-computation]], [[self-adaptive-mutation]], [[survivor-selection-and-elitism]].

## Exam angles
- Compare EP and ES (recombination, selection).
