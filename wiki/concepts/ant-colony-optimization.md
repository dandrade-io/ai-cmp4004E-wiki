---
title: Ant Colony Optimization
type: concept
tags: [optimization, swarm, combinatorial]
sources: [raw/slides/04_Optimization.pptx, raw/papers/3 - dorigo1996.pdf]
updated: 2026-09-29
---
# Ant Colony Optimization (ACO)

## Intuition
Metaheuristic by **Marco Dorigo** (with Maniezzo & Colorni) for combinatorial problems — slide says 1996, which is the journal publication date of the *Ant System* paper; the manuscript was first received in **Nov 1991** ([[paper-dorigo-ant-system-1996]] p.1), modeled on ants finding short paths to food (slides 12–13). Ants wander randomly; on finding food they return leaving **pheromone**. Others prefer stronger trails and reinforce them; **evaporation** erases trails on poor paths. See [[marco-dorigo]].

## Mechanism (original Ant System, [[paper-dorigo-ant-system-1996]] pp.3–4)
- Goal: raise pheromone on good solutions, lower it on bad ones (slide 13).
- **Construction:** ant k in town i (tabu list = towns already visited) chooses j among allowed_k with
  `p_ij^k = τ_ij^α · η_ij^β / Σ_{l ∈ allowed_k} τ_il^α · η_il^β`, visibility `η_ij = 1/d_ij` (fixed), τ = trail. α=0 ⇒ stochastic multi-start greedy.
- **Update (ant-cycle), after every full tour:** `τ_ij ← ρ·τ_ij + Σ_k Δτ_ij^k`, with `Δτ_ij^k = Q/L_k` if ant k used edge (i,j), else 0.
- Three variants: **ant-cycle** (global, uses tour length L_k — best), **ant-density** (Q per move) and **ant-quantity** (Q/d_ij per move), the last two using only local info (worse, Table I).
- Loop: init → build m tours → evaluate/keep best → update trails → repeat until NC_MAX cycles or **stagnation** (all ants build the same tour).
- Complexity O(NC·n²·m) ≈ **O(NC·n³)** with m ≈ n.

> ⚠️ Contradiction / notation warning: in the paper **ρ is persistence** (evaporation = 1−ρ, and ρ=0.5 was best). Most later texts (and the earlier version of this page) write `(1−ρ)τ + Δτ` with ρ = evaporation rate. Always check which convention an exam/slide uses.

## Parameters and tuned values (paper)
Number of ants m (best ≈ number of towns n), α (trail weight), β (visibility weight), ρ, Q (negligible effect), NC_MAX, elitist ants e. Best on Oliver30: **α=1, β=5, ρ=0.5, Q=100** (e=8 with elitism). High α ⇒ stagnation; low α ⇒ no communication/greedy-like; good results in the middle band of the α–β map (Fig. 8).

## Results (paper)
Oliver30 TSP best tour 423.741 (integer 420) in < 400 cycles; equals Tabu Search and beats Simulated Annealing under equal time (Table IV: SA avg 459.8 vs AS 420.4); beats 2-opt, ≈ Lin–Kernighan quality but much slower; also applied to ATSP, QAP, job-shop scheduling. Elitist strategy helps up to a point.

## Pros / cons
+ Natural fit for graph problems (TSP, routing), positive feedback + distributed memory. − Slower convergence, parameter-sensitive, mainly discrete.

## Exploration vs exploitation
Evaporation and randomness = exploration; reinforcement = exploitation. The paper describes the greedy heuristic (visibility) guiding early search and losing importance as trail accumulates; the standard deviation of tour lengths never drops to 0 (population keeps searching), while average node branching shrinks as poor edges lose trail. **Stagnation** = all ants follow one tour (branching → 2). See [[exploration-vs-exploitation]].

## Related
[[swarm-intelligence]], [[particle-swarm-optimization]], [[artificial-bee-colony]], [[metaheuristics]], [[optimization-algorithms-comparison]].

## Exam angles
- Why is evaporation necessary? (avoids early lock-in to a suboptimal path)
- Why does ant-cycle beat ant-density/ant-quantity? (uses global tour quality, not local step info)
- What happens with α = 0? with very large α? (greedy multi-start / stagnation)
- Apply the probability rule to a small graph.
