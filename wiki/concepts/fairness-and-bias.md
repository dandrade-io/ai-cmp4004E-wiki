---
title: Fairness and Bias in Machine Learning
type: concept
tags: [ethics, fairness, machine-learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Fairness and Bias

**Intuition.** ML trained on past human decisions can reproduce (and hide) societal bias; "fair" has several incompatible meanings (AIMA §28.3.3, p. 1043–1047).

## Fairness criteria (p. 1043–1044)
- **Individual fairness:** similar individuals treated similarly.
- **Group fairness:** classes treated similarly by some statistic.
- **Fairness through unawareness:** delete the sensitive attribute – fails because correlates (zip code, occupation) predict it, and equal outcomes can no longer be checked.
- **Equal outcome / demographic parity:** same approval percentage per group (ignores individual merit).
- **Equal opportunity ("balance"):** qualified people equally likely to be classified correctly.
- **Equal impact:** similar likelihood ⇒ same expected utility (considers benefit of true and cost of false predictions).

## COMPAS case (p. 1044–1045)
Recidivism scorer designed to be **well calibrated** (score 7/10 ⇒ ~60 % vs 61 % reoffend for whites/blacks). But false-positive rates differ (45 % blacks vs 23 % whites) ⇒ fails equal opportunity. **Kleinberg et al. (2016):** if base rates differ, calibration and equal opportunity cannot both hold. *State v. Loomis* raised due-process concerns about secret algorithms.

## Sources of bias
- Biased ground truth (convictions ≠ crimes; patrol patterns).
- Sample-size disparity: fewer minority examples ⇒ lower accuracy (a gender classifier: near-perfect for light-skinned men, 33 % error for dark-skinned women, p. 1046).
- ML used to *justify* human bias; bias in the development process (engineers fix what affects them).
- Wrong objective: hiring for "best qualifications" vs "best ability to learn".
- Which classes are protected varies by law.

## Defences (p. 1046 ff.; only partly read)
Understand the limits of your data (AIMA suggests documenting data sets and models; specifics not read), audit, revisit the objective function, diversify teams (unverified beyond the first point).

## Related
[[ai-ethics-and-safety]], [[overfitting-and-generalization]] (a constrained model may fit only the majority), [[support-vector-machine]] (support vectors may all be majority examples), [[aima-ch28-philosophy-ethics-safety]]

## Exam angles
- Explain why calibration and equal opportunity conflict when base rates differ.
- Why does removing the "race" column not remove bias?
- Give two data-related sources of unfairness.
