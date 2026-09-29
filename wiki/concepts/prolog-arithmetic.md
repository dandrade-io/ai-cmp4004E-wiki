---
title: Prolog Arithmetic (is/2 vs =/2)
type: concept
tags: [prolog, arithmetic]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Arithmetic: `is/2` is not `=/2`

## Idea (slide 16)
- `=/2` **unifies** two terms; evaluates nothing.
- `is/2` **evaluates** the right side, then unifies with the left.
- The right side's variables must already be bound, so arithmetic is **one-way**.

```prolog
?- X = 3 + 4.        % X = 3+4.   a term, not a number
?- X is 3 + 4.       % X = 7.
?- 3 + 4 = 7.        % false.     structures differ
?- 3 + 4 =:= 7.      % true.      values compared
?- X is Y + 1.       % ERROR: Arguments are not sufficiently instantiated
?- X is 2 ** 10, Y is 17 mod 5.   % X = 1024, Y = 2.
```

## Comparison operators
| Op | Meaning |
|---|---|
| `=:=` / `=\=` | arithmetic equal / not equal |
| `<  >  =<  >=` | note `=<` and `>=`, never `<=` |
| `==` | term identity |
| `\=` | not unifiable |

Integers are unbounded: `factorial(20, X)` gives `2432902008176640000` (slide 17).

## Pitfalls
Using `=` instead of `is`; wrong order of goals so RHS is unbound; writing `<=`.

## Related
[[prolog-lists-and-recursion]], [[unification]], [[prolog-debugging-and-common-mistakes]].

## Exam angles
- Predict the result of `X = 1+2`, `X is 1+2`, `1+2 =:= 3`, `1+2 == 3`.
- Why does `factorial` put `C is A - 1` before the recursive call?
