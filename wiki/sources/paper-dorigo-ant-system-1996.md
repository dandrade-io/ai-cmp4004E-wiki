---
title: "Paper: Dorigo, Maniezzo & Colorni (1996), Ant System"
type: source
tags: [paper, aco, swarm, tsp, combinatorial]
sources: [raw/papers/3 - dorigo1996.pdf]
updated: 2026-09-29
---
# Dorigo, Maniezzo & Colorni (1996) — "Ant System: Optimization by a Colony of Cooperating Agents"

**Bibliographic info:** Marco Dorigo, Vittorio Maniezzo, Alberto Colorni. *IEEE Transactions on Systems, Man, and Cybernetics — Part B: Cybernetics*, vol. 26, no. 1, Feb 1996, pp. 29–41 (13 PDF pages; PDF p.1 = journal p.29). Manuscript first received **Nov 1991**, revised through 1994 — so the ideas predate 1996. Source: `raw/papers/3 - dorigo1996.pdf`. Equations (2)–(4) are partly garbled in the extraction; the forms below follow the paper's text and the standard formulas.

## Thesis
A new general-purpose heuristic, the **Ant System (AS)**, for stochastic combinatorial optimization built on three ingredients (abstract, p.1): **positive feedback** (rapid discovery of good solutions), **distributed computation** (avoids premature convergence), and a **constructive greedy heuristic** (good solutions early on).

## Biological motivation (pp.1–2)
Real ants lay pheromone; others follow strong trails → autocatalytic loop. Bridge/obstacle example (Fig. 1–2): with 30 new ants per step, trail on the short path is double (30 vs 15), so expected split is 20 vs 10, and the colony quickly commits to the shorter path. Artificial ants differ: they have **memory** (tabu list), are **not blind** (use visibility), and live in **discrete time**.

## The algorithm (pp.3–4)
Setup on the TSP: n towns, distance d_ij, m ants, trail τ_ij(t), visibility **η_ij = 1/d_ij** (fixed).

- **Transition rule (eq. 4):** ant k in town i goes to j ∈ allowed_k (= towns not in its tabu list) with probability
  `p_ij^k(t) = [τ_ij(t)]^α · [η_ij]^β / Σ_{l∈allowed_k} [τ_il(t)]^α · [η_il]^β`.
  α weighs trail (autocatalysis), β weighs visibility (greedy). **α = 0 ⇒ stochastic greedy with multiple starts** (p.3).
- **Trail update (eq. 1–3), every n iterations (one *cycle*, when every ant has finished a tour):**
  `τ_ij(t+n) = ρ·τ_ij(t) + Δτ_ij`, `Δτ_ij = Σ_k Δτ_ij^k`, `Δτ_ij^k = Q/L_k` if ant k used edge (i,j) else 0 (L_k = tour length).
  **Here ρ is trail *persistence*: (1−ρ) is evaporation, 0 ≤ ρ < 1** (p.4).
- **Ant-cycle algorithm** (pseudocode p.4): init τ = small constant c; place ants; build tours step by step using eq. 4 and tabu lists; compute L_k, keep the best tour; update trails; repeat until NC_MAX cycles or **stagnation** (all ants make the same tour).
- **Complexity:** O(NC·n²·m); since the best m ≈ n empirically, **O(NC·n³)** (p.4).
- **Variants:** *ant-density* (lay Q per move, independent of d_ij) and *ant-quantity* (lay Q/d_ij per move) update trail at every step using **local** info; *ant-cycle* uses **global** info (tour quality) and performs best (Table I).

## Experiments and results
- **Parameters** (p.4): default α=1, β=1, ρ=0.5, Q=100; best found **α=1, β=5, ρ=0.5, Q=100** (Q has negligible effect). ρ=0.5 means ants must forget part of the past to exploit new global information (p.5).
- **Oliver30 TSP** (30 cities): best tour **423.741** (integer 420), vs 424.635 from a GA in the literature; found in < 400 cycles (342 in one run), ~100 cycles to get under 430; never entered stagnation with good parameters. Standard deviation of tour lengths never reaches 0; average node branching shrinks as bad edges lose trail (Figs. 3–7).
- **α–β map** (Fig. 8): high α ⇒ stagnation / multi-greedy-like bad solutions; low α ⇒ bad solutions without stagnation; good solutions in the middle region.
- **Synergy** (pp.7–8): 4×4 grid (optimum 160): communication (α=1) beats no communication (α=0); best number of ants ≈ number of cities. Distributing ants over towns beats starting them all in one town. Grids up to 8×8 (64 cities): optimum always found (Table II).
- **Elitist strategy** (p.8): extra reinforcement e·Q/L* on the best-so-far tour helps up to an optimum e (e=8 used); too many elitist ants forces early exploitation of suboptimal tours.
- **vs TSP heuristics (p.8–9):** beats 2-opt, comparable to Lin–Kernighan on Oliver30, but "requires a much longer computational time" than special-purpose heuristics.
- **vs general-purpose (Table IV, p.9):** same time (1 h on a 386 PC): AS 420 best / 420.4 avg, Tabu Search 420 / 420.6, **Simulated Annealing 422 / 459.8 (σ 25.1)** — AS ≈ TS > SA.
- **Generality (pp.9–11):** ATSP (RY48P): avg 14,899, 3.3 % above optimum. QAP (Nugent, Elshafei, Krarup): within 5 % of best known; AS + non-deterministic hill climbing usually hits best known (Table V). JSP (10×10, 10×15): within 10 % of optimum, using a job-graph with a dummy node 0 and problem-specific allowed sets.

## Discussion (pp.11–12)
Trail acts as a "space deformation" of path costs; the transition matrix converges to near stationary. A lone greedy ant gives good early moves but forced bad final ones; many ants reinforce good *parts* of tours. Contributions: positive feedback as search tool, synergy of cooperating agents, generality across problems. Related to natural algorithms (GA, SA, evolutionary strategies, neural nets).

## Limitations (by the authors)
Outperformed by specialized algorithms on some problems; much slower than tailored TSP heuristics; no mathematical analysis yet ("not yet developed a mathematical analysis", p.4), so parameters are chosen empirically; only small instances (≤75 cities, Eilon50/75 didn't reach best known).

## Relation to the slides
Slide 12–13 describe the biology and pheromone reinforcement/evaporation; this paper supplies the actual equations, parameters and results. The paper introduces **Ant System**; the name "Ant Colony Optimization" (ACO) for the wider metaheuristic came later (unverified).

Pages updated: [[ant-colony-optimization]], [[marco-dorigo]], [[swarm-intelligence]], [[exploration-vs-exploitation]], [[simulated-annealing]] (comparison data).
