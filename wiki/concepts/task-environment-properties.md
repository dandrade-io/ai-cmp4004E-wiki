---
title: Task Environment Properties
type: concept
tags: [agents, environments]
sources: [raw/slides/03_Intelligent Agents.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Task Environment Properties

Dimensions from slides 8–12:

| Dimension | Easy end | Hard end | Key question |
|---|---|---|---|
| Observability | Fully observable | Partially observable | Can sensors access the complete relevant state? Partial needs memory/state estimation (8) |
| Determinism | Deterministic | Non-deterministic / stochastic | Is next state fully determined by state + action? (9) |
| Episodes | Episodic | Sequential | Are episodes independent, or do decisions affect the future? (10) |
| Dynamics | Static | Dynamic (semidynamic) | Does the world change while deliberating? Semidynamic: world static, performance changes (chess with a clock) (11) |
| State/percept/action set | Discrete | Continuous | Finite well-defined states? (12) |
| Agents | Single | Multi-agent | Others may be competitive or cooperative (12) |

## AIMA additions ([[aima-ch02-intelligent-agents]], §2.3.2, pp. 61–65)
> ⚠️ Contradiction: AIMA lists **seven** dimensions — the slides' six plus **known vs. unknown**. This concerns the agent's/designer's knowledge of the "laws of physics" of the environment (outcomes of actions given), *not* observability: solitaire is known but partially observable; a new video game is unknown but fully observable.
> ⚠️ Contradiction: slide 9 equates non-deterministic with stochastic. AIMA: **stochastic** = the environment model explicitly uses probabilities ("25 % chance of rain"); **nondeterministic** = possibilities listed without probabilities ("a chance of rain"). Also partially observable environments can *appear* nondeterministic (p. 64).
- Also: *unobservable* (no sensors) is possible and goals may still be achievable (Ch. 4). Single-agent vs. multiagent depends on whether another entity's behavior is best described as maximizing a performance measure that depends on our agent's behavior; chess = **competitive**, taxi driving = partially **cooperative** and partially competitive (parking space). Randomized behaviour can be rational in competitive multiagent settings.
- Slide 11's semidynamic (chess with a clock) matches AIMA (p. 64).
- Slide 12 lumps two separate dimensions (discrete/continuous; single/multi-agent).
- **Hardest case** (p. 65): partially observable, multiagent, nondeterministic, sequential, dynamic, continuous, unknown. Taxi driving is hard in all senses except that it is mostly known.
- Examples table (Fig. 2.6, p. 65):

| Task | Observable | Agents | Deterministic | Episodic | Static | Discrete |
|---|---|---|---|---|---|---|
| Crossword | Fully | Single | Deterministic | Sequential | Static | Discrete |
| Chess with clock | Fully | Multi | Deterministic | Sequential | Semi | Discrete |
| Poker | Partially | Multi | Stochastic | Sequential | Static | Discrete |
| Backgammon | Fully | Multi | Stochastic | Sequential | Static | Discrete |
| Taxi driving | Partially | Multi | Stochastic | Sequential | Dynamic | Continuous |
| Medical diagnosis | Partially | Single | Stochastic | Sequential | Dynamic | Continuous |
| Image analysis | Fully | Single | Deterministic | Episodic | Semi | Continuous |
| Part-picking robot | Partially | Single | Stochastic | Episodic | Dynamic | Continuous |
| Refinery controller | Partially | Single | Stochastic | Sequential | Dynamic | Continuous |
| English tutor | Partially | Multi | Stochastic | Sequential | Dynamic | Discrete |

The properties are "not always cut and dried" (e.g. medical diagnosis is episodic if it just maps symptoms to a diagnosis, sequential if it includes a series of tests). Experiments run over an *environment class* (many simulated conditions) and average performance.

## Why it matters
Environment type determines suitable agent design ([[agent-types]]) and algorithm. [[problem-solving-agents]] assume observable, deterministic, discrete, static. [[adversarial-search]] = deterministic, fully observable, multi-agent competitive.

## Related
[[peas]], [[rational-agents]]

## Exam angles
- Classify a given environment on all six dimensions and justify.
- Stochastic vs. non-deterministic; semidynamic example.
