---
title: What Is AI? Four Approaches and the Standard Model
type: concept
tags: [foundations, history]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf, raw/slides/01_Introduction to Artificial Intelligence.pptx]
updated: 2026-09-29
---
# What Is AI? — Four Approaches and the Standard Model

Slide 2 of [[slides-01-introduction-to-ai]] asks "What do we mean by intelligence / by AI?" and lists informal definitions (understanding, problem solving, skill…). AIMA §1.1 ([[aima-ch01-introduction]], pp. 19–23) organizes the answers along two dimensions:

| | **Human** fidelity | **Rational** (ideal) |
|---|---|---|
| **Thought / reasoning** | Thinking humanly — cognitive modeling (GPS, cognitive science) | Thinking rationally — "laws of thought", logic (Aristotle; logicist tradition) |
| **Behavior** | Acting humanly — [[turing-test]] | Acting rationally — **rational agent** ([[rational-agents]]) |

## The standard model
AI = study and construction of agents that **do the right thing**, where "right" is defined by the objective we supply (p. 22). Same paradigm as control theory (cost function), OR (rewards), statistics (loss), economics (utility). Advantages of the rational-agent approach: more general than "laws of thought" (inference is only one route to rationality; reflexes count) and amenable to science (mathematically defined standard). Perfect rationality is infeasible → *limited rationality*.

## Beyond the standard model
The **value alignment problem**: it is hard to specify the objective fully and correctly; a highly capable system with a wrong objective can behave harmfully (chess-player that blackmails the opponent). AIMA proposes machines that are *uncertain about our objectives*, hence cautious and deferential — "provably beneficial" AI (pp. 23–24). Echoed by the slides' warning "you get what you ask for" ([[rational-agents]]).

## Note on terminology
Machine learning is a subfield of AI, not a synonym (footnote p. 19).

## Related
[[history-of-ai]], [[causal-models]], [[perceptron]]

## Exam angles
- Place a given system (chatbot, theorem prover, Roomba) in the 2×2 table.
- Why did the rational-agent approach prevail?
