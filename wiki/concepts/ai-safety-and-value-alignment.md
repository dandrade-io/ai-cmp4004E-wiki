---
title: AI Safety and the Value Alignment Problem
type: concept
tags: [ethics, safety, alignment]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AI Safety and Value Alignment

**Intuition.** A utility maximizer does what you *asked for*, not what you *meant*. Safety means designing for failure and for mis-specified objectives (AIMA §28.3.7, p. 1052–1056).

## Safety engineering (p. 1052–1053)
- **FMEA** (failure modes and effects analysis): enumerate how each component can fail, trace consequences, redesign if severe.
- **Fault tree analysis:** AND/OR tree of failures with root-cause probabilities.
- Software *correctness* (meets spec) ≠ *safety* (spec anticipates failure modes and degrades gracefully; e.g. backup computer with separate power).

## Objective-function failures (p. 1053–1055)
- **Unintended side effects:** coffee robot knocks over lamps. Remedy: **low impact** – maximise utility minus a weighted measure of changes to the world (like regularization; "first, do no harm").
- **Externalities:** costs not in the utility function (greenhouse gases); internalise them (carbon tax) or apply Ostrom's commons principles.
- **Specification gaming** (Krakovna's catalogue): agents exploit simulator bugs, crash/pause the game to avoid losing, evolved creatures that were tall and "moved" by falling over (a genetic-algorithm example, cf. [[genetic-algorithms]]).
- **Value alignment / King Midas problem:** make sure what we ask for is what we really want. Writing all the rules is hopeless ("loophole-free tax law").

## Approaches (p. 1054–1056)
- Learn from human behaviour: **imitation learning** (repeats human mistakes) vs **inverse reinforcement learning** (infer the utility function; can exceed humans, e.g. AlphaZero-style).
- **Assistance games:** robot uncertain about human preferences → acts cautiously, asks questions, accounts for human imperfection (lies, self-destructive acts, limited introspection).
- Testing: AI Safety Gridworlds.

## Connection to the course
Slide on rational agents: "you get what you ask for… a poor measure produces unintended behavior" ([[rational-agents]], [[slides-03-intelligent-agents]]).

## Related
[[ai-ethics-and-safety]], [[fairness-and-bias]], [[agent-types]] (utility-based agent), [[aima-ch28-philosophy-ethics-safety]]

## Exam angles
- Define value alignment and give the King Midas example.
- Explain low-impact design and specification gaming with an example.
- Difference between correctness and safety.
