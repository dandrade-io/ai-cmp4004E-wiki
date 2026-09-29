---
title: Prolog Built-ins
type: concept
tags: [prolog, reference]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Built-ins Worth Memorising (slides 13, 24)

## Collecting answers
- `findall(T, G, L)` — every solution, duplicates kept, order kept; `[]` if none.
- `bagof/setof` — grouped; `setof` sorts + dedups, **fails** when nothing matches. `Var^Goal` = "any Var will do".
- `aggregate_all(count, G, N)` — count without building a list.
- `forall(C, A)` — A holds for every solution of C.

```prolog
?- findall(D, ancestor(hector, D), Ds).   % Ds = [ana, luis, sofia, diego].
?- setof(P, C^parent(P, C), Parents).     % Parents = [ana, hector, luis].
```

## Generating and choosing
- `between(L, H, X)` — X ranges L..H on backtracking.
- `select(X, L, Rest)` — pick X out of L.
- `permutation(L, P)` — every rearrangement.
- `length(L, N)` — also builds N fresh variables.

## Measuring / inspecting
- `msort/2` (keeps duplicates), `sort/2` (removes duplicates).
- `format("~w~n", [X])`, `time(Goal)` (runtime + inferences), `listing/1`, `make/0`.

## Portability
ISO covers core: terms, control, arithmetic, `is/2`, `findall/3`. Most list/aggregation/I-O predicates are library, not ISO (slide 9).

## Pitfalls
`findall` vs `setof` on empty results; `sort/2` silently dedups.

## Related
[[prolog-lists-and-recursion]], [[n-queens-prolog]], [[swi-prolog]].

## Exam angles
Predict output of `findall` vs `setof`; count solutions with `aggregate_all`.
