---
title: "AIMA Ch. 2 — Intelligent Agents"
type: source
tags: [agents, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 2 — Intelligent Agents (pp. 53–79)

Book: [[russell-norvig]]. Course slides: [[slides-03-intelligent-agents]].

## Summary
The chapter treats AI as "the science of agent design": define an agent and its environment, define rationality, classify task environments, then present the standard agent-program designs.

## Key definitions
- **Agent**: perceives via sensors, acts via actuators (p. 54). **Percept sequence** = complete history. **Agent function**: percept sequence → action (abstract); **agent program**: its implementation; *agent = architecture + program* (p. 65). See [[rational-agents]].
- **Vacuum world** (Fig. 2.2/2.3, pp. 55–56): 2 squares A/B; actions Left/Right/Suck. The tabulated function is unbounded unless percept-sequence length is bounded.
- **Performance measure** (p. 57): evaluates sequences of *environment states*; design it for "what you actually want in the environment", not for how you think the agent should behave (dirt-dumping example).
- **Rational agent** (p. 58): *for each possible percept sequence, select an action expected to maximize its performance measure, given the evidence from the percept sequence and built-in knowledge.* Depends on four things: performance measure, prior knowledge, available actions, percept sequence.
- Rationality ≠ omniscience ≠ perfection (Champs-Élysées example); requires *information gathering*, *learning*, and *autonomy* (dung beetle, sphex wasp) (pp. 58–60).
- **Task environment / PEAS** (p. 60–62, Fig. 2.4–2.5): [[peas]].
- **Properties of task environments** (pp. 61–65, Fig. 2.6): fully/partially observable (or unobservable), single/multiagent (competitive/cooperative), deterministic/nondeterministic (vs. stochastic), episodic/sequential, static/dynamic (semidynamic), discrete/continuous, **known/unknown** — [[task-environment-properties]].
- **Agent programs** (pp. 65–78): table-driven (Fig. 2.7; hopeless — table size 4^T for vacuum), [[agent-types]]: simple reflex (Fig. 2.9–2.10), model-based reflex (Fig. 2.11–2.12; *transition model* + *sensor model*), goal-based (2.13), utility-based (2.14), and [[learning-agents]] (critic, learning element, performance element, problem generator, Fig. 2.15).
- **Representations** (pp. 76–78, Fig. 2.16): atomic, factored, structured; expressiveness vs. reasoning cost; chess rules: 1–2 pages in FOL, thousands in propositional, ~10^38 pages atomic — [[state-representation]].

## Summary bullets (p. 79)
Seven environment dimensions; risk of optimizing the wrong objective when the measure is misspecified; designs vary in efficiency/compactness/flexibility; all agents can improve through learning.

## Slide vs. book discrepancies
> ⚠️ Contradiction: [[slides-03-intelligent-agents]] lists six environment dimensions; AIMA lists **seven** (adds known/unknown, p. 65). Slide 9 also treats "non-deterministic" and "stochastic" as the same; AIMA distinguishes them: *stochastic* = probabilities explicitly modeled, *nondeterministic* = outcomes listed without probabilities (p. 64).

> ⚠️ Contradiction: slide 15 says a model-based agent uses a *world model* and a *transition model*. AIMA's two models are the **transition model** (how the world evolves *and* what the agent's actions do) and the **sensor model** (how state shows up in percepts) (p. 70). The slide's split matches the two *parts* of AIMA's transition model.

> ⚠️ Contradiction (soft): slide 5 says the performance measure is defined "by the designer, not by the agent" — consistent with AIMA, but AIMA adds that the designer may not know the users' true preferences and the agent may need to learn them (pp. 57–58, 65).

## Pages updated
[[rational-agents]], [[peas]], [[task-environment-properties]], [[agent-types]], [[state-representation]], [[learning-agents]] (new).
