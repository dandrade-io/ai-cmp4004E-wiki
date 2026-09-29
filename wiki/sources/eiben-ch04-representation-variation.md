---
title: Eiben & Smith Ch.4 — Representation, Mutation, Recombination
type: source
tags: [book, evolutionary, operators]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Eiben & Smith, Ch. 4 (pp. 49–78)

Book: [[eiben-smith]]. Ties to [[crossover-and-mutation]], [[permutation-representation-operators]], [[self-adaptive-mutation]], [[genetic-programming]].

## Key ideas
- Variation operators are **representation dependent**; choosing the representation is one of the hardest design steps (p.49). Recombination is applied with probability p_c (else copies); arity a can exceed 2 (multiparent) — no biological analogue (pp.49–51).
- **Binary** (pp.51–54): bitwise mutation with p_m flips L·p_m bits on average; typical rates between 1 gene per generation and 1 per offspring. Recombination: **one-point** (point in [1, l−1]), **n-point**, **uniform** (p = 0.5). *Positional bias* (n-point keeps close genes together) vs *distributional bias* (uniform transmits ~50 % of genes from each parent). Binary coding of integers has Hamming cliffs (0111→1000 = 4 flips); **Gray coding** fixes this. Using bit strings for non-binary information is "usually a mistake".
- **Integer** (pp.54–56): random resetting (cardinal attributes, e.g. graph colours) vs creep mutation (ordinal). Recombination: same as binary.
- **Real-valued** (pp.56–67): uniform mutation; **Gaussian non-uniform** mutation (σ = step size); Cauchy alternative; self-adaptation (see [[self-adaptive-mutation]]). Recombination: discrete, **arithmetic** (simple/single/whole, α), **blend crossover BLX-α**.
- **Permutation** (pp.67–75): swap, insert, scramble, inversion mutation; PMX, edge-3, order, cycle crossover. Two problem classes: *order-based* (scheduling) vs *adjacency-based* (TSP).
- **Tree** (pp.75–78): function set F + terminal set T, closure property; subtree mutation and subtree crossover (see [[genetic-programming]]).

> ⚠️ Errata (book, p.66): BLX-α is given as γ = (1−2α)u − α, which for the recommended α = 0.5 collapses to γ = −0.5 for every u (no randomness). The original BLX-α uses γ = (1+2α)u − α, which spans [−α, 1+α] (unverified against the original paper, but the algebra of the printed formula is checkable).

## Worked examples
See [[crossover-and-mutation]] (blend, arithmetic) and [[permutation-representation-operators]] (PMX, order, cycle on the book's 9-element parents).
