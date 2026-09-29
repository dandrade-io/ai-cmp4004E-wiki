---
title: Evolutionary Computation
type: concept
tags: [optimization, evolutionary]
sources: [raw/slides/04_Optimization.pptx, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Evolutionary Computation (EC)

## Intuition
Use the mechanisms of biological evolution — **adaptation, heredity, natural selection** — to solve (combinatorial) optimization problems. A population of candidate solutions is repeatedly varied and filtered by fitness (source: [[slides-04-optimization]], slides 2–3).

## History (slide 2)
- **Fogel, 1960:** evolving finite-state machines (evolutionary programming) — [[lawrence-fogel]].
- **Rechenberg & Schwefel, 1970:** evolution strategies for parameter optimization.
- **Holland, 1975:** genetic algorithms — [[john-holland]].

## Generic loop (Eiben & Smith, Fig. 3.1, p.26)
```
INITIALISE population with random candidate solutions
EVALUATE each candidate
REPEAT UNTIL termination:
    1 SELECT parents   2 RECOMBINE pairs   3 MUTATE offspring
    4 EVALUATE new candidates   5 SELECT survivors for the next generation
```
Families: genetic algorithms ([[genetic-algorithms]]), evolution strategies, evolutionary programming, genetic programming. Swarm methods ([[swarm-intelligence]]) are related but not strictly evolutionary.

## Pros / cons
+ Gradient-free, global, parallel, handles discrete or non-differentiable problems. − Many evaluations, parameter tuning, no optimality guarantee.

## Related
[[crossover-and-mutation]], [[metaheuristics]], [[exploration-vs-exploitation]], [[eiben-smith]] (textbook, ingested: [[eiben-ch01-03-problems-origins-and-eas]]).

## Exam angles
- Name the founders and years; match each to their algorithm.
- Explain selection/variation/heredity in optimization terms.

## From Eiben & Smith (2015)
- **Two forces:** *variation* (recombination + mutation) creates diversity/novelty; *selection* raises mean quality. EAs are population-based, stochastic and usually use recombination; they are **generate-and-test** methods (pp.25–27).
- **Components to specify** (p.28): representation, evaluation (fitness) function, population, parent selection, variation operators, survivor selection (+ initialisation, termination). Different EA "dialects" differ mainly in representation: strings (GA), real vectors ([[evolution-strategies]]), finite-state machines/real vectors ([[evolutionary-programming]]), trees ([[genetic-programming]]). Selection is representation-independent (pp.27–28).
- **Genotype vs phenotype:** the encoding maps phenotypes → genotypes; search happens in genotype space; decode the best genotype at the end (pp.29–30). Example: 18 ↔ 10010.
- **Population** is the unit of evolution (individuals are static), usually constant size; **diversity** has no single measure (number of distinct fitness values / phenotypes / genotypes, entropy).
- **Behaviour:** anytime curve (fast early progress, then flat), premature convergence, exploration vs exploitation (pp.41–43). Long runs and heuristic initialisation rarely pay off.
- **Other variants:** [[differential-evolution]], [[particle-swarm-optimization]], [[estimation-of-distribution-algorithms]], [[learning-classifier-systems]]; hybrids: [[memetic-algorithms]]. Theory: [[no-free-lunch-theorem]].
- **Design detail pages:** [[selection-mechanisms]], [[survivor-selection-and-elitism]], [[crossover-and-mutation]], [[permutation-representation-operators]], [[parameter-control]], [[diversity-and-niching]], [[constraint-handling-in-ea]], [[multi-objective-optimization]].

> ⚠️ Contradiction: slide 2 credits Fogel (1960) as creator and dates evolution strategies to 1970; the book says ES were **invented in the early 1960s** by Rechenberg & Schwefel, with multi-membered ES in the 1970s (p.101), and EP by Fogel et al. in the 1960s (p.103).
