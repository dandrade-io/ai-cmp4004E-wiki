---
title: N-Queens in Prolog
type: concept
tags: [prolog, search, backtracking]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# N-Queens in Prolog (slides 25–27)

Place N queens on an N×N board so none attack. **Representation does half the work**: `Qs` is a permutation of `1..N`; the i-th element is the column of the queen in row i. One per row by construction, distinct values ⇒ one per column; only diagonals remain.

```prolog
queens(N, Qs) :- range(1, N, Ns), queens(Ns, [], Qs).
queens([], Qs, Qs).
queens(UnplacedQs, SafeQs, Qs) :-
    select(Q, UnplacedQs, NewUnplaced),
    \+ threat(Q, SafeQs),
    queens(NewUnplaced, [Q|SafeQs], Qs).
threat(X, Xs) :- threat(X, 1, Xs).
threat(X, N, [Y|_]) :- X is Y + N ; X is Y - N.
threat(X, N, [_|Ys]) :- N1 is N + 1, threat(X, N1, Ys).
range(M, N, [M|Ns]) :- M < N, M1 is M + 1, range(M1, N, Ns).
range(N, N, [N]).
```
`select/3` is the choicepoint; `threat/2` = shared diagonal. Uses [[negation-as-failure]] (safe: `Q` and `SafeQs` are bound).

## Solution counts
| N | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|
| sols | 2 | 10 | 4 | 40 | 92 | 352 | 724 |
N=2, 3 have none. `findall(Q, queens(8,Q), L), length(L,N).` → 92.

## Generate & test vs test as you go
```prolog
queens_perm(N, Qs) :- range(1,N,Ns), permutation(Ns, Qs), safe(Qs).   % generate whole board, then test
queens_bt(N, Qs) :- range(1,N,Ns), place(Ns, [], Qs).                 % prune as you build
```
Inferences to enumerate all solutions (SWI 9.2.9):
| N | gen&test | interleaved | ratio |
|---|---|---|---|
| 4 | 425 | 200 | 2.1x |
| 6 | 15,358 | 3,090 | 5.0x |
| 8 | 1,058,230 | 61,770 | 17.1x |
| 10 | 113,230,594 | 1,468,869 | 77.1x |

Interleaving prunes early — same idea as [[constraint-satisfaction-problems]] (backtracking with early constraint checks) and [[depth-first-search]].

## Exam angles
Why is interleaved faster? Explain the representation; count solutions for N=6.
Related: [[prolog-built-ins]], [[sld-resolution-and-backtracking]].
