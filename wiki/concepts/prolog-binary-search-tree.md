---
title: Prolog Binary Search Tree
type: concept
tags: [prolog, data-structures]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Binary Search Tree

## Idea (slide 22)
Data structures are just **terms**: a tree is `empty` or `node(Key, Left, Right)`. No class, constructor or allocation; pattern matching takes it apart. Terms are immutable, so `insert/3` **relates** an old tree to a new one sharing most structure.

```prolog
member2(K, node(K, _, _)).
member2(K, node(N, S, _)) :- K < N, member2(K, S).
member2(K, node(N, _, T)) :- K > N, member2(K, T).

insert(N, empty, node(N, empty, empty)).
insert(N, node(K, L, R), node(K, M, R)) :- N < K, insert(N, L, M).
insert(N, node(K, L, R), node(K, L, M)) :- N > K, insert(N, R, M).

?- insert(5, empty, T1), insert(3, T1, T2), insert(8, T2, T3).
T3 = node(5, node(3, empty, empty), node(8, empty, empty)).
?- member2(3, T3).   % true.
```

## Notes
- The original lab file adds clauses for empty children; they are subsumed because [[unification]] treats `empty` like any term.
- Inserting an existing key fails (neither `<` nor `>` holds) — duplicates aren't handled. (unverified inference from the code)
- Comparisons use [[prolog-arithmetic]] operators.

## Related
[[prolog-lists-and-recursion]], [[prolog-syntax-and-terms]].

## Exam angles
Write `insert` for a given sequence and draw the tree; explain immutability; add an in-order traversal.
