---
title: Prolog Lists and Recursion
type: concept
tags: [prolog, recursion, lists]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Lists and Recursion

## Lists (slide 19)
A list is `[]` or `[Head|Tail]`; `[1,2,3]` is `[1|[2|[3|[]]]]`. Relations run backwards: `append(X, Y, [1,2,3])` enumerates all splits.

```prolog
mymember(X, [X|_]).
mymember(X, [_|T]) :- mymember(X, T).
myappend([], L, L).
myappend([H|T], L, [H|R]) :- myappend(T, L, R).
mylen([], 0).
mylen([_|T], N) :- mylen(T, N0), N is N0 + 1.
```
Built-ins already exist: `member/2, append/3, length/2, nth0/3, reverse/2, msort/2, sum_list/2, last/2, exclude/3`.

## Factorial (slide 17)
```prolog
factorial(0, 1).
factorial(A, B) :- A > 0, C is A - 1, factorial(C, D), B is A * D.
```
Base case is a fact; `A > 0` avoids overlap (a choicepoint still survives); `C is A-1` must precede the call. Exercises: `?- factorial(X, 120).` (fails/errors: `A > 0` with unbound `A`), and an accumulator version.

## Fibonacci (slide 18)
Naive `fibo/2` is exponential (proof tree re-proves subgoals; `fibo(25,_)` = 1,092,530 inferences). Accumulator version is linear; or memoise with `:- table fibo/2.`
```prolog
fib(N, F) :- fib_(N, 1, 1, F).
fib_(0, A, _, A).
fib_(N, A, B, F) :- N > 0, N1 is N - 1, C is A + B, fib_(N1, B, C, F).
```

## isEven / isOdd (slide 20)
Mutual recursion on list length. Singleton warnings say rename to `_`. Idiomatic: succeed/fail instead of returning `true/false`.
```prolog
even_length([]).
even_length([_|T]) :- odd_length(T).
odd_length([_|T])  :- even_length(T).
```

## isPerm bug (slide 21)
```prolog
isPerm(X, Y) :- isInc(X, Y), isInc(Y, X).   % checks set equality!
?- isPerm([1,1,2], [1,2,2]).   % true — WRONG
```
Ignores multiplicity and length. Fix: `is_perm(X,Y) :- msort(X,S), msort(Y,S).` or `permutation/2`.

## Pitfalls
Left recursion ([[sld-resolution-and-backtracking]]); `=` vs `is` ([[prolog-arithmetic]]).

## Exam angles
Trace `mylen`; explain why naive fibo is exponential; find the isPerm counterexample. Related: [[prolog-built-ins]], [[prolog-binary-search-tree]].
