---
title: SWI-Prolog
type: concept
tags: [prolog, tools]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# SWI-Prolog (slides 9–11, 29)

"Prolog is the language; SWI-Prolog is the implementation." Free, open source, macOS/Windows/Linux. Developed since 1987 at the University of Amsterdam. Stable series 10.x; course uses 9.2 (≥9.2 is fine).

## Why this one
Readable errors, real debugger (`trace/0`, `gtrace/0` — [[prolog-debugging-and-common-mistakes]]), large library incl. `library(clpfd)`, **tabling** ([[sld-resolution-and-backtracking]]), SWISH in-browser (swish.swi-prolog.org).

## Install
```
brew install swi-prolog                 # macOS
winget install SWI-Prolog.SWI-Prolog    # Windows (keep "add to PATH")
sudo apt install swi-prolog             # Linux (Ubuntu build is older; use SWI PPA)
swipl --version
```
Commands: `swipl` toplevel; `swipl file.pl` load + toplevel; `swipl-win` editor/console.

## First session
```prolog
?- X is 2 + 3 * 4.          % X = 14.
?- [user].                  % type clauses in; |: prompt; ^D ends
|: likes(ana, prolog).
|: likes(luis, X) :- likes(ana, X).
?- likes(luis, W).          % W = prolog.
?- consult('queens.pl').    % or ?- [queens].
?- listing(range/3).
?- halt.
```
Prompts: `?-` wants a query; `|:` is reading clauses. `;` next solution, Enter stops. Forgetting the period is the classic first error.

## Testing with plunit (slide 29)
```prolog
:- begin_tests(family).
test(mother_of_ana) :- mother(rosa, ana), !.
test(no_self_sibling, [fail]) :- sibling(X, X).
:- end_tests(family).
?- run_tests.     % All 24 tests passed
```
Load check: `swipl -g true -t halt file.pl`.

## Exam angles / related
Know `consult`, `listing`, `halt`, `run_tests`. See [[prolog-lab-01]], [[prolog]].
