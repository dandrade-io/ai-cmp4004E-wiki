---
title: Learning Classifier Systems (LCS)
type: concept
tags: [evolutionary, machine-learning]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Learning Classifier Systems (LCS)

Evolutionary model building with **rule sets** {condition:action:payoff} (book §6.5, pp.107–110). Condition alphabet {0,1,#} (# = don't care).
- **Michigan** approach: each individual = one rule; the whole population is the model; rules rewarded by reinforcement. Holland 1976; ZCS (Wilson, memoryless); **XCS** adds *accuracy* and selects on accuracy, running the EA in the action set — links LCS to reinforcement learning.
- **Pittsburgh** approach: each individual = a complete ordered rule list (variable length); fitness = accuracy on the data; suffers bloat like [[genetic-programming]]; good where interpretability matters (medicine, bioinformatics).
- Workflow (Michigan): match set → (cover if empty) → group by action → choose action (exploit/explore) → reward → update payoff/accuracy → EA in action set.

Related: [[john-holland]] (classifier systems in [[paper-holland-genetic-algorithms]]), [[genetic-algorithms]].
