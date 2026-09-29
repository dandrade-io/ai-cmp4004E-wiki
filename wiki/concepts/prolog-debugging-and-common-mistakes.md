---
title: Prolog Debugging and Common Mistakes
type: concept
tags: [prolog, debugging]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Debugging and Common Mistakes (slide 28)

## Tracing
`trace/0` enables the **four-port debugger**: each goal is reported as **Call, Exit, Redo, Fail**. `notrace/0` turns it off; `gtrace/0` is graphical ([[swi-prolog]]).
```prolog
?- trace, factorial(3, X).
   Call: (10) factorial(3, _2312)
   Call: (11) 3>0
   Exit: (11) 3>0
   ...
   Exit: (10) factorial(3, 6)
X = 6.
```

## Mistakes everyone makes first
| Mistake | Effect |
|---|---|
| Missing period | clause merges with next |
| `=` instead of `is` | `X = 3+4` binds a term ([[prolog-arithmetic]]) |
| Singleton variable warnings | usually a typo, or should be `_` |
| Left recursion | loops before reaching a fact ([[sld-resolution-and-backtracking]]) |
| Uppercase where atom meant | `parent(Hector, ana)` = "some Hector" |
| `\+` on unbound variables | bind first ([[negation-as-failure]]) |

Warnings are real feedback: in `isEven([X|XS], Y)`, `X` is singleton → `_` ([[prolog-lists-and-recursion]]). Lab files must load cleanly: singleton warnings cost points ([[prolog-lab-01]]).

## Exam angles
Read a trace and identify the port; spot the bug in a short program; explain a singleton warning.
