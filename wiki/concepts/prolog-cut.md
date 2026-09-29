---
title: Prolog Cut
type: concept
tags: [prolog, control]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Cut (`!`)

## Definition (slide 23)
`!` **commits** to the choices made so far in the clause: Prolog won't retry goals to its left, nor try later clauses of this predicate. It buys speed but **destroys the declarative reading**. Prefer `( Cond -> Then ; Else )`.

## The classic bug
```prolog
max(X, Y, X) :- X >= Y, !.     % WRONG: output sits in the head
max(_, Y, Y).
?- max(5, 3, 3).   % true.   -- should be false!

max(X, Y, M) :- X >= Y, !, M = X.   % right
max(_, Y, Y).

max2(X, Y, M) :- ( X >= Y -> M = X ; M = Y ).   % no cut at all
```
Why wrong: the call `max(5,3,3)` fails to match head 1 (`X=5` vs `3`), so falls to clause 2 (`max(_,3,3)`) which succeeds. Unify output *after* the cut.

## Pitfalls
Cuts make clause order semantically significant; "red cuts" change meaning. (unverified terminology)

## Related
[[negation-as-failure]], [[sld-resolution-and-backtracking]].

## Exam angles
Explain what is cut off; fix `max/3`; rewrite with if-then-else.
