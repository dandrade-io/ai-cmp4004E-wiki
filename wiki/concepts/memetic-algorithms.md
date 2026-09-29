---
title: Memetic Algorithms
type: concept
tags: [evolutionary, hybrid]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Memetic algorithms (MA)

EA + **local search**/problem knowledge (Moscato's term; book Ch.10, pp.167–171). Motivation: EAs quickly find good *regions* but fine-tune slowly (OneMax: last bits found only by chance) — add a bit-flip hill-climber; NFL says knowledge must be added for specific problems; "memes" (Dawkins) = units of cultural transmission that transform a solution (learning phase).

## Local search (Fig. 10.2)
Components: **pivot rule** (steepest vs greedy/first ascent), **depth** (1 step … to local optimum), **neighbourhood** function. Hybrid points: intelligent initialisation, intelligent crossover/mutation, local search on offspring, genotype→phenotype mapping. **Lamarckian** (write the improved solution back to the genotype) vs **Baldwinian** (only use its fitness). *Adaptive* MAs let memes be selected too.

Contrast: heuristic initialisation is often not worth it because EAs reach that level in a few generations (anytime behaviour, p.43).

Related: [[no-free-lunch-theorem]], [[constraint-handling-in-ea]] (repair = local search), [[simulated-annealing]], [[optimization-landscape]] (hill climbing), [[genetic-algorithms]].
