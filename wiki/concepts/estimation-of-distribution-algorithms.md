---
title: Estimation of Distribution Algorithms (EDA)
type: concept
tags: [evolutionary]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Estimation of Distribution Algorithms (EDA)

Replace crossover/mutation by **model building** (book §6.8, pp.113–116): select fittest subpopulation (truncation) → learn a probabilistic graphical model (dependencies between genes, "linkage learning") → **sample** μ new candidates from it; generational replacement. Univariate (PBIL), pairwise (MIMIC, BMDA), tree/BN-based (BOA). Discrete data → Bayesian networks; continuous → Gaussians (cf. covariance in [[self-adaptive-mutation]]). Connects to probabilistic reasoning in AI (Bayesian networks).

Related: [[genetic-algorithms]], [[evolutionary-computation]].
