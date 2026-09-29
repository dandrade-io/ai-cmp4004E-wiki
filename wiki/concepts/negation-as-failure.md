---
title: Negation as Failure
type: concept
tags: [prolog, logic]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx]
updated: 2026-09-29
---
# Negation as Failure

## Definition (slide 23)
`\+ Goal` succeeds when Prolog **fails to prove** `Goal`. It equals logical negation only under the **closed-world assumption (CWA)**: whatever is not derivable is taken to be false.

```prolog
?- \+ parent(sofia, _).        % true.  no children recorded
?- \+ parent(X, ana).          % false. some X does satisfy it
?- X = sofia, \+ parent(X, _). % X = sofia.  bind first, then negate
```

## Rule of thumb
Only negate goals whose variables are already bound. `\+ parent(X, ana)` with unbound `X` does not mean "no X is a parent of ana" as one might read it in FOL... it means "not provable for some X" — the query fails because a proof exists.

## CWA link
[[prolog-lab-01]] asks what the closed-world assumption claims that you never wrote down (e.g., that two people not recorded as parent/child are not related).

## Pitfalls
Non-monotonic; sensitive to goal order; unbound variables give surprising answers.

## Related
[[prolog-cut]] (negation is implemented with cut-like commitment (unverified)), [[horn-clauses]] (Horn clauses cannot express classical negation).

## Exam angles
Difference between `\+` and logical ¬; why bind before negating; state the CWA.
