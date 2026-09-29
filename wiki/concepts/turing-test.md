---
title: Turing Test
type: concept
tags: [history, foundations]
sources: [raw/slides/01_Introduction to Artificial Intelligence.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Turing Test (1950)

**Intuition.** Replace "can machines think?" with an operational test based on conversation.

**Setup (slide 5).** Two humans and one computer. The interrogator is isolated from both and asks questions through a text terminal, then decides which is the computer. If the interrogator cannot identify the computer, the machine is deemed intelligent. It "attempts to provide an operational and satisfactory definition of intelligence".

## Discussion
- Tests behaviour, not internal understanding; text-only avoids physical cues. AIMA §1.1.1 (p. 20): passing requires **natural language processing, knowledge representation, automated reasoning, machine learning**; the **total Turing test** adds a video signal and object manipulation, requiring **computer vision, speech recognition and robotics**. Those six disciplines "compose most of AI" ([[aima-ch01-introduction]]).
- It is the "acting humanly" approach in AIMA's 2×2 ([[ai-foundations-and-approaches]]); contrast with "acting rationally" → [[rational-agents]]. AIMA's argument: aeronautics did not succeed by imitating pigeons, so AI researchers study underlying principles rather than trying to pass the test.
- Turing's 1950 paper "Computing Machinery and Intelligence" also introduced machine learning, genetic algorithms and reinforcement learning ideas (AIMA p. 36).
- Criticisms: Searle's Chinese Room; imitation ≠ intelligence (unverified).

## Related
[[history-of-ai]], [[slides-01-introduction-to-ai]]

## Exam angles
- Describe participants and pass criterion.
- Why is it "operational"? Limitations of a behavioural definition.
