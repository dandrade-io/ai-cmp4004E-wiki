---
title: Swarm Intelligence
type: concept
tags: [optimization, swarm, bio-inspired]
sources: [raw/slides/04_Optimization.pptx, raw/papers/2 - Particle_swarm_optimization.pdf, raw/papers/3 - dorigo1996.pdf, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Swarm Intelligence

## Intuition
Collective, decentralized behavior of many simple agents yields "intelligent" global results without central control: birds, fish, ants, bees. Slide 16 explicitly calls ABC "a swarm-intelligence approach"; PSO builds on swarm theory (slide 8).

## Key principles
Local interaction, simple rules, indirect communication (**stigmergy**, e.g., pheromone), positive feedback and randomness (stigmergy term itself: unverified; not used in the papers).

**Millonas' five principles of swarm intelligence** (cited by Kennedy & Eberhart, [[paper-particle-swarm-optimization]] PDF pp.5–6): (1) *proximity* — the population performs simple space/time computations; (2) *quality* — responds to quality factors in the environment; (3) *diverse response* — does not commit along excessively narrow channels; (4) *stability* — doesn't change mode every time the environment changes; (5) *adaptability* — changes mode when worth the computational price. PSO satisfies them via pbest/gbest (quality), split between the two (diversity), and changing state only when gbest changes (stability/adaptability).

**Positive feedback / synergy** (Dorigo et al., [[paper-dorigo-ant-system-1996]]): autocatalytic reinforcement of good choices, plus synergy — a colony of cooperating ants (trail communication, α>0) finds optima with less effort than the same number of independent ants (4×4 grid experiment, PDF p.7). Positive feedback in evolutionary algorithms is applied to whole solutions, in AS to *building* solutions (footnote, p.12).

## Members
- [[particle-swarm-optimization]] — shared best positions, continuous spaces.
- [[ant-colony-optimization]] — pheromone trails, graph/combinatorial problems.
- [[artificial-bee-colony]] — division of labor: employed/onlooker/scout.

## Contrast
[[evolutionary-computation]] evolves a population through selection across generations; swarms typically keep the same individuals and move them, sharing information.

## Related
[[metaheuristics]], [[exploration-vs-exploitation]], [[optimization-algorithms-comparison]]; multi-agent notions in [[rational-agents]].

## Exam angles
- Define stigmergy and give an example.
- Compare swarm methods with GAs.

## Eiben & Smith's view
The book treats only PSO among swarm methods, placing it in the EA framework (§6.7); it does **not** cover ACO or ABC (Dorigo is only cited in references). Book: PSO's "mindset is a spatial metaphor of particles" rather than biological genotypes. See [[particle-swarm-optimization]], [[eiben-ch06-popular-ea-variants]].
