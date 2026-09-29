---
title: "Slides 04 — Optimization and Biology-Inspired Agents"
type: source
tags: [optimization, evolutionary, swarm]
sources: [raw/slides/04_Optimization.pptx]
updated: 2026-09-29
---
# Slides 04 — Optimization and Biology-Inspired Agents

Lecture deck on optimization with bio-inspired metaheuristics. Course-outline item 9 ("Optimization and bio-inspired algorithms").

## Structure and takeaways
- **Slide 2 — Evolutionary computation origins:** Fogel (1960, evolving finite-state machines), Rechenberg & Schwefel (1970, evolution strategies), Holland (1975, genetic algorithms). See [[evolutionary-computation]], [[lawrence-fogel]], [[john-holland]].
- **Slide 3 — Landscape framing:** global vs local maxima/minima; treat each point of the search space as an individual with a fitness. See [[optimization-landscape]]. Vocabulary: adaptation, heredity, natural selection.
- **Slides 5–6 — Genetic algorithms:** bit-string individuals, fitness function, crossover (single/two/k-point), bit-flip mutation. See [[genetic-algorithms]], [[crossover-and-mutation]].
- **Slides 8–10 — PSO (Kennedy & Eberhart, 1995):** particles with position, velocity, p_best, and swarm g_best; φ1, φ2 ~ U[0,1]; exploration vs exploitation. See [[particle-swarm-optimization]], [[kennedy-eberhart]].
- **Slides 12–15 — ACO (Dorigo, 1996):** pheromone trails, reinforcement and evaporation. See [[ant-colony-optimization]], [[marco-dorigo]].
- **Slides 16–18 — ABC (Karaboga, 2007):** employed, onlooker and scout bees; parameters BN/SN, limit, MCN. See [[artificial-bee-colony]].
- Cross-cutting: [[swarm-intelligence]], [[exploration-vs-exploitation]], [[metaheuristics]].

## Related code
[[code-gradient-descent]] and [[code-simulated-annealing]] (raw/code) accompany this unit; see [[gradient-descent]], [[simulated-annealing]], [[benchmark-functions]].

## Errata / notes
> ⚠️ Errata: slide 5 credits "John Holland - 1992" while slide 2 says 1975. 1975 is the original book; 1992 is likely the MIT Press reprint of *Adaptation in Natural and Artificial Systems*, matching `raw/papers/Holland-GeneticAlgorithms-1992.pdf` (unverified).

Slides 7, 11, 14, 15 and 19 contain only images/equations not extracted as text (e.g., the PSO update rule, ACO probability rule, ABC food-position equation); the wiki pages give the standard forms (unverified against the slide images).

Comparison: [[optimization-algorithms-comparison]].
