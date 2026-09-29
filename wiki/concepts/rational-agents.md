---
title: Rational Agents
type: concept
tags: [agents]
sources: [raw/slides/03_Intelligent Agents.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Rational Agents

**What is an agent (slide 2).** Anything that perceives an environment through sensors and acts through actuators. Examples: human (eyes/ears → brain → hands/mouth), robot (cameras → processor → motors), software agent (keyboard/file input → program → screen/network).

## Agent function vs. agent program (slide 3)
- **Agent function**: abstract specification mapping percept history → action; could in theory be a lookup table. *What we want.*
- **Agent program**: concrete implementation on a physical architecture that approximates the function compactly. *How we approximate it.*
- Vacuum world (slide 4): 2 rooms A/B, dirty/clean; sensors = position + status; actuators = left, right, vacuum. The table over percept histories grows exponentially → intractable for real agents.

## Rationality (slide 5)
A rational agent, at every moment, picks the action that **maximizes the expected value of a performance measure**, given its percept history and built-in knowledge. Includes exploring to gather information and learning from percepts.

**Performance measure**: external criterion set by the *designer*, not the agent. ⚠️ "You get what you ask for": a poor or incomplete measure yields unintended behaviour (AIMA example: reward dirt cleaned per time → agent dumps and re-cleans) (unverified).

### AIMA grounding ([[aima-ch02-intelligent-agents]])
- **Definition (p. 58):** *for each possible percept sequence, a rational agent should select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has.* Rationality at any time depends on four things: performance measure, prior knowledge of the environment, available actions, percept sequence to date.
- **Rational ≠ omniscient ≠ perfect** (pp. 58–59): rationality maximizes *expected* performance; perfection maximizes *actual* performance (crossing the street when a cargo door falls from a plane). It requires **information gathering** (look before crossing) and **learning**, and should be **autonomous** (dung beetle, sphex wasp lack it) (pp. 59–60).
- **Performance measures** evaluate sequences of *environment states*, not agent behavior; dirt-cleaned-per-shift can be gamed (dump and re-clean), so award clean squares per time step (p. 57). It may be unknown to the designer or user → the agent should be uncertain about it and learn (pp. 57–58, 65).
- The vacuum agent is rational under specific assumptions (1 point per clean square per step over 1000 steps; known geography; unknown dirt; only Left/Right/Suck; correct percepts), but *irrational* if moves cost points (it oscillates after cleaning) (p. 58).
- Vacuum world Fig. 2.3: the percept-sequence table is unbounded unless length is bounded; the reflex program needs only 4 percept cases instead of 4^T (p. 67).
- "Agent = architecture + program" (p. 65); the agent concept is an analysis tool, not a strict classification (calculator example, p. 56).
- Book-level "standard model" of AI: build agents that do the right thing for the objective we supply ([[ai-foundations-and-approaches]]).

## Related
[[peas]], [[task-environment-properties]], [[agent-types]], [[learning-agents]], [[problem-solving-agents]], [[turing-test]] (acting humanly vs. acting rationally), [[ai-foundations-and-approaches]]

## Exam angles
- Distinguish agent function/program; define rationality precisely.
- Give a performance measure for the vacuum world and critique it.
