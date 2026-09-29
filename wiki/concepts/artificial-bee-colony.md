---
title: Artificial Bee Colony
type: concept
tags: [optimization, swarm]
sources: [raw/slides/04_Optimization.pptx]
updated: 2026-09-29
---
# Artificial Bee Colony (ABC)

## Intuition
Swarm-intelligence algorithm by **Karaboga (2007)** imitating honeybee foraging (slides 16–18). Success depends on quickly discovering and efficiently exploiting the best food sources.

## Components (slide 17)
- **Employed bees:** each tied to a food source (candidate solution); search near it.
- **Onlooker bees:** choose sources with probability related to their quality; refine them.
- **Scout bees:** abandon exhausted sources and search randomly — they drive **exploration**; employed + onlooker bees do **exploitation**.

## Parameters (slide 18)
Number of food sources (= employed bees BN = onlookers SN), abandonment **limit**, max cycles **MCN**. Dimension D.

## New candidate (standard form, unverified — slide equation is an image)
v_ij = x_ij + φ_ij (x_ij − x_kj), with random k ≠ i in {1..BN}, j in {1..D}, φ ∈ [−1,1]. Greedy selection keeps the better of x_i and v_i. If a source fails to improve for `limit` trials, a scout replaces it with a random solution.

## Pros / cons
+ Few parameters, built-in exploration via scouts, gradient-free. − Slower exploitation than PSO/DE on some problems (unverified).

## Related
[[swarm-intelligence]], [[particle-swarm-optimization]], [[ant-colony-optimization]], [[exploration-vs-exploitation]], [[metaheuristics]], [[optimization-algorithms-comparison]].

## Exam angles
- Which bees explore and which exploit?
- What triggers a scout? (limit exceeded)
- List the three control parameters.
