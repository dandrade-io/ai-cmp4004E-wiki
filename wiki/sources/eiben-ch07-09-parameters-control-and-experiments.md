---
title: Eiben & Smith Ch.7–9 — Parameters, Control, Working with EAs
type: source
tags: [book, evolutionary, methodology]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Eiben & Smith, Ch. 7–9 (pp. 119–164)

Book: [[eiben-smith]]. *Ch.7 (tuning) skimmed; Ch.8 read in part (pp.131–135, 143); Ch.9 read in part (pp.157–162).*

- **Ch.7**: EA parameters vs EA instances; tuning is itself a hard optimisation problem; tuners exist but a solid comparison was unavailable "as of 2013" (p.129).
- **Ch.8 Parameter control** (pp.131–145): static parameters are at odds with the dynamic nature of a run. Three control styles: **deterministic** (σ(t) = 1 − 0.9·t/T), **adaptive** (feedback, e.g. Rechenberg's **1/5 success rule**), **self-adaptive** (parameters co-evolve in the genome). Examples: mutation step size, penalty weights W(t) = (C·t)^α. Simulated annealing's cooling schedule is a *blind deterministic* control (p.132) and SA is a "(1+1) EA with increasing selection pressure" (p.142). See [[parameter-control]], [[self-adaptive-mutation]].
- **Ch.9 Working with EAs**: report **success rate (SR)** and **mean best fitness (MBF)** over many independent runs; compare with t-tests / ANOVA (or rank-based tests when not normal), not by eyeballing means; benchmark suite guidelines (Bäck & Michalewicz): unimodal (speed), many-optima multimodal, noisy, constrained, high-dimensional, scalable in n; De Jong five-function suite is outdated; Ackley, Griewank, Rastrigin common. "Bad practice" template: run new EA vs SGA 20× on 10 functions and count wins. See [[benchmark-functions]].
