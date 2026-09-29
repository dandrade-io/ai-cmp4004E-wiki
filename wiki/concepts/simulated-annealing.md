---
title: Simulated Annealing
type: concept
tags: [optimization, metaheuristic, stochastic]
sources: [raw/code/sa_functions.py, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Simulated Annealing (SA)

## Intuition
Inspired by annealing metal: heat it (atoms move freely), then cool slowly so it settles into a low-energy crystal. High temperature T ⇒ accept many worse moves (explore); low T ⇒ only improvements (exploit). Not covered in slides-04 text; the code file is the course source ([[code-simulated-annealing]]).

## Algorithm (as in the code)
```
x ← random; T ← T0
repeat max_iter times:
    x' ← x + noise (clipped to bounds)
    Δ ← f(x') − f(x)
    if Δ < 0 or rand() < exp(−Δ/T): x ← x'      # Metropolis criterion
    T ← α·T                                       # geometric cooling, α<1
return best seen
```
Acceptance probability for a worse move: exp(−Δ/T) — falls as Δ grows or T shrinks.

## Parameters
Initial temperature T0, cooling rate α (typically 0.95–0.9999, background), iterations, neighbourhood/step size, bounds.

## Empirical comparison (Dorigo et al. 1996)
On the 30-city Oliver30 TSP with equal time (1 h, 386 PC), SA with geometric cooling `T(t+1)=0.99·T(t)` scored best 422 / avg 459.8 (σ 25.1) versus 420 / 420.4 for Ant System and 420 / 420.6 for Tabu Search ([[paper-dorigo-ant-system-1996]] Table IV, PDF p.9) — SA was less consistent. Note the paper's cooling factor 0.99, versus 0.8 in [[code-simulated-annealing]].

## Pros / cons
+ Simple, one solution in memory, can escape local minima, no gradient. − Sensitive to cooling schedule; too-fast cooling ≈ hill climbing (the course code with α = 0.8 does exactly this — see errata in [[code-simulated-annealing]]); theoretical convergence needs very slow (logarithmic) cooling (unverified).

## Related
[[exploration-vs-exploitation]], [[metaheuristics]], [[optimization-landscape]], [[benchmark-functions]], [[optimization-algorithms-comparison]].

## Exam angles
- Compute acceptance probability for Δ = 2, T = 10 (e^−0.2 ≈ 0.82).
- What happens as T → 0? (greedy) T → ∞? (random walk)
- Why does a bad cooling rate ruin results?

## In Eiben & Smith (§8.4.5, p.142)
SA is "a generate-and-test technique based on a physical analogy"; formally a **(1+1) EA with increasing selection pressure** — population 1, problem-specific mutation, and a Boltzmann-style survivor selection: accept a worse neighbour j with probability exp((f(i) − f(j))/c_k) (maximisation; c_k = temperature) — the **Metropolis criterion**. The cooling schedule is a *deterministic, state-blind parameter control* (p.132), unlike adaptive/self-adaptive control ([[parameter-control]]). Convergence proofs exist for SA and some EAs but they do not identify the optimum as global (p.47). See [[metaheuristics]].
