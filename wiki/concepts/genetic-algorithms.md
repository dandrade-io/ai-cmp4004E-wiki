---
title: Genetic Algorithms
type: concept
tags: [optimization, evolutionary, genetic]
sources: [raw/slides/04_Optimization.pptx, raw/papers/Holland-GeneticAlgorithms-1992.pdf, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
paper: "[[paper-holland-genetic-algorithms]]"
updated: 2026-09-29
---
# Genetic Algorithms (GA)

## Intuition
Apply natural selection to computing: **variation, selection, heredity** (slide 5). Keep a population of candidate solutions, let fitter ones reproduce more, and recombine/mutate them.

## Representation (slide 5–6)
- **Individual / chromosome:** bit string, e.g. a decimal number encoded in binary; represents a point in the solution space.
- **Fitness function:** evaluates each individual (maximize or minimize).
- **Reproduction:** [[crossover-and-mutation|crossover]]; **variation:** bit-flip mutation with some probability.

## Pseudocode (standard; Holland's version in [[paper-holland-genetic-algorithms]] p.3–4)
```
P ← random population of N bit strings
repeat:
    compute fitness of each
    select parents (fitter strings mate; roulette-wheel FPS in the Simple GA, tournament in practice — [[selection-mechanisms]])
    offspring ← crossover(parents, p_c); mutate(offspring, p_m)
    offspring replace the LOW-fitness strings (population size constant)
until generations exhausted or fitness good enough
```
Holland: "High-quality strings mate; low-quality ones perish"; offspring do not replace their parents but the weakest strings (PDF p.4).

## Parameters
Population size, crossover rate p_c (~0.6–0.8, Eiben & Smith p.100), mutation rate p_m (Holland quotes roughly **1 in 10,000 symbols**, PDF p.4; book recommendation between **1/l and 1/μ**, p.100), selection pressure, elitism, encoding.

## Why it works: schemata and implicit parallelism (Holland 1992)
- A bit string belongs to many **regions** (schemata) at once, e.g. `11011001` ∈ `11******`, `1*******`, `**0**00*`. A few thousand strings therefore sample vastly more regions — **implicit parallelism** (PDF p.4).
- The number of strings in a region grows in proportion to that region's estimated average fitness.
- Crossover can pull an offspring out of its parents' region; **compact building blocks** (defining bits close together) survive best. Example: `10****` leaves its region with prob. 1/5 in a 6-gene string, 1/999 in a 1,000-gene string.
- Handles **nonlinear** gene interactions (a block like `01****` can be fit even if `0*****` and `*1****` are not) — hill climbing cannot.
- Best at finding promising *regions*; for local refinement, hybridize with standard methods (p.8).
- Encoding programs: **classifier systems** (rules as bit strings) let GAs evolve arbitrary programs; applications include the iterated Prisoner's Dilemma (rediscovered tit for tat), pipeline control, network design, jet-turbine design (pp.5–8).

## Pros / cons
+ Global search, no gradient, works on discrete spaces. − Needs good encoding, many fitness evaluations, premature convergence if diversity lost.

## Related
[[evolutionary-computation]], [[john-holland]], [[exploration-vs-exploitation]] (crossover/mutation vs selection), [[metaheuristics]], [[optimization-algorithms-comparison]].

> ⚠️ Contradiction (resolved): slide 5 says "John Holland – 1992" while slide 2 says 1975. The raw file is Holland's **1992 *Scientific American* article**; he says the GA was developed in the **mid-1960s**, and the founding book *Adaptation in Natural and Artificial Systems* is 1975 (1992 = MIT Press edition). So 1975 (book) is the right citation for the algorithm's origin; 1992 is just this popular article. See [[paper-holland-genetic-algorithms]], [[slides-04-optimization]].

## Exam angles
- Given two parents and a crossover point, produce offspring.
- Role of mutation (restores lost diversity) vs crossover (combines building blocks).
- What is premature convergence and how to mitigate?

## The Simple (canonical) GA — Eiben & Smith §6.1, pp.99–100
| Component | Simple GA |
|---|---|
| Representation | bit strings |
| Recombination | 1-point crossover (probability p_c per pair) |
| Mutation | bit flip, independent p_m per bit |
| Parent selection | fitness-proportional (roulette wheel) |
| Survivor selection | generational (whole population replaced) |
Workflow: fill an intermediate population of μ by parent selection (duplicates allowed), shuffle, cross consecutive pairs with p_c, mutate each bit with p_m, replace the old population.

**Known flaws / modern practice:** no elitism; roulette wheel replaced by SUS; usually **tournament** selection (rank-based, simple, pressure tuned by k); uniform crossover to avoid positional bias; non-binary representations where natural (using bit strings for numbers is "usually a mistake"); self-adapting mutation rates; "linkage learning" → [[estimation-of-distribution-algorithms]]. The SGA remains a teaching and benchmarking baseline.

**By-hand cycle (book §3.3, x² on 0–31, pop 4):** initial x = 13, 24, 8, 19 (avg fitness 293, max 576) → FPS → one-point crossover (e.g. 01101 × 11000 cut after bit 4 → 01100, 11001) → mutation → avg fitness 588.5, max 729. Full tables in [[selection-mechanisms]] and [[crossover-and-mutation]].

**Origins:** the book says GAs were "initially conceived by Holland as a means of studying adaptive behaviour" (title of his 1975 book), and have "largely (if perhaps mistakenly) been considered function optimisation methods", helped by Goldberg's book and De Jong's thesis (p.99) — consistent with [[paper-holland-genetic-algorithms]].

See also [[eiben-ch06-popular-ea-variants]], [[survivor-selection-and-elitism]], [[parameter-control]], [[diversity-and-niching]], [[no-free-lunch-theorem]].
