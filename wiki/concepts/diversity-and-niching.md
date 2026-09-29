---
title: Diversity and Niching
type: concept
tags: [evolutionary, multimodal]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Diversity, multimodality and niching

**Problem:** on multimodal landscapes finite populations with panmictic mixing suffer **genetic drift** — two equal niches of 50/50 drift to 49/51 and eventually one niche wins (book p.91). Sometimes we *want* several good solutions (broader peaks generalise better than sharp ones).

## Explicit approaches
- **Fitness sharing**: F'(i) = F(i) / Σ_j sh(d(i,j)), sh(d) = 1 − (d/σ_share)^α for d ≤ σ_share else 0. Population per peak ∝ peak fitness (needs FPS). Example: two identical individuals (d = 0) ⇒ each F' = F/2.
- **Crowding** (De Jong, crowding factor 2): offspring replaces the most similar of CF random parents. **Deterministic crowding** (Mahfoud): offspring compete with the closest parent; subpopulations spread *evenly* over peaks.
- **Automatic speciation**: mating restrictions (distance thresholds or species tags).
## Implicit approaches
- **Island models**: several subpopulations, migration every epoch (25–150 generations), exchange 2–5 individuals; epochs = exploitation, migration = exploration. Too-frequent migration ⇒ everyone converges together.
- **Cellular EAs**: individuals on a toroidal grid, mate/compete only within a deme (neighbourhood) — slower diffusion, lower pressure.

Related: [[exploration-vs-exploitation]], [[selection-mechanisms]], [[optimization-landscape]].

## Exam angles
- Compare sharing vs crowding population distributions (Fig. 5.4: 5 peaks fitness 5,4,3,2,1, pop 15 → sharing ∝ fitness; crowding even).
