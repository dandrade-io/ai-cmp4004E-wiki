---
title: Eiben & Smith Ch.5 — Fitness, Selection, Population Management
type: source
tags: [book, evolutionary, selection]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Eiben & Smith, Ch. 5 (pp. 79–98)

Book: [[eiben-smith]].

## Contents
- **Population models** (p.79–80): *generational* (μ parents → λ offspring replace everything; Simple GA has μ = λ) vs *steady-state* (replace λ < μ; generational gap λ/μ; often λ = 1, Whitley's GENITOR).
- **Parent selection** (pp.80–87): fitness proportional (FPS) with problems (premature convergence, weak pressure late, not translation invariant — Table 5.1), **windowing** and **sigma scaling** f' = max(f − (f̄ − c·σ_f), 0), c = 2; **ranking** (linear, parameter s ∈ (1,2]; exponential); sampling by **roulette wheel** (Fig 5.1) vs **stochastic universal sampling** (SUS, Fig 5.2); **tournament** (size k, probability p, with/without replacement); uniform selection (ES, EP); **over-selection** for huge populations (Koza's 32 %/16 %/8 %/4 % table, 80/20 rule).
- **Survivor selection** (pp.87–90): age-based (generational, FIFO, random not recommended); fitness-based: replace-worst, **elitism**, round-robin tournament (EP, q = 10), **(μ+λ)** and **(μ,λ)** (ES).
- **Selection pressure** (p.90): takeover time τ* = ln λ / ln(λ/μ) for ES; τ* = λ ln λ for FPS GA.
- **Diversity & multimodality** (pp.91–98): genetic drift, **fitness sharing**, **crowding / deterministic crowding**, automatic speciation, **island models** (epochs 25–150 gens, exchange 2–5 individuals), **cellular EAs** (demes on a toroidal grid).

## Derived pages
[[selection-mechanisms]], [[survivor-selection-and-elitism]], [[diversity-and-niching]], [[exploration-vs-exploitation]], [[evolution-strategies]].
