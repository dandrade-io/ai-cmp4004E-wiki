---
title: Markov Models (Temporal Probabilistic Models)
type: concept
tags: [probability, temporal, markov]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Markov Models

**Intuition.** Model a world that changes over time as a sequence of *time slices*. The **Markov assumption**: the present state summarises the relevant past, so the future is independent of the past given the present. Syllabus topic 8 ([[slides-00-course-intro]]).

## Setup (AIMA §14.1, p. 479–482)
- Xₜ = hidden state variables, Eₜ = observed evidence at time t. Umbrella world: Rₜ (rain), Uₜ (umbrella).
- **First-order Markov:** **P**(Xₜ | X₀:ₜ₋₁) = **P**(Xₜ | Xₜ₋₁). Second-order uses two previous states.
- **Transition model** **P**(Xₜ|Xₜ₋₁); **sensor model** **P**(Eₜ|Xₜ) with the **sensor Markov assumption** **P**(Eₜ|X₀:ₜ,E₁:ₜ₋₁) = **P**(Eₜ|Xₜ); **prior** **P**(X₀).
- **Time-homogeneous (stationary process):** the same tables for every t.
- Joint: P(X₀:ₜ, E₁:ₜ) = P(X₀) ∏ᵢ P(Xᵢ|Xᵢ₋₁) P(Eᵢ|Xᵢ).
- Umbrella numbers: P(Rₜ|Rₜ₋₁) = 0.7 (stay), 0.3 (switch); P(u|r) = 0.9, P(u|¬r) = 0.2.

## Fixing a poor Markov assumption
Raise the order, or (equivalently in power) add state variables (season, temperature, battery level) – possibly with new sensors.

## Stationary distribution / mixing time (p. 486)
Predicting further ahead without evidence converges to a fixed point: for the umbrella world ⟨0.5, 0.5⟩. Prediction beyond a fraction of the mixing time is hopeless; more transition uncertainty ⇒ faster mixing.

## Worked example (prediction converges)
Start P(R₁)=⟨0.8,0.2⟩. Next day: 0.7·0.8+0.3·0.2 = 0.62 → then 0.7·0.62+0.3·0.38 = 0.548 → 0.5192 … → 0.5. Each step the distance from 0.5 shrinks by factor 0.4 (=0.7−0.3).

## Related
[[hidden-markov-models]] (inference algorithms), [[bayesian-networks]] (dynamic Bayes nets extend these), [[conditional-independence]], [[state-representation]], [[aima-ch14-reasoning-over-time]]

## Exam angles
- State the Markov and sensor assumptions and draw the network.
- Compute a one-step prediction by hand; identify the stationary distribution.
- When is first-order Markov a bad approximation and what are two fixes?
