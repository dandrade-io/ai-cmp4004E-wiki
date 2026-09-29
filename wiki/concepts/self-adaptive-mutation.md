---
title: Self-Adaptive Mutation
type: concept
tags: [evolutionary, continuous, parameter-control]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Self-adaptive mutation (real-valued representation)

## Idea
Include the mutation **step sizes in the chromosome** so they co-evolve with the solution; a step size is judged indirectly by whether the offspring it produces survive (book §4.4.2, pp.57–65). Always mutate **σ first, then x** (the new individual is "evaluated twice": as a solution and as a step-size producer).

## Variants
| Variant | Chromosome | Update |
|---|---|---|
| Uncorrelated, 1 step size | ⟨x₁…xₙ, σ⟩ | σ' = σ·e^{τN(0,1)}; x'ᵢ = xᵢ + σ'·Nᵢ(0,1); τ ∝ 1/√n; boundary rule σ' < ε₀ ⇒ ε₀ |
| Uncorrelated, n step sizes | ⟨x, σ₁…σₙ⟩ | σ'ᵢ = σᵢ·e^{τ'N(0,1)+τNᵢ(0,1)}; τ' ∝ 1/√(2n), τ ∝ 1/√(2√n) |
| Correlated | ⟨x, σ, α₁…α_{n(n−1)/2}⟩ | α'ⱼ = αⱼ + β·N(0,1), β ≈ 5°; mutation vector ~ N(0, C') |

Offspring lie on a **circle** (1 σ), an **axis-parallel ellipse** (n σ) or a **rotated ellipse** (correlated). "We can get nothing for free": more parameters ⇒ more evaluations to learn them (p.62). σ must decrease over time (explore early, fine-tune late).

**Log-normal** multiplier: smaller changes more often than large, σ > 0, median 1, neutral on average.

## Conditions for self-adaptation to work (p.65)
μ > 1; λ > μ; not-too-strong pressure (λ/μ ≈ 7); **(μ,λ)** selection; intermediate recombination of strategy parameters.

## Worked example
σ = 1, τ = 0.2, draw N(0,1) = 0.5 ⇒ σ' = e^{0.1} ≈ 1.105; then x' = x + 1.105·N_i(0,1).

## Related
[[evolution-strategies]], [[parameter-control]], [[crossover-and-mutation]], [[evolutionary-programming]].

## Exam angles
- Write the σ-then-x update for one step size.
- Why does (μ+λ) selection hurt self-adaptation?
