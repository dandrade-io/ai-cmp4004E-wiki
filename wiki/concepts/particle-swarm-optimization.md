---
title: Particle Swarm Optimization
type: concept
tags: [optimization, swarm]
sources: [raw/slides/04_Optimization.pptx, raw/papers/2 - Particle_swarm_optimization.pdf, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Particle Swarm Optimization (PSO)

## Intuition
Stochastic optimizer by **Kennedy & Eberhart (1995)**, inspired by flocks of birds and schools of fish. A swarm of particles flies through continuous space, each pulled toward its own best find and the swarm's best find (slides 8–10). See [[kennedy-eberhart]].

## State per particle (slide 9)
position x_t, velocity v_t, personal best p_best. Swarm keeps global best g_best.

## Update rule in the original paper ([[paper-particle-swarm-optimization]], PDF p.5)
```
v[i][d] = v[i][d] + 2*rand()*(pbest[i][d] - x[i][d])
                  + 2*rand()*(pbest[gbest][d] - x[i][d])
x[i][d] = x[i][d] + v[i][d]     # implied (not printed in the extracted text)
update pbest, gbest
```
The factor 2·rand() has mean 1, so particles "overfly" their targets about half the time. The previous velocity acts as **momentum**; removing it made the algorithm "quite ineffective at finding global optima".

## Textbook form (Eiben & Smith §6.7, p.113 — later refinement)
```
v ← w·v + c1·φ1·(p_best − x) + c2·φ2·(g_best − x)     φ1, φ2 ~ U[0,1]
```
In the book: v' = w·v + φ₁U₁(b − x) + φ₂U₂(c − x), x' = x + v', b' = x' if f(x') < f(b) (minimisation), where **w = inertia**, **φ₁ = personal/cognitive learning rate**, **φ₂ = social learning rate**, and **U₁, U₂ are uniform random factors per coordinate**. The particle is the triple ⟨x, v, b⟩; c is the swarm's global best. Book view: PSO fits the EA framework (no crossover; mutation = adding velocity), similar to ES with the perturbation vector stored per individual. The inertia weight and separate learning rates are absent from the 1995 paper.

> ⚠️ Contradiction (slide vs book): slide 9 says φ₁, φ₂ are *random variables* uniform on [0,1]; the book has φ_i as *weights* and separate U_i as the random draws.

> ⚠️ Contradiction: slide 9 presents φ1, φ2 as parameters with x_t, v_t; the paper's final version has no tunable coefficients except the constant 2. Don't cite `w` as part of Kennedy & Eberhart's original algorithm.

## How the paper arrived at it
Flock simulation (nearest-neighbor velocity matching + "craziness") → "cornfield vector" with pbest/gbest → dropped craziness and velocity matching (swarm rather than flock) → velocity change proportional to distance from pbest/gbest → simplified constant 2. Roughly equal pull to pbest and gbest works best: high pbest weight → isolated wandering; high gbest weight → premature rush into local minima (PDF p.4). pbest = "simple nostalgia" (memory), gbest = group norm.

## Parameters
Swarm size (paper: 15–30 agents in demos, 20 for XOR net), velocity clamp, iterations; in textbook forms also inertia w, cognitive c1, social c2.

## Reported results (paper, pp.4–6)
Trained a 13-parameter XOR net to error < 0.05 in ~30.7 iterations (20 agents); matched backpropagation on Iris (avg 284 epochs); 92 % vs 89 % (backprop) on EEG spike classification; found the global optimum of the multimodal **Schaffer f6** every run.

## Exploration vs exploitation (slide 10)
Random terms + momentum ⇒ overshooting/exploration; strong pull to g_best ⇒ exploitation and possible premature convergence. The authors credit success to particles "hurtling past their target" and tie it to Holland's optimum allocation of trials (paper PDF p.7). See [[exploration-vs-exploitation]].

## Pros / cons
+ Few parameters, easy to code, no gradient, good for continuous problems. − Can converge prematurely to a local optimum; less natural for discrete problems.

## Related
Source paper: [[paper-particle-swarm-optimization]]. [[swarm-intelligence]], [[ant-colony-optimization]], [[artificial-bee-colony]], [[metaheuristics]], [[optimization-algorithms-comparison]].

## Exam angles
- Do one update step numerically given x, v, p_best, g_best and φ values.
- Roles of p_best (cognitive) vs g_best (social).

**Worked step (book form):** x = 2, v = 1, b = 3, c = 5, w = 0.7, φ₁ = φ₂ = 2, U₁ = 0.5, U₂ = 0.25 ⇒ v' = 0.7 + 2·0.5·(3−2) + 2·0.25·(5−2) = 0.7 + 1 + 1.5 = 3.2; x' = 5.2. Compare with [[differential-evolution]] (both from 1995, both vector-difference based). See [[eiben-ch06-popular-ea-variants]].
