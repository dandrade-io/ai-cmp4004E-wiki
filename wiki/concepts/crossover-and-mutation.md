---
title: Crossover and Mutation
type: concept
tags: [genetic, evolutionary, operators]
sources: [raw/slides/04_Optimization.pptx, raw/papers/Holland-GeneticAlgorithms-1992.pdf, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Crossover and Mutation

Variation operators of [[genetic-algorithms]] (slide 6 of [[slides-04-optimization]]).

## Chromosome
A sequence of 1s and 0s encoding a point of the solution space (e.g., a decimal number in binary).

## Crossover (recombination)
Parents (h1, h2) **exchange bit sections at the same position**.
- **Single-point:** pick cut c; child1 = h1[:c] + h2[c:], child2 = h2[:c] + h1[c:].
- **Two-point / k-point:** generalization with several cuts.
- **Uniform crossover** (Eiben & Smith p.53): each gene inherited from parent 1 if a random number < p (usually 0.5), else parent 2; second child is the inverse.
Example: h1 = 1101|0010, h2 = 0110|1111, cut 4 → 11011111 and 01100010.

## Mutation
Each bit flips independently with probability p_m (small; book p.52: expected L·p_m flips per chromosome, typical p_m gives between 1 gene per generation and 1 gene per offspring). Example: 11011111 → 11001111.

## What Holland says (1992, [[paper-holland-genetic-algorithms]])
- Crossover "closely mimics its biological model": chromosomes line up, a random point is chosen, and the portions beyond it are swapped, giving two complementary offspring (PDF p.4). Offspring replace the *least fit* strings, not their parents.
- Mutation rate quoted: roughly **1 in 10,000 symbols** flip 0↔1 (p.4) — much lower than the 1/L heuristic for short strings. Mutation "does not generally advance the search" alone; it is insurance against a uniform population that can no longer evolve.
- Crossover can break **building blocks**; the chance depends on the distance between the defining bits (compact blocks survive; e.g. `10****` breaks with prob. 1/5 in 6 genes). The biological **inversion** operator reorders genes to make useful blocks more compact (pp.4–5).
- Early evolutionary computing relied on mutation only and "fared poorly"; Bremermann's 1960s mating summed parent genes (only for additive traits) (p.2).

## Roles
Crossover mixes good partial solutions (exploitation); mutation injects new genetic material and avoids stagnation (exploration). See [[exploration-vs-exploitation]].

## Related
[[evolutionary-computation]], [[john-holland]].

## Exam angles
- Perform a 1- and 2-point crossover by hand.
- Expected number of flips = L·p_m.
- Too high p_m ⇒ random search; too low ⇒ premature convergence.

## More operators — Eiben & Smith Ch.4 ([[eiben-ch04-representation-variation]])
**Biases:** n-point crossover has *positional bias* (keeps nearby genes together; odd n strongly separates end genes); uniform crossover has none but a *distributional bias* (≈50 % of genes from each parent). No operator is best for all problems ([[no-free-lunch-theorem]]).

**Gray coding:** in plain binary 7→8 (0111→1000) needs 4 flips but 7→6 only 1; Gray code makes consecutive integers differ by one bit (7 = 0100, 8 = 1100).

**Integer genes:** random resetting (cardinal, e.g. colours) vs creep mutation (ordinal). Recombination as for binary.

**Real-valued genes:**
- Mutation: uniform, or Gaussian N(0,σ) (σ = step size; ≈ ⅔ of changes within ±σ); Cauchy has a fatter tail. Step sizes can be self-adapted → [[self-adaptive-mutation]].
- Recombination: **discrete** (z_i = x_i or y_i), **arithmetic** z = αx + (1−α)y — *simple* (first k genes from parent, rest averaged), *single* (one gene averaged), *whole* (all genes; α = ½ gives identical children) — and **blend crossover BLX-α** (children in a box larger than the parents' box). Example: x_i = 2, y_i = 6 (d = 4), α = 0.5 ⇒ child range [x_i − αd, y_i + αd] = [0, 8].

> ⚠️ Errata: the book prints γ = (1−2α)u − α for BLX-α; with α = 0.5 this is constant (−0.5). The original BLX-α uses (1+2α)u − α (unverified vs original paper).

**Permutations:** swap/insert/scramble/inversion mutation; PMX, order, cycle, edge crossover with worked examples in [[permutation-representation-operators]].
**Trees:** subtree crossover/mutation in [[genetic-programming]].
**Multiparent** (arity > 2) operators have no biological analogue but often accelerate search (p.51); DE's differential mutation is an example ([[differential-evolution]]).
