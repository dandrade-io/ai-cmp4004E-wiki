---
title: James Kennedy and Russell Eberhart
type: entity
tags: [person, swarm]
sources: [raw/slides/04_Optimization.pptx, raw/papers/2 - Particle_swarm_optimization.pdf]
updated: 2026-09-29
---
# James Kennedy and Russell Eberhart

Authors of **Particle Swarm Optimization** (1995; slide 8 of [[slides-04-optimization]]), a stochastic optimizer inspired by social behavior of birds and fish and swarm theory. Source paper: [[paper-particle-swarm-optimization]].

- **James Kennedy** — affiliation on the paper: Bureau of Labor Statistics, Washington DC; described as a social psychologist. **Russell Eberhart** — Purdue School of Engineering and Technology, Indianapolis; an electrical engineer (paper p.7). Their motive: model human social behavior and optimize with it; the algorithm arose from bird-flock simulations (after Reynolds and Heppner & Grenander) and later applied to neural-network training.
- Signature idea: fly potential solutions through hyperspace, accelerating toward pbest and gbest with `2*rand()` weights.

See [[particle-swarm-optimization]], [[swarm-intelligence]].
