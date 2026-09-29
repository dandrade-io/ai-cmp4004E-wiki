---
title: Propositional vs First-Order Logic
type: concept
tags: [logic, knowledge-representation]
sources: [raw/slides/XX_Logic Programming with Prolog.pptx, raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# Propositional vs First-Order Logic

## Comparison (slide 2)
| | Propositional | First-order (FOL) |
|---|---|---|
| Building blocks | propositional symbols, connectives, truth tables | constants, variables, predicates, quantifiers |
| Talks about objects? | No | Yes |
| Can say "every"? | No | Yes (∀, ∃) |
| Decidability | Decidable (finite models; co-NP-hard, [[model-checking-and-entailment]]) | Entailment **semidecidable**: an algorithm says yes to every entailed sentence, none says no to every non-entailed one (AIMA §9.1, p. 299; Turing/Church 1936) |

> ⚠️ Nuance: slide 2 writes "Undecidable" for FOL while slide 5 says "semi-decidable". Both are true: FOL is undecidable *and* semidecidable (validity/entailment can be confirmed but not always refuted). Function-free definite clauses (**Datalog**) are decidable (AIMA p. 305).

## Intuition
Propositional logic treats facts as atomic true/false symbols (`Rain`, `Wet`). FOL looks inside: `Sells(West, m1, Nono)`, `∀x American(x) ∧ … ⇒ Criminal(x)`.

## Why it matters here
Propositional logic can only be *checked* (truth tables). To *run* logic, restrict FOL to [[horn-clauses]], which gives [[prolog]] ([[logic-programming]]).

Semantics (AIMA Ch. 8): propositional models are truth assignments; FOL models contain a nonempty **domain of objects** with interpretations of constants, predicates and functions ([[aima-ch08-first-order-logic]]). Quantifier pitfalls: ∀ pairs with ⇒, ∃ with ∧ (∀x with ∧ is too strong; ∃x with ⇒ too weak). Prolog adopts **database semantics** (unique names, closed world, domain closure) rather than standard FOL semantics.

Note the state-representation link: the [[agent-types]] material distinguishes atomic, factored and structured representations; FOL is the structured one (objects and relations).

## Pitfalls
- Case convention flips in Prolog: uppercase = variable, lowercase = constant, the opposite of the textbook ([[prolog-syntax-and-terms]]).

## Related
[[cnf-and-resolution]], [[forward-and-backward-chaining]].

## Exam angles
- Give a sentence expressible in FOL but not propositional logic ("every…").
- State decidability of each.

Inference: [[first-order-inference]], [[aima-ch07-logical-agents]].
