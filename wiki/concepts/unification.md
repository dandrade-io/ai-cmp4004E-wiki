---
title: Unification
type: concept
tags: [prolog, logic, inference]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Unification

## Definition (slide 14)
Given two terms, find the **substitution** that makes them identical — or fail. Pattern matching in both directions: neither side is "the input".

## Rules
- Atoms and numbers unify only with themselves.
- A variable unifies with anything, then stays bound.
- Compound terms unify if functor and arity match and arguments unify pairwise.
- **No occurs check** by default.

```prolog
?- f(a, Y) = f(X, b).        % X = a, Y = b.
?- [H|T] = [1, 2, 3].        % H = 1, T = [2, 3].
?- f(a) = g(a).              % false (different functors)
?- X = f(X).                 % X = f(X). cyclic term
?- unify_with_occurs_check(X, f(X)).   % false.
```

## AIMA formalisation (§9.2.1, p. 301)
UNIFY(p,q) = θ with SUBST(θ,p) = SUBST(θ,q). Examples:
- UNIFY(Knows(John,x), Knows(John,Jane)) = {x/Jane}
- UNIFY(Knows(John,x), Knows(y,Bill)) = {x/Bill, y/John}
- UNIFY(Knows(John,x), Knows(y,Mother(y))) = {y/John, x/Mother(John)}
- UNIFY(Knows(John,x), Knows(x,Elizabeth)) = **failure** — a name clash, avoided by **standardizing apart** (rename x→x₁₇ → {x/Elizabeth, x₁₇/John}). Prolog renames clause variables automatically on each use.

Several unifiers may exist; the **most general unifier (MGU)** places the fewest restrictions and is unique up to renaming: for Knows(John,x) vs Knows(y,z) it is {y/John, x/z}, not {y/John,x/John,z/John}. The **occurs check** (x may not unify with a term containing x) is omitted by Prolog → can build cyclic terms/unsound inferences "almost never a problem in practice" (p. 312).

## Role
Unification is what connects a goal to a clause head in [[sld-resolution-and-backtracking]]; it is how Prolog passes data and returns answers.

## Pitfalls
- `=/2` only unifies; it evaluates nothing ([[prolog-arithmetic]]).
- Skipping the occurs check is faster but allows cyclic terms.

## Related
[[prolog]], [[prolog-syntax-and-terms]].

## Exam angles
- Unify two given terms and give the substitution.
- Why does `X = f(X)` succeed in Prolog but is invalid logically?
- `==` (identity) vs `=` (unifiable) vs `\=` (not unifiable).

Source: [[aima-ch09-inference-in-first-order-logic]]. See [[first-order-inference]].
