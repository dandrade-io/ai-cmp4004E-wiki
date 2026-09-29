---
title: Selection Mechanisms (Parent Selection)
type: concept
tags: [evolutionary, selection]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Selection Mechanisms (parent selection)

## Intuition
Parent selection gives better individuals a higher chance to reproduce. It depends **only on fitness**, never on the representation (Eiben & Smith p.28), and is usually **probabilistic** — weak individuals keep a small chance, otherwise the search gets too greedy and stalls in a local optimum (p.31). Survivor selection is covered in [[survivor-selection-and-elitism]].

## Methods (book Ch.5, [[eiben-ch05-selection-and-population-management]])
| Method | Probability / procedure | Notes |
|---|---|---|
| **Fitness-proportional (FPS)** | P(i) = f_i / Σ f_j | premature convergence; weak pressure when fitnesses are close; **not translation invariant** |
| **Windowing** | subtract β^t = min fitness in population | restores differentials |
| **Sigma scaling** | f' = max(f − (f̄ − c·σ), 0), c = 2 | uses mean & std-dev |
| **Linear ranking** | P(i) = (2−s)/μ + 2i(s−1)/(μ(μ−1)), 1 < s ≤ 2, worst rank 0 | s = expected copies of the best; max pressure s = 2 |
| **Exponential ranking** | P(i) ∝ 1 − e^(−i/c) | higher pressure |
| **Tournament (k)** | sample k, keep best (prob. p) | no global knowledge; only needs an ordering; larger k ⇒ more pressure; invariant to fitness transposition |
| **Uniform** | P = 1/μ | ES/EP; pressure comes from survivor selection |
| **Over-selection** | 80 % of picks from top x % (x = 32,16,8,4 for pop 1000…8000) | GP with huge populations |

## Sampling algorithms
- **Roulette wheel**: cumulative probabilities a_i; per pick draw r ∈ [0,1] and take first a_i ≥ r. High variance.
- **Stochastic Universal Sampling (SUS)**: one spin, λ equally spaced pointers; each parent gets ⌊λP⌋ or ⌈λP⌉ copies. Preferred over roulette (p.84).

## Worked examples
**FPS, book Table 3.1** (maximise x², 5-bit): x = 13, 24, 8, 19 → f = 169, 576, 64, 361 (Σ = 1170) → P = 0.14, 0.49, 0.06, 0.31; expected copies (×4) = 0.58, 1.97, 0.22, 1.23.

**Not translation invariant** (Table 5.1): f = (1, 4, 5) → P = (0.10, 0.40, 0.50). Adding 10: (11,14,15) → (0.275, 0.35, 0.375); adding 100 → (0.326, 0.335, 0.339): almost uniform.

**Linear ranking, μ = 3** (ranks A=0, B=1, C=2): s = 2 → (0, 0.33, 0.67); s = 1.5 → (0.167, 0.333, 0.5).

**SUS**: P = (0.1, 0.4, 0.5) → a = [0.1, 0.5, 1.0]; λ = 4, r ∈ [0, 0.25], say r = 0.2 → pointers 0.2, 0.45, 0.7, 0.95 → picks B, B, C, C.

## Selection pressure
Takeover time τ* = ln λ / ln(λ/μ) for ES (μ=15, λ=100 ⇒ ≈ 2.4, book says ≈ 2); FPS GA: τ* = λ ln λ (λ=100 ⇒ ≈ 460). So a typical ES is far more aggressive than a simple GA (p.90). Book warns such measures ignore variation and did not predict solution quality well.

## Related
[[genetic-algorithms]], [[evolution-strategies]], [[diversity-and-niching]], [[exploration-vs-exploitation]], [[crossover-and-mutation]].

## Exam angles
- Compute FPS probabilities and expected counts; explain why adding a constant changes them (and ranking/tournament don't).
- SUS vs roulette: variance.
- How does tournament size k tune pressure?
