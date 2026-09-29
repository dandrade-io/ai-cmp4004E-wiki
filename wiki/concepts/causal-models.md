---
title: Causal Models
type: concept
tags: [causality, foundations]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Causal Models

**Motivation (slide 14).** Statistical models have limitations (slide title only; content is an image).

**Slide 15.** Causality between phenomena A and B: either A causes B, or B causes A, but not both at once. Judea Pearl's **Causal Calculus** (1987 per slide) encodes cause–effect relations in a **Directed Acyclic Graph (DAG)** and promises to connect with ML and AI. See [[judea-pearl]].

## What AIMA says (§13.5 Causal Networks, p. 467–471)
- A single arrow Fire → Smoke and the reversed Fire ← Smoke can encode the *same* joint distribution (via Bayes' rule), so an ordinary Bayesian network cannot express causal asymmetry. A **causal network** fixes arrow direction by **structural equations** xᵢ = fᵢ(other variables, Uᵢ) ("nature assigns Xᵢ from its parents"); Uᵢ are unmodelled disturbances. These mechanisms stay invariant under local changes.
- **Interventions – the do-operator:** do(Sprinkler=true) deletes the equation S = f_S(C,U_S) and replaces it by S = true ("mutilated network"), so nothing flows back from Sprinkler to Cloudy. Hence **P(·|do(x)) ≠ P(·|x)**: observing the sprinkler on lowers P(cloudy); turning it on does not.
- New joint: P_x(x₁…xₙ) = ∏_{i≠j} P(xᵢ|parents(Xᵢ)) when x_j = x_jk, else 0 (Eq. 13.19). **Adjustment formula:** P(xᵢ|do(x_jk)) = Σ_{parents(Xⱼ)} P(xᵢ|x_jk, parents(Xⱼ)) P(parents(Xⱼ)).
- **Back-door criterion:** when the needed conditionals are unknown, adjust for a set Z that blocks back-door paths (uses d-separation), e.g. P(g|do(S=true)) = Σᵣ P(g|S=true, r)P(r) for the sprinkler/rain/grass story. This lets causal effects be estimated from observational data, challenging the dogma that only randomized controlled trials can give causal information; also supports counterfactuals and transfer between populations.
- Compare with the slide's claim that A causes B *or* B causes A but not both: in a DAG, edges are acyclic, consistent with this (though feedback needs unrolling in time, unverified).

See [[bayesian-networks]] (the underlying formalism) and [[conditional-independence]] (d-separation).

## Related
[[bayesian-networks]], [[aima-ch13-probabilistic-reasoning]], [[history-of-ai]]; statistical methods listed on slide 10 (Bayesian networks, Markov networks).

## Exam angles
- Why a DAG (acyclic) and why direction matters.
- Give an example where correlation misleads.
