---
title: "Code — Simulated Annealing (sa_functions.py)"
type: source
tags: [optimization, simulated-annealing, code]
sources: [raw/code/sa_functions.py]
updated: 2026-09-29
---
# Code — Simulated Annealing

`simulated_annealing(func, bounds, max_iter, initial_temp, cooling_rate)` minimizes `func` over box `bounds`. Concept: [[simulated-annealing]].

## Algorithm as coded
1. Random initial solution inside bounds; track best.
2. Each iteration: propose `new = current + U(−1, 1)` per dimension (fixed step size), clip to bounds.
3. `delta = f(new) − f(current)`. Accept if `delta < 0` or `rand() < exp(−delta/T)` (**Metropolis criterion**).
4. Update best if improved; then **geometric cooling** `T ← T · cooling_rate`.
5. Returns best solution, best value, and history of current values (plotted).

## Objective functions
- `objective_function`: **Rastrigin** 2D (used). Global min 0 at origin, many local minima.
- `objective_f2`: **Ackley** (defined but **never used**). See [[benchmark-functions]].
- Parameters: bounds ±5.12, `max_iter = 100000`, `initial_temp = 100`, `cooling_rate = 0.8`.

## Issues
> ⚠️ Errata / design flaw: with `cooling_rate = 0.8`, T = 100·0.8ⁿ. After ~200 iterations T ≈ 100·0.8²⁰⁰ ≈ 4·10⁻¹⁹ and after ~3300 it underflows toward 0 (double min ≈ 1e-308 reached ≈ n≈3300). So >95% of the 100 000 iterations run at essentially zero temperature: acceptance reduces to **greedy hill climbing** with a fixed ±1 step. A cooling rate like 0.999–0.9999 (or fewer iterations) is normal (unverified).
- Also: at T→0, `np.exp(-delta/temperature)` can produce overflow/divide warnings once T underflows to exactly 0 (unverified).
- Fixed step size means it cannot fine-tune near the optimum (best error plateaus ~ step scale); adaptive step or step ∝ T is common (unverified).
- `history` stores *current* not *best* value, so the plot is noisy early then flat.

## Takeaways
Shows the [[exploration-vs-exploitation]] trade-off controlled entirely by temperature. Compare with [[code-gradient-descent]] (gradient-based, single basin) and [[optimization-algorithms-comparison]].
