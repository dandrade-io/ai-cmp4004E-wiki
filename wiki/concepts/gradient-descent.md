---
title: Gradient Descent
type: concept
tags: [optimization, gradient, machine-learning]
sources: [raw/code/gd_functions.py, raw/code/gd_steroids.py, raw/slides/01_Introduction to Artificial Intelligence.pptx]
updated: 2026-09-29
---
# Gradient Descent

## Intuition
Stand on a hillside in fog and always step downhill along the steepest slope. The gradient ∇f points to steepest ascent, so move opposite to it.

## Update rule
```
w ← w − η ∇f(w)          # repeat for num_iterations or until ||∇f|| < ε
```
η is the **learning rate**. In [[code-gradient-descent]]: f = (x−2)²+(y+2)², ∇f = [2(x−2), 2(y+2)], w₀ = (0,0). Error contracts by (1−2η) per step for that quadratic.

## Properties
- Needs a differentiable objective (gradient available analytically or by autodiff, unverified).
- Converges to a local minimum (global if convex). Result depends on the start point.
- Too small η: slow; too large: oscillation/divergence. Variants: momentum, Adam, stochastic/mini-batch GD (unverified).
- Slide 11 of [[slides-01-introduction-to-ai]] links it to [[backpropagation]]: backprop computes the gradient of the loss w.r.t. every weight, then GD updates them (see also [[perceptron]], [[deep-learning]]).

## Pros / cons
+ Cheap per step, scales to millions of parameters. − Local only, sensitive to η and scaling; useless for discrete/non-differentiable problems (where [[genetic-algorithms]] or [[simulated-annealing]] apply).

## Related
[[optimization-landscape]], [[metaheuristics]], [[optimization-algorithms-comparison]].

## Exam angles
- Compute two GD iterations by hand on a quadratic given η.
- Effect of η on convergence; give the stability range for f = x² (0 < η < 1).
- Why gradient-based methods stall in local minima of [[benchmark-functions]] like Rastrigin.
