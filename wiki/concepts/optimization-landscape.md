---
title: Optimization Landscape
type: concept
tags: [optimization, fitness-landscape]
sources: [raw/slides/04_Optimization.pptx, "raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Optimization Landscape

## Intuition
An optimization problem asks for the point x* minimizing (or maximizing) an objective f(x). Picture f as terrain: valleys are minima, peaks are maxima. Slide 3 stresses: *find the global optimum and avoid confusing it with local ones*. If every point is an "individual" with a fitness, evolutionary processes let the fittest converge on global optima (source: slides-04, slide 3). See [[slides-04-optimization]].

## Definitions
- **Global optimum:** best value over the whole search space.
- **Local optimum:** best in a neighbourhood, but worse than the global one.
- **Fitness / objective / cost / energy:** the value being optimized (names vary by field).
- **Convex function:** any local minimum is global (e.g., the quadratic in [[code-gradient-descent]]). **Multimodal:** many local optima (e.g., Rastrigin, see [[benchmark-functions]]).
- Plateaus, ridges, saddle points and noise also hinder search (ridges: motivate correlated mutation, [[self-adaptive-mutation]]).

## Why it matters
Local methods like [[gradient-descent]] converge to the nearest basin; global/stochastic methods ([[simulated-annealing]], [[genetic-algorithms]], [[particle-swarm-optimization]]) trade extra evaluations for a chance to escape. This is the [[exploration-vs-exploitation]] tension.

## Related
[[metaheuristics]], [[evolutionary-computation]], [[optimization-algorithms-comparison]]; state-space view in [[state-space]].

## Exam angles
- Distinguish local vs global optimum; give a function that has both.
- Why can gradient descent fail on multimodal functions? (Depends on the initial point.)
- Pitfall: maximization vs minimization — flip sign of f.

## In Eiben & Smith
Fitness landscape = fitness over the search space with neighbourhood structure given by the variation operators (§3.7, p.47). The **neighbourhood defines which points are local optima**; a global optimum is fitter than all neighbours under any neighbourhood. **Basin of attraction** matters: a local optimum with the largest basin can trap search ([[diversity-and-niching]]). Multimodality is typical of EA problems.
