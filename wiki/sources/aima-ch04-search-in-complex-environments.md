---
title: "AIMA Ch. 4 — Search in Complex Environments"
type: source
tags: [search, optimization, local-search, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 4 — Search in Complex Environments (pp. 128–160)

Book: [[russell-norvig]]. Related course material: [[slides-04-optimization]] (optimization), [[slides-02-problem-solving]]. Cross-notes for the optimization pages: [[aima-local-search-notes]].

## Summary
Relaxes chapter 3's assumptions: first *where the path doesn't matter* (local search, discrete and continuous), then nondeterminism (AND–OR search), partial observability (belief states) and unknown environments (online search).

## 4.1 Local search and optimization (pp. 128–137)
- **Local search**: keep only a current state (no paths, no reached set); not systematic, but tiny memory and works in huge/infinite spaces. Solves **optimization problems** with an **objective function** over a *state-space landscape* (global max, local max, "flat" local max, shoulder; Fig. 4.1) → [[local-search]].
- **Hill climbing** (Fig. 4.2): move to best neighbor; stops at a peak. 8-queens (complete-state formulation, h = attacking pairs, 8×7 = 56 successors): steepest ascent gets stuck **86 %** of the time (solves 14 %), ~4 steps on success; with ≤100 sideways moves solves **94 %** (≈21 steps on success, 64 on failure). Variants: stochastic, first-choice, **random-restart** (expected 1/p restarts; p ≈ 0.14 → ~7 iterations) → [[hill-climbing]].
- **Simulated annealing** (Fig. 4.5): random successor; accept if better, else with probability e^(ΔE/T) where ΔE is the (negative) change in value; T decreases by a schedule; if T falls slowly enough, converges to the global optimum with probability → 1 (Boltzmann distribution) → [[simulated-annealing]].
- **Local beam search** (k states, shares information; stochastic beam search for diversity).
- **Evolutionary algorithms** (Fig. 4.6–4.8): population, fitness, selection, crossover (mixing number ρ), mutation, elitism; genetic algorithms use strings over a finite alphabet, evolution strategies real vectors, genetic programming programs; the **schema** theory explains why crossover helps only when building blocks are meaningful → [[genetic-algorithms]], [[crossover-and-mutation]], [[evolutionary-computation]].

## 4.2 Continuous spaces (pp. 137–140)
Discretization / empirical gradient; the **gradient** ∇f; update **x ← x + α∇f(x)** (step size α: too small = slow, too large = overshoot; line search); **Newton–Raphson** x ← x − H⁻¹∇f; constrained optimization, linear programming, convex optimization (polynomial-time) → [[gradient-descent]].
Note: AIMA writes "gradient *descent*" for minimizing cost and *hill climbing* for maximizing objective — the same idea (p. 129).

## 4.3–4.5 Nondeterminism, partial observability, online search (pp. 140–160)
- **AND–OR search trees** produce *contingent plans* (erratic vacuum world).
- **Belief states** (sets of possible states); sensorless problems solved by ordinary search over belief-state space.
- **Online search** / exploration: agents interleave planning and acting in unknown environments; online DFS, LRTA*, learning heuristics from experience.
Not covered in the slides.

## Historical notes worth remembering (p. 160)
Simulated annealing: Kirkpatrick et al. (1983), borrowing the Metropolis algorithm (1953). Tabu search (OR). STAGE algorithm. Local search was reinvigorated in the early 1990s by results on n-queens and SAT.

## Slide / code vs. book
> ⚠️ Note (sign convention): Fig. 4.5 (p. 133) is printed as `ΔE ← VALUE(current) − VALUE(next); if ΔE > 0 then current ← next, else current ← next with probability e^(ΔE/T)`, (as extracted from the PDF; the sign of ΔE reads oddly for a maximization problem, so rely on the prose on p. 132: better moves always accepted, worse moves accepted with probability < 1 that falls exponentially with the badness ΔE and as T decreases). The course code in [[code-simulated-annealing]] *minimizes* cost and accepts a worse move with probability exp(−Δ/T), Δ = new − current > 0. Both give a probability < 1 that shrinks with badness and with T. Watch the sign when reading either.

> ⚠️ Note: [[slides-04-optimization]] presents Holland's GA with only bit strings, single-point crossover and mutation; AIMA notes GAs work best when adjacent positions form meaningful building blocks (schemas) and that representation engineering is critical (p. 136–137). It also questions how much of GAs' appeal is the metaphor versus performance (p. 137).

## Pages updated / created
[[hill-climbing]], [[local-search]], [[aima-local-search-notes]] (new). The simulated-annealing, genetic-algorithm and gradient-descent pages are owned by others; see [[aima-local-search-notes]] for the AIMA content to merge.
