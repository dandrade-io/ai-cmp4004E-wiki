---
title: Eiben & Smith Ch.1–3 — Problems, Origins, What Is an EA
type: source
tags: [book, evolutionary, optimization]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Eiben & Smith, Ch. 1–3 (book pp. 1–48)

Book: [[eiben-smith]]. Printed page numbers below (PDF page = printed + 14 in this file). *Ch.1 (problem types, NP) was only skimmed via the TOC/Ch.13 recap; the rest was read.*

## Ch.1 Problems to be solved (skimmed; recapped in Ch.13 p.203)
Problem types: **optimisation** (find input maximising output), **modelling** (find model matching data), **simulation** (what-if). With/without constraints: *Free Optimisation Problem (FOP)* = fitness only; *Constraint Satisfaction Problem (CSP)* = constraints only; *Constrained Optimisation Problem (COP)* = both. See [[constraint-handling-in-ea]], [[constraint-satisfaction-problems]].

## Ch.2 Origins (pp. 13–24)
- Main metaphor: environment ↔ problem, individual ↔ candidate solution, fitness ↔ quality (p.13).
- Darwinian evolution + genetics: **genotype** (code) vs **phenotype** (traits). Variation (mutation, recombination) acts on genotypes; selection acts on phenotypes (p.19). Lamarckian inheritance is refuted biologically (p.19), yet appears in [[memetic-algorithms]].
- Generate-and-test view of evolution (p.20).
- Why EC: (1) nature's most powerful problem solver besides the brain; (2) need for robust general solvers as problems grow; (3) curiosity (simulating evolution). Examples: university timetabling, satellite-boom design (asymmetric evolved design 20,000 % better than regular), stock-trader rule models via classifier systems.

## Ch.3 What is an evolutionary algorithm? (pp. 25–48)
- **Generic EA scheme** (Fig. 3.1, p.26): INITIALISE → EVALUATE → REPEAT {SELECT parents, RECOMBINE, MUTATE, EVALUATE, SELECT survivors} UNTIL termination. See [[evolutionary-computation]].
- Two forces: **variation** (diversity/novelty) and **selection** (raises mean quality). Population-based, stochastic, usually with recombination.
- Components (p.28): representation, evaluation (fitness) function, population, parent selection, variation operators, survivor selection; plus initialisation and termination. Termination: CPU time, evaluation budget, stagnation, diversity below threshold (p.34).
- *Representation*: phenotype→genotype mapping (encoding) and inverse (decoding); e.g. 18 ↔ 10010, fitness x² = 324 (pp.29–30).
- Parent selection is typically **probabilistic** (weak individuals keep a small chance, else too greedy); survivor selection is often **deterministic** (pp.31–33). See [[selection-mechanisms]], [[survivor-selection-and-elitism]].
- **Cycle by hand** (Goldberg's x² on 0–31, pp.34–36): [[selection-mechanisms]] worked example.
- **8-queens EA** (permutation genotype, swap mutation, "cut-and-crossfill" crossover; Table 3.4, pp.36–39) and **0–1 knapsack EA** (binary, decoder, one-point crossover 70 %, pm = 1/n, tournament of 2, generational, pop 500; Table 3.5, pp.39–41). Compare with [[n-queens-prolog]] (constructive/backtracking vs evolutionary).
- **Behaviour** (pp.41–44): population climbs hills; *exploration vs exploitation* and *premature convergence*; **anytime behaviour** (rapid early progress, then flattening) ⇒ heuristic initialisation and very long runs are often not worth it. Goldberg's 1980s "EAs are uniformly good" picture is superseded by [[no-free-lunch-theorem]] and hybrids ([[memetic-algorithms]]).
- Natural vs artificial evolution (Table 3.6, p.45): fitness a priori vs a posteriori, centralised/synchronous vs parallel, constant vs variable population.
- EC vs global optimisation (pp.46–48): exhaustive enumeration, branch-and-bound, local search/hill climbing, tabu search, [[simulated-annealing]]; EAs use a population-induced non-uniform sampling distribution and diversity to escape local optima. TSP has n!/2 tours (p.46).

## Derived pages
[[evolutionary-computation]], [[selection-mechanisms]], [[survivor-selection-and-elitism]], [[genetic-algorithms]], [[exploration-vs-exploitation]], [[metaheuristics]], [[no-free-lunch-theorem]].

## Slide comparison
> ⚠️ Contradiction: [[slides-04-optimization]] slide 2 credits Fogel (1960) as "creator" of EC and dates evolution strategies to 1970. The book says ES were **invented in the early 1960s** by Rechenberg & Schwefel and EP by Fogel et al. in the 1960s (pp.101, 103). The slide's 1970 is more likely the date of ES publications/multi-membered ES (book: "in the 1970s multi-membered ES", p.101).
