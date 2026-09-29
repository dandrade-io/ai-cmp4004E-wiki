---
title: Probability Basics for AI
type: concept
tags: [probability, uncertainty, foundations]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Probability Basics for AI

**Intuition.** Logic says which worlds are ruled out; probability says *how likely* each remaining world is. An agent facing uncertainty (partial sensors, laziness, ignorance) keeps a *degree of belief* per proposition and conditions it on evidence (AIMA p. 403–406).

## Core definitions (AIMA §12.2, p. 406–412)
- **Sample space** Ω = all possible worlds (mutually exclusive, exhaustive). A **probability model** gives each world ω a P(ω) with 0 ≤ P(ω) ≤ 1 and ΣP(ω) = 1.
- **Proposition/event** φ: P(φ) = Σ_{ω∈φ} P(ω). Two fair dice: 36 worlds, P(Total=11) = 2/36 = 1/18.
- **Prior (unconditional)** P(a) vs **posterior (conditional)** P(a|b) = P(a∧b)/P(b), needs P(b) > 0.
- **Product rule:** P(a∧b) = P(a|b)P(b).
- **Random variable** (capitalised) with a range; **distribution** **P**(Weather) = ⟨0.6, 0.1, 0.29, 0.01⟩; **joint** **P**(X,Y) is a table.
- **Negation:** P(¬a) = 1 − P(a). **Inclusion–exclusion:** P(a∨b) = P(a) + P(b) − P(a∧b) (Kolmogorov's axioms).
- Continuous variables use a *density* (a density is not a probability).
- De Finetti's betting argument: an agent with beliefs violating the axioms can be made to lose money for sure (p. 412).

## Inference from the full joint (AIMA §12.3, p. 413)
Toothache/Catch/Cavity table: P(cavity∨toothache) = 0.28; **marginalization** P(Y) = Σ_z P(Y,z); **conditioning** P(Y) = Σ_z P(Y|z)P(z).
P(cavity | toothache) = (0.108+0.012)/(0.108+0.012+0.016+0.064) = **0.6**.
**Normalization:** P(X|e) = α Σ_y P(X,e,y): compute unnormalised entries, divide by their sum, so P(e) is never needed.

Problem: n Boolean variables → 2ⁿ entries. Full joint is a theoretical foundation, not a practical tool → need [[conditional-independence]] and [[bayesian-networks]].

## Worked example
Joint from Fig 12.3: P(cavity) = 0.108+0.012+0.072+0.008 = 0.2. P(¬cavity | toothache) = 0.08/0.2 = 0.4, and 0.6+0.4 = 1 as required.

## Pros / cons
+ Principled, complete language for uncertainty. − Exponential joint tables; probabilities can be hard to elicit.

## Related
[[bayes-theorem]], [[conditional-independence]], [[naive-bayes]], [[bayesian-networks]], [[rational-agents]] (maximize expected performance), [[task-environment-properties]] (partial observability, stochastic), [[aima-ch12-quantifying-uncertainty]]

## Exam angles
- Compute a marginal/conditional from a joint table; show the normalisation step.
- Difference between conditioning and logical implication.
- Why the joint table does not scale.
