---
title: Learning Agents
type: concept
tags: [agents, learning]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Learning Agents

Not in the course slides ([[slides-03-intelligent-agents]] stops at utility-based agents); from AIMA §2.4.6, pp. 74–76 ([[aima-ch02-intelligent-agents]]).

Any agent type (model-based, goal-based, utility-based) can be built as a learning agent. Turing (1950): build learning machines and teach them rather than hand-programming intelligence.

## Four components (Fig. 2.15)
- **Performance element** — what we previously called the whole agent: percepts → actions.
- **Learning element** — improves the performance element using feedback.
- **Critic** — tells the learning element how well the agent does relative to a *fixed performance standard* (outside the agent, so it can't rewrite the standard to suit itself). Percepts alone don't say whether checkmate is good.
- **Problem generator** — suggests exploratory, possibly suboptimal actions that yield informative experiences (like a scientist's experiments).

## What can be learned
Any knowledge component: "what my actions do" and "how the world evolves" (transition model), sensor model, reflex rules, utility function (needs external reward/penalty feedback). Learning brings the components into closer agreement with feedback. Rational agents should be *autonomous*: learn to compensate for partial/incorrect prior knowledge ([[rational-agents]]).

## Related
[[agent-types]], [[task-environment-properties]] (unknown environments), [[exploration-vs-exploitation]] (problem generator ≈ exploration)

## Exam angles
- Name and describe the four components; why is the critic separate from the performance standard's owner?
