---
title: "AIMA Ch. 8 — First-Order Logic"
type: source
tags: [logic, knowledge-representation, book]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA 4th ed. (Global), Chapter 8 — First-Order Logic (pp. ~268–296)

Book: [[russell-norvig]]. Course slides: [[slides-xx-logic-programming-prolog]] (slides 2, 7).

## Summary
Propositional logic lacks the expressive power to describe environments with many objects concisely. FOL borrows from natural language (objects, relations, functions) while staying context-free and unambiguous (§8.1).

## 8.2 Syntax and semantics (pp. 274–283)
- **Model** = a nonempty *domain* of objects plus interpretations of constant, predicate and function symbols (§8.2.1–8.2.2, pp. 274–277).
- **Terms** refer to objects; a complex term such as LeftLeg(John) is "just a complicated kind of name", not a subroutine call (p. 277). **Atomic sentences** = predicate(term…) or term = term. Complex sentences reuse propositional connectives.
- **Quantifiers** (p. 278): ∀x P is true if P holds under every extended interpretation; ∃x P if at least one. Natural pairings: ∀ with ⇒, ∃ with ∧. Typical mistakes: ∀x with ∧ (too strong) and ∃x with ⇒ (too weak — true if any object falsifies the antecedent). De Morgan duality between ∀ and ∃.
- **Equality** (p. 282); **database semantics** (p. 282): unique-names assumption + closed-world assumption + domain closure → makes sentences like "Richard has exactly one brother" straightforward. "Database semantics is also used in logic programming" — i.e. [[prolog]] ([[negation-as-failure]]).

## 8.3 Using FOL (pp. 283–289)
TELL/ASK assertions and queries (substitutions/bindings as answers); **kinship domain** (parent, grandparent, sibling axioms — the same domain as slide 12's family.pl in [[prolog-syntax-and-terms]]); numbers, sets and lists; the wumpus world in FOL ([[wumpus-world]]).

## 8.4 Knowledge engineering (pp. 289–296)
Process: identify the task, assemble knowledge, decide on vocabulary, encode general knowledge, encode the instance, query, debug. Worked example: electronic circuits.

## Derived / updated pages
[[propositional-vs-first-order-logic]], [[first-order-inference]], [[prolog-syntax-and-terms]] (cross-link only).

## Slide vs. book
- Slide 7: "Prolog uses uppercase for variables, the opposite of the textbook" — the book (§9.4.2, p. 312) confirms *Prolog* is the reverse of the book's convention (book: lowercase variables, capitalised constants).
