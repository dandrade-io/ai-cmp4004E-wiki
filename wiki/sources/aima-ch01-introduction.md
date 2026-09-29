---
title: "AIMA Ch. 1 — Introduction"
type: source
tags: [history, foundations, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 1 — Introduction (pp. 19–52)

Book: [[russell-norvig]]. Course slides covering the same ground: [[slides-01-introduction-to-ai]]. Page numbers below are the *printed* book pages.

## Summary
The chapter defines AI along two axes (human vs. rational, thought vs. behavior), surveys the disciplines that fed AI, gives a phase-by-phase history, and closes with state of the art and risks/benefits.

## 1.1 What is AI? (pp. 19–23)
Four approaches ([[ai-foundations-and-approaches]]):
1. **Acting humanly** — [[turing-test]] approach (needs NLP, knowledge representation, automated reasoning, machine learning; *total* Turing test adds vision and robotics).
2. **Thinking humanly** — cognitive modeling (introspection, experiments, brain imaging); Newell & Simon's GPS.
3. **Thinking rationally** — "laws of thought", logic (Aristotle syllogisms; logicist tradition); limited because real knowledge is uncertain → probability.
4. **Acting rationally** — the *rational agent* approach; "do the right thing", defined by the objective supplied. Called the **standard model**; the book adopts it ([[rational-agents]]).
Also: *limited rationality* (perfect rationality infeasible), and the **value alignment problem** — the objective we specify may not match our true preferences (p. 23).

## 1.2 Foundations (pp. 23–35)
Philosophy (Aristotle, Descartes dualism, empiricism, utilitarianism vs. deontology), mathematics (Boole, Frege, Gödel incompleteness, Turing computability, tractability, NP-completeness), economics (utility, decision theory), neuroscience, psychology, computer engineering, control theory, linguistics. Key point for search: **tractability** — "the world is an extremely large problem instance" (p. 28).

## 1.3 History (pp. 35–45)
| Phase | Key facts (book) |
|---|---|
| Inception 1943–1956 | McCulloch & Pitts neuron model (1943); Hebb (1949); SNARC (Minsky & Edmonds, 1950); Turing 1950 paper; **Dartmouth workshop, summer 1956** (2 months, 10 attendees; first use of the term "artificial intelligence"); Logic Theorist |
| Early enthusiasm 1952–1969 | GPS, Samuel's checkers (reinforcement learning), McCarthy's **Lisp (1958)** and Advice Taker, Robinson's resolution (1965), microworlds/blocks world, Rosenblatt perceptrons, Widrow adalines |
| Dose of reality 1966–1973 | Failures of "informed introspection"; combinatorial explosion; Lighthill report (1973); Minsky & Papert *Perceptrons* (1969) |
| Expert systems 1969–1986 | DENDRAL, MYCIN, R1; "weak methods" vs. knowledge-intensive; Prolog popular in Europe/Japan; Fifth Generation project (1981); **AI winter** afterwards |
| Return of neural nets 1986– | Back-propagation *reinvented* mid-1980s (first developed early 1960s: Kelley 1960, Bryson 1962); PDP volumes (1986) |
| Probabilistic reasoning & ML 1987– | HMMs in speech; Pearl 1988 Bayesian networks; Sutton 1988 RL–MDP link |
| Big data 2001– | Web-scale data; Watson wins Jeopardy! (2011) |
| Deep learning 2011– | Took off 2011 (speech, then vision); 2012 ImageNet win by Hinton's group; AlphaGo (2016) |
Turing Award summary (p. 35): Minsky 1969, McCarthy 1971, Newell & Simon 1975, Feigenbaum & Reddy 1994, [[judea-pearl]] 2011, Bengio/Hinton/LeCun 2019.

## 1.4–1.5 State of the art, risks and benefits (pp. 45–52)
Applications overview; risks (lethal autonomous weapons, surveillance, bias, employment, safety, existential risk) and benefits. Not in the slides.

## Derived / updated wiki pages
[[history-of-ai]], [[turing-test]], [[rational-agents]], [[perceptron]] (Minsky–Papert limits), [[backpropagation]], [[deep-learning]], [[ai-foundations-and-approaches]].

## Slide vs. book discrepancies
> ⚠️ Contradiction: [[slides-01-introduction-to-ai]] dates backprop to 1975 and "deep learning" to 1986/2000. AIMA: backprop was first developed in the early 1960s and reinvented in the mid-1980s (p. 40, p. 43); deep learning took off in **2011** (p. 44). Exam answers should follow the book/instructor's stated dates; see [[history-of-ai]].

> ⚠️ Contradiction: the slide 1 timeline lists Prolog as 1970 (and misattributes it). See [[prolog]]; AIMA only says Prolog "became popular in Europe and Japan" (p. 41).
