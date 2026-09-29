---
title: History of AI
type: concept
tags: [history, foundations]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# History of AI

**Intuition.** AI's roots run from myths of artificial beings to mechanical calculators, then to formal computation and learning machines. The course slides use a timeline ([[slides-01-introduction-to-ai]]).

## Timeline (from slides)
| Date | Event | Slide |
|---|---|---|
| ~800 BC | Talos, bronze automaton in the Iliad | 19 |
| ~200 BC | Antikythera mechanism, earliest known analog computer (predicts eclipses up to 19 years ahead); studied 1900–1971 | 17–18 |
| 1768–1774 | Jaquet-Droz automata (musician, draughtsman, writer); 1770 Mechanical Turk (von Kempelen) | 3 |
| 1936 / 1945 | Z1 (Zuse, binary, punched cards, floating point) / ENIAC (vacuum tubes, 170 m², 27 t) | 4 |
| 1950 | [[turing-test]] | 5 |
| 1956 | Dartmouth workshop (McCarthy, Minsky, Rochester, Shannon organizers; 10 attendees incl. Newell, Simon, Samuel) — birth of AI; first use of the term "artificial intelligence" (AIMA p. 36) | 7 |
| 1957–58 | FORTRAN (imperative), LISP (McCarthy; lambda calculus, lists) | 6 |
| 1958 | [[perceptron]] (Rosenblatt) | 8 |
| 1970 | [[prolog]] / logic programming | 9 |
| 1975 | [[backpropagation]] (slide date) | 11 |
| 1995 | [[support-vector-machine]] (Vapnik) | 12 |
| 2000 | [[deep-learning]] (Bengio, Hinton, LeCun) | 13 |
| 1987 | Causal calculus, [[judea-pearl]] → [[causal-models]] | 15 |
| today | Generative AI, LLMs, agents | 2 |

Dartmouth proposal topics: automatic computers, language, neuron nets, theory of computation size, self-improvement, abstractions, randomness and creativity (slide 7).

## AIMA's phase-by-phase history (§1.3, pp. 35–45; see [[aima-ch01-introduction]])
- **1943–1956 inception:** McCulloch & Pitts artificial neurons (1943), Hebb (1949), SNARC (1950), Turing 1950 (test, machine learning, genetic algorithms, RL), **Dartmouth 1956** — two months, 10 attendees, first use of the term "artificial intelligence"; Logic Theorist.
- **1952–1969 early enthusiasm:** GPS, Samuel's checkers, Lisp (1958), Advice Taker, resolution (1965), microworlds, perceptrons/adalines.
- **1966–1973 dose of reality:** combinatorial explosion, Lighthill report (1973), Minsky–Papert *Perceptrons* (1969).
- **1969–1986 expert systems:** DENDRAL, MYCIN, R1; knowledge-intensive "strong" methods vs. general "weak methods"; Fifth Generation project (1981); then the **AI winter**.
- **1986– neural nets return:** back-propagation reinvented mid-1980s (first developed early 1960s).
- **1987– probabilistic reasoning & ML:** HMMs, Bayesian networks (Pearl 1988), RL–MDP link (Sutton 1988).
- **2001– big data; 2011– deep learning** (2012 ImageNet, AlphaGo 2016).
Turing Awards as milestones: Minsky 1969, McCarthy 1971, Newell & Simon 1975, Feigenbaum & Reddy 1994, Pearl 2011, Bengio/Hinton/LeCun 2019.

> ⚠️ Contradiction: the slide timeline dates backpropagation to **1975** and deep learning to **1986/2000**. AIMA: backprop first developed in the early 1960s (Kelley 1960, Bryson 1962) and reinvented by ≥4 groups in the mid-1980s (PDP volumes, 1986); "deep learning" took off in **2011** (p. 44). The 1975 date is not supported by AIMA (Holland's *genetic algorithms* book is 1975 — [[john-holland]]; possible mix-up, unverified).

> ⚠️ Contradiction: slide timeline's Prolog entry (1970, "Dennis Ritchie") is wrong; see [[prolog]] / [[alain-colmerauer]] (1972, Marseille).

## Two traditions
Symbolic/logic (LISP, Prolog, expert systems) vs. statistical/connectionist (perceptron → deep learning). AIMA frames this as logicists (McCarthy) vs. anti-logic (Minsky) vs. connectionists (Hinton calls symbols the "luminiferous aether of AI") (pp. 38, 43); the field later embraced statistics and probability ("neats" vs. "scruffies"). Slide 10 contrasts formal vs. statistical methods for building models. See also [[ai-foundations-and-approaches]].

## Related
[[rational-agents]], [[optimization-landscape]]

## Exam angles
- Match milestone ↔ person ↔ decade (Turing 1950, McCarthy/Minsky/Shannon/Rochester 1956, Rosenblatt 1958, Vapnik 1995).
- Pitfall: slide dates for backprop/deep learning differ from common textbook dates (see errata in source page).
