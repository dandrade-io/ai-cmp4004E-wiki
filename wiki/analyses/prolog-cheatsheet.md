---
title: Prolog Cheatsheet
type: analysis
tags: [prolog, exam-prep]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Cheatsheet (exam-oriented)

**Core equation:** Algorithm = Logic + Control ([[robert-kowalski]]). Prolog = [[horn-clauses]] + backward chaining + [[unification]] ([[prolog]]).

## Syntax ([[prolog-syntax-and-terms]])
`head :- b1, b2.` · fact `f(a).` · query `?- f(X).` · `,` and · `;` or · Uppercase/`_` var · lowercase atom · `father/2` name/arity.

## Execution ([[sld-resolution-and-backtracking]])
Leftmost goal → first matching clause in file order → replace by body → fail ⇒ backtrack. Base case first; recurse last; no left recursion; `:- table p/2.` cures loops.

## Operators ([[prolog-arithmetic]])
`=` unify · `\=` not unifiable · `==` identical · `is` evaluate · `=:=` `=\=` `<` `>` `=<` `>=` · `mod`, `**`.

## Unify quick ([[unification]])
`f(a,Y)=f(X,b)` → X=a,Y=b · `[H|T]=[1,2,3]` → H=1,T=[2,3] · `X=f(X)` cyclic (no occurs check).

## Lists ([[prolog-lists-and-recursion]])
`[H|T]`; `member append length nth0 reverse msort sum_list last exclude`. `append(X,Y,L)` splits.

## Collecting ([[prolog-built-ins]])
`findall` (dups, [] if none) · `setof` (sorted, fails if none, `V^G`) · `aggregate_all(count,G,N)` · `forall` · `between` · `select` · `permutation`.

## Control ([[prolog-cut]], [[negation-as-failure]])
`\+ G` = not provable (CWA; bind first). `!` commits; keep outputs out of head before cut. Prefer `( C -> T ; E )`.

## Known traps
- `X = 3+4` ≠ 7. `X is Y+1` unbound error. `<=` doesn't exist.
- `isPerm` = set equality bug. Naive `fibo` exponential.
- Missing `.`, singleton warnings, `Hector` vs `hector`.

## Tools ([[swi-prolog]], [[prolog-debugging-and-common-mistakes]])
`swipl f.pl`, `[f].`, `listing(p/2)`, `trace/notrace`, `time(G)`, `run_tests`.

## Numbers
N-Queens solutions: 4→2, 5→10, 6→4, 7→40, 8→92, 9→352, 10→724 ([[n-queens-prolog]]).
