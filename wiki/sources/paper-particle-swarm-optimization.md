---
title: "Paper: Kennedy & Eberhart (1995), Particle Swarm Optimization"
type: source
tags: [paper, pso, swarm]
sources: [raw/papers/2 - Particle_swarm_optimization.pdf]
updated: 2026-09-29
---
# Kennedy & Eberhart (1995) — "Particle Swarm Optimization"

**Bibliographic info:** James Kennedy (Bureau of Labor Statistics, Washington DC) and Russell Eberhart (Purdue School of Engineering and Technology, Indianapolis). IEEE, 1995 (footer "0-7803-2768-3/95", pp. 1942–1948; the venue is not named in the text — this is the ICNN'95 proceedings paper, unverified). 7 PDF pages. Source: `raw/papers/2 - Particle_swarm_optimization.pdf`. Portions adapted from the book *Computational Intelligence PC Tools* (Academic Press, 1996).

## Thesis
A very simple method for optimizing **continuous nonlinear functions**, discovered by simulating a simplified social model (bird flocking); the algorithm "stands without metaphorical support" (PDF p.1). It is "a few lines of code," needs only primitive math operators, and is cheap in memory and speed.

## Development story (the paper's real content)
1. **Nearest-neighbor velocity matching + "craziness"** (p.2): agents copy the velocity of their nearest neighbor; a random perturbation ("craziness") stops the flock settling on one direction.
2. **Cornfield vector** (p.3): agents evaluate `Eval = sqrt((presentx−100)² + (presenty−100)²)` (zero at (100,100)); each remembers **pbest** (best value + position); the flock's best is **gbest**. Original inequality-based rule: if x > pbestx then `vx -= rand()*p_increment`, else `vx += rand()*p_increment` (same for y and for gbest with `g_increment`). Flocks of 15–30 agents got "sucked" into the cornfield when increments were high, and swirled/landed when low.
3. **Eliminating ancillary variables** (p.4): craziness and velocity matching were removed (search got slightly faster; flock → swarm). pbest and gbest are both necessary: pbest ≈ autobiographical memory ("simple nostalgia"), gbest ≈ publicized group norm. High p_increment relative to g_increment → isolated wandering; high g_increment → premature rush to local minima; roughly equal values work best.
4. **Multidimensional search** (p.4): positions/velocities become D×N matrices. Trained a 2-3-1 XOR neural net (**13 parameters**): reached error < 0.05 in an average of **30.7 iterations with 20 agents**.
5. **Acceleration by distance** (p.4–5): velocity adjusted proportionally to the difference: `vx[][] = vx[][] + rand()*p_increment*(pbestx[][] − presentx[][])`.
6. **Current simplified version** (p.5): the p/g increments are dropped and the random factor is multiplied by 2 (mean 1, so agents "overfly" the target about half the time):

```
v[i][d] = v[i][d]
        + 2*rand() * (pbest[i][d]        - x[i][d])
        + 2*rand() * (pbest[gbest][d]    - x[i][d])
(x[i][d] += v[i][d]  — implied, not printed)
```

7. **Other experiments (p.5):** collapsing both terms into the midpoint of pbest and gbest → converges to that point even if not optimal (the two stochastic "kicks" are necessary); "explorers vs settlers" gave no improvement; **removing momentum** (dropping the `v[i][d] +` term) was "quite ineffective at finding global optima".

## Swarm concept (pp.5–6)
Uses Millonas' five principles of swarm intelligence: proximity, quality, diverse response, stability, adaptability. "Particle" chosen as a compromise (mass-less points vs. things with velocity/acceleration).

## Results (p.6)
- NN weight training matched backpropagation (XOR; Fisher Iris — avg **284 epochs** over ten sessions).
- EEG spike data: backprop **89 %** vs PSO **92 %** test accuracy (informal, suggests better generalization).
- **Schaffer f6** (Davis's GA handbook benchmark): global optimum found every run; evaluations comparable to elementary GAs.

## Discussion / limitations
- Placed between GAs and evolutionary programming; pbest/gbest adjustment "conceptually similar to crossover"; unique feature is *flying* solutions through hyperspace with momentum (p.6–7).
- Success attributed to overshooting ("hurtle past their target") and Holland's "optimum allocation of trials" balance (p.7); see [[exploration-vs-exploitation]] and [[paper-holland-genetic-algorithms]].
- Evidence is small-scale and informal ("much further research remains"); the constant 2 is not justified beyond "mean of 1".

## Relation to the slides
> ⚠️ Contradiction: slide 9 writes parameters φ1, φ2 ~ U[0,1] and keeps x_t, v_t; the paper has **no inertia weight** and no φ notation — it uses `2*rand()`. Inertia weight `w` and the c1/c2 coefficients in many textbooks are later refinements (unverified). The paper's velocity term *is* the "momentum" (the previous v). Position update `x += v` is not printed in the extracted text.

Pages updated: [[particle-swarm-optimization]], [[swarm-intelligence]], [[exploration-vs-exploitation]], [[kennedy-eberhart]].
