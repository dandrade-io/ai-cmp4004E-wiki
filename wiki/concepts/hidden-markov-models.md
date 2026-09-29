---
title: Hidden Markov Models and Temporal Inference
type: concept
tags: [probability, temporal, hmm, inference]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Hidden Markov Models (HMMs) and Temporal Inference

**Intuition.** You can't see the state (is it raining?), only noisy evidence (umbrella). An **HMM** is a [[markov-models]] with a *single discrete* state variable; several variables can be merged into one "megavariable" (AIMA §14.3, p. 491).

## Four inference tasks (p. 483–484)
| Task | Computes | Example |
|---|---|---|
| **Filtering** | P(Xₜ \| e₁:ₜ) (belief state) | P(rain today \| umbrellas so far) |
| **Prediction** | P(Xₜ₊ₖ \| e₁:ₜ), k>0 | rain in 3 days |
| **Smoothing** | P(X_k \| e₁:ₜ), k<t | did it rain last Wednesday? |
| **Most likely explanation** | argmax P(x₁:ₜ \| e₁:ₜ) | best weather sequence (speech recognition) |

## Filtering (recursive; p. 484–485)
P(Xₜ₊₁|e₁:ₜ₊₁) = α · P(eₜ₊₁|Xₜ₊₁) · Σ_{xₜ} P(Xₜ₊₁|xₜ) P(xₜ|e₁:ₜ)  = α · **sensor** · Σ **transition** · **previous belief**.
Two steps: *predict* (project forward), *update* (multiply by evidence, normalise). Constant time/space per step.

**Worked (umbrella; verified numerically).** Prior ⟨0.5,0.5⟩.
- Day 1, umbrella: predict ⟨0.5,0.5⟩; update α⟨0.9·0.5, 0.2·0.5⟩ = α⟨0.45,0.1⟩ = **⟨0.818, 0.182⟩**.
- Day 2, umbrella: predict ⟨0.7·0.818+0.3·0.182, …⟩ = ⟨0.627,0.373⟩; update α⟨0.565,0.075⟩ = **⟨0.883, 0.117⟩**.
- Day 3, *no* umbrella (P(¬u|r)=0.1, P(¬u|¬r)=0.8): predict ⟨0.653,0.347⟩; update α⟨0.0653,0.2774⟩ ≈ **⟨0.191, 0.809⟩** (own extension).

## Smoothing – forward–backward (p. 486–488)
P(X_k|e₁:ₜ) = α f₁:ₖ × b_{k+1:t}. Backward message b_{k+1:t} = Σ P(e_{k+1}|x_{k+1}) b_{k+2:t} P(x_{k+1}|X_k), initialised to a vector of 1s. Storing forward messages gives O(t) for the whole sequence.
Umbrella check: b₂:₂ = ⟨0.69, 0.41⟩; smoothed P(R₁|u₁,u₂) = α⟨0.818,0.182⟩×⟨0.69,0.41⟩ ≈ **⟨0.883, 0.117⟩** > filtered 0.818 (later evidence + persistence).

## Most likely sequence – Viterbi (p. 489–491)
Same recursion as filtering with **max instead of sum** and no normalisation: m₁:ₜ₊₁ = P(eₜ₊₁|Xₜ₊₁) max_{xₜ} P(Xₜ₊₁|xₜ) m₁:ₜ; keep back-pointers. Linear time, **linear space**. Use log-probabilities or rescaling to avoid underflow. Umbrella [T,T,F,T,T] → most likely rain,rain,¬rain,rain,rain (checked). Caution: choosing the individually most likely state at each step (from smoothing) can give a *different*, worse sequence.

## Matrix form (p. 492)
Transition matrix T_{ij} = P(Xₜ=j|Xₜ₋₁=i); diagonal observation matrix Oₜ. Forward: f₁:ₜ₊₁ = α Oₜ₊₁ Tᵀ f₁:ₜ; backward: b_{k+1:t} = T O_{k+1} b_{k+2:t}. Cost O(S²t) time, O(St) space for S states.

## Other temporal models (skimmed)
Kalman filters (continuous Gaussian state), dynamic Bayesian networks (§14.4–14.5). HMM application: robot localization (§14.3.2).

## Related
[[markov-models]], [[bayes-theorem]], [[bayesian-networks]], [[bayes-and-markov-worked-examples]], [[aima-ch14-reasoning-over-time]], [[agent-types]] (model-based agent = filtering)

## Exam angles
- Do 1–2 filtering steps by hand with normalisation.
- Difference between filtering, prediction, smoothing; why smoothing beats filtering for past states.
- Viterbi vs forward: max vs sum.
- Why the state must be kept as a distribution (belief state).
