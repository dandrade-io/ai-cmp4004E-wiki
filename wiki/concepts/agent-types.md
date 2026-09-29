---
title: Agent Types
type: concept
tags: [agents]
sources: [raw/slides/03_Intelligent Agents.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Agent Types

Increasing sophistication (slides 14–17):

| Type | Idea | Strength | Limitation |
|---|---|---|---|
| **Simple reflex** | Current percept only, condition–action rules | Simple, efficient | Fails in partially observable environments |
| **Model-based reflex** | Keeps internal state via a *world model* (how world evolves independently) and a *transition model* (effect of own actions); applies rules to the state | Acts coherently under partial observability | No notion of goals |
| **Goal-based** | Knows desired states; chooses actions toward goals via planning/search; adapts when goal changes | Flexible | Binary goal/not-goal; can't rank paths |
| **Utility-based** | Maximizes expected utility over outcome probabilities | Handles conflicting objectives (speed vs. safety) and uncertainty | Needs utility function and probabilities |

## AIMA grounding ([[aima-ch02-intelligent-agents]], §2.4, pp. 65–76)
- Every program has the skeleton *percept in → action out*; the table-driven agent (Fig. 2.7) is infeasible.
- **Simple reflex** (Fig. 2.9–2.10): if car-in-front-is-braking then initiate-braking; works only if the correct decision follows from the current percept alone, i.e. the environment is fully observable. Without a location sensor the vacuum agent loops forever; a **randomized** reflex agent escapes (expected 2 steps to reach the other square) — randomization is usually not rational in single-agent settings.
- **Model-based reflex** (Fig. 2.11–2.12): maintains *internal state* using a **transition model** ("how the world evolves" + "what my actions do") and a **sensor model** (how states appear in percepts); the state is a "best guess" under uncertainty.
> ⚠️ Contradiction: the slide names a *world model* and a *transition model*; AIMA names the **transition model** (which covers both world evolution and action effects) and the **sensor model**.
- **Goal-based** (Fig. 2.13): needs goal information plus the model; considers the future ("what will happen if I do X?") — uses search and planning; flexible because knowledge is explicit (change the destination without rewriting rules).
- **Utility-based** (Fig. 2.14): utility function = internalization of the performance measure; needed when goals conflict (speed vs. safety) or are uncertain; rational if the utility function agrees with the external measure. AIMA notes it is *not the only way to be rational* (the reflex vacuum agent is rational without any utility function).
- **Learning agents** → [[learning-agents]] (performance element, learning element, critic, problem generator).

## Related
[[problem-solving-agents]] (goal-based), [[learning-agents]], [[task-environment-properties]], [[rational-agents]], [[state-representation]]

## Exam angles
- Pick the minimal agent type for a given environment.
- Why model-based reflex agents need two models.
- Example where goal-based is insufficient (many paths to goal, different quality).
