---
title: Prolog Syntax and Terms
type: concept
tags: [prolog, syntax]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Prolog Syntax and Terms

## FOL → Prolog: four conventions (slide 7)
1. **Implication is backwards**: `A ∧ B ⇒ C` → `C :- A, B.`
2. **Case inverted**: Uppercase = variable, lowercase = constant (opposite of textbook).
3. **Quantifiers implicit**: every variable is universally quantified.
4. **Punctuation**: `,` = and, `;` = or, every clause ends with `.`

## Everything is a term (slide 12)
- Atom: `ana`, `prolog`, `'Ana María'`
- Number: `42`, `3.14`
- Variable: starts uppercase or `_`: `X`, `Qs`
- Compound: `parent(hector, ana)`, `[1,2,3]`

Fact `parent(hector, ana).` · Rule `father(X,Y) :- parent(X,Y), male(X).` · Query `?- father(hector, Who).`

**Name/arity identify a predicate**: `father/2` ≠ `father/3`.

## Example: family.pl
```prolog
parent(hector, ana).   parent(hector, luis).
parent(ana, sofia).    parent(luis, diego).
male(hector). male(luis). male(diego).
female(ana).  female(sofia).
father(X, Y) :- parent(X, Y), male(X).
grandparent(X, Z) :- parent(X, Y), parent(Y, Z).
sibling(X, Y) :- parent(P, X), parent(P, Y), X \= Y.
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```

## Querying (slide 13)
`;` gives next solution; a trailing `.` means no more. `false.` after a solution means a choicepoint survived. See [[prolog-built-ins]] for `findall`/`setof`.

## Pitfalls
`parent(Hector, ana)` means "some Hector"; missing period merges clauses ([[prolog-debugging-and-common-mistakes]]).

## Related
[[unification]], [[prolog]].

## Exam angles
- Translate a FOL rule to Prolog.
- Identify atom/variable/compound in a given string.
- Why `sibling` needs `X \= Y`.
