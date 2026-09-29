---
title: "Paper: Holland (1992), Genetic Algorithms (Scientific American)"
type: source
tags: [paper, genetic-algorithms, evolutionary, classifier-systems]
sources: [raw/papers/Holland-GeneticAlgorithms-1992.pdf]
updated: 2026-09-29
---
# Holland (1992) — "Genetic Algorithms"

**Bibliographic info:** John H. Holland, "Genetic Algorithms: Computer programs that 'evolve' in ways that resemble natural selection can solve complex problems even their creators do not fully understand", *Scientific American* 267(1), July 1992, pp. 66–73 (JSTOR copy; PDF pp. 1–9, where PDF p.2 = magazine p.66; the last PDF page is an unrelated advert). Source: `raw/papers/Holland-GeneticAlgorithms-1992.pdf`. Text extraction is mostly legible; some figure text and numbers are garbled (noted below).

> ⚠️ Contradiction/Resolution (dating): this file is a **1992 popular-science magazine article**, *not* the 1975 book. Holland says he developed the GA "by the mid-1960s" (PDF p.2), and lists *Adaptation in Natural and Artificial Systems* (MIT Press, **1992** edition) as further reading (PDF p.8); the 1975 date is the original book edition (the Dorigo paper cites it as Univ. of Michigan Press 1975, see [[paper-dorigo-ant-system-1996]] ref. [23]). So slide 2's "Holland 1975" (the book) and slide 5's "Holland – 1992" (this article / MIT reprint) are both citing real things; neither is the invention date. See [[slides-04-optimization]].

## Thesis
Programs that evolve via **selection + recombination (mating) + mutation** can solve problems whose structure nobody fully understands, and GAs explore a far larger range of solutions than conventional programs (PDF p.2). Recombination (crossover), not mutation alone, is the key ingredient (p.2).

## Key ideas
- **History (p.2):** early 1950s–60s evolutionary attempts relied on mutation only and fared poorly; Bremermann added mating by *summing* parent genes (limited to additive traits); Holland developed the GA by mid-1960s and then the **classifier system** (rules as bit strings with a "don't care" symbol) to represent any program.
- **Cycle (pp.3–4):** start with random bit strings → rate each by fitness → high-quality strings mate, low-quality ones perish → repeat. Fitness may be profit, game payoff, error rate, etc.
- **Search landscape (p.3):** strings = points on a landscape; *hill climbing* gets stuck on complex multi-peak landscapes; chess example: ~10^60 strategies (10 alternatives × 30 moves per side).
- **Crossover (p.4):** pick a random point, swap the tails to produce two offspring; offspring replace *low-fitness* strings so population size is constant.
- **Mutation (p.4):** roughly **1 in 10,000 symbols** flips; mutation alone does not advance search but insures against a uniform population that cannot evolve further.
- **Implicit parallelism (p.4–5):** a string like 11011001 belongs to many "regions" (schemata such as `11******`, `**0**00*`); a population of a few thousand strings implicitly samples vastly more regions; the number of strings in a region grows in proportion to its estimated average fitness.
- **Compact building blocks (p.4):** blocks whose defining bits are close together survive crossover intact. Example: region `10****` in a 6-gene string leaves its parents' region with prob. 1 in 5 (crossover at position 2); in a 1,000-gene string only 1 in 999.
- **Inversion (pp.4–5):** biological operator that rearranges genes so building blocks become more compact.
- **Nonlinearity (p.5):** GAs handle non-additive interactions between genes (regions like `01****` can be above average even if `0*****` and `*1****` are not).
- **Exploration vs exploitation (p.5):** "striking a balance between exploration and exploitation" is a classic problem; crossover both tests building blocks in new contexts and can break them. See [[exploration-vs-exploitation]].

## Applications and experiments
- **Iterated Prisoner's Dilemma (pp.5–6):** Axelrod & Forrest encoded a strategy as a bit string with one gene per history of the last three plays (4 outcomes per round → 4³ = 64 histories; the extracted text shows "54"/"264" — garbled, unverified). Fitness = average payoff. The GA quickly discovered **tit for tat**, then a further strategy that exploits "bluffable" opponents. Payoff table (p.71): C/C 3/3, C/D 0/5, D/C 5/0, D/D 0/0.
- **Classifier systems with rule competition (pp.6–7):** rules compete, winners are strengthened/weakened by outcome; yields **default hierarchies** and credit assignment over long delays.
- **Gas pipeline control** (Goldberg), **communications network design** (Davis), **jet turbine design** at GE/RPI (p.8): >100 variables, search space >10^387, ~50 constraints, 30 s per simulation; manual design ≈ 8 weeks; expert system < 1 day (2× improvement); expert system + GA seeding ≈ 2 days (3× improvement).
- Classifier systems of up to 8,000 rules; economic-agent simulations at the Santa Fe Institute (p.8).

## Limitations noted by the author
- Simple GAs are best at locating promising regions; "if a partial solution can be improved further by making small changes in a few variables, it is best to augment the genetic algorithm with other, more standard methods" (p.8), i.e. hybrid with local search.
- Biological populations are far larger than what GAs run; massively parallel machines suit GAs since operations act on one or two strings (p.8).

## Relation to the course slides
Confirms the slide 5–6 picture (bit-string chromosomes, fitness, single-point crossover, bit-flip mutation) and adds the theory the slides omit (schemata / implicit parallelism, building blocks). The slides say nothing about classifier systems or inversion. Pages updated: [[genetic-algorithms]], [[crossover-and-mutation]], [[exploration-vs-exploitation]], [[evolutionary-computation]], [[john-holland]].
