---
title: PEAS
type: concept
tags: [agents]
sources: [raw/slides/03_Intelligent Agents.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# PEAS (Task Environment Specification)

**Slide 6.** Specify the task environment of an agent with:
- **P**erformance measure — success criterion
- **E**nvironment — the world the agent operates in
- **A**ctuators — mechanisms to act
- **S**ensors — mechanisms to perceive

(Slide 7 is a figure, likely an example table.)

## Examples from AIMA Ch. 2 (Fig. 2.4–2.5, pp. 61–62; [[aima-ch02-intelligent-agents]])
| Agent | Performance | Environment | Actuators | Sensors |
|---|---|---|---|---|
| Taxi driver | safe, fast, legal, comfortable trip, maximize profits, minimize impact on other road users | roads, other traffic, police, pedestrians, customers, weather | steering, accelerator, brake, signal, horn, display, speech | cameras, radar, speedometer, GPS, engine sensors, accelerometer, microphones, touchscreen |
| Medical diagnosis | healthy patient, reduced costs | patient, hospital, staff | display of questions, tests, diagnoses, treatments | touchscreen/voice entry of symptoms and findings |
| Satellite image analysis | correct categorization of objects, terrain | orbiting satellite, downlink, weather | display of scene categorization | high-res digital camera |
| Part-picking robot | % parts in correct bins | conveyor belt with parts; bins | jointed arm and hand | camera, tactile and joint-angle sensors |
| Refinery controller | purity, yield, safety | refinery, raw materials, operators | valves, pumps, heaters, stirrers, displays | temperature, pressure, flow, chemical sensors |
| Interactive English tutor | student's score on test | set of students, testing agency | display of exercises, feedback, speech | keyboard entry, voice |

AIMA notes the taxi's performance goals conflict (speed vs. safety vs. profit) so trade-offs are needed; the more restricted the environment (e.g. no snow, drive on one side) the easier the design; virtual environments (softbots) can be as complex as real ones. "In designing an agent, the first step must always be to specify the task environment as fully as possible" (p. 60).

## Use
First step of agent design; forces explicit choice of the performance measure ([[rational-agents]]) and then classification via [[task-environment-properties]].

## Exam angles
- Write PEAS for a given agent (vacuum, chess player, medical diagnosis, recommender).
- Sensors vs. actuators confusion.
