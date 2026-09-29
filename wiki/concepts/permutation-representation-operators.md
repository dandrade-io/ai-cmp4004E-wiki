---
title: Permutation Representation and Operators
type: concept
tags: [evolutionary, permutation, tsp]
sources: ["raw/books/A.E. Eiben_ J.E. Smith - Introduction to Evolutionary Computing-Springer (2015).pdf"]
updated: 2026-09-29
---
# Permutation representation and its operators

Used when the solution is an ordering: **order-based** (scheduling: the relative order matters) or **adjacency-based** (TSP: links between neighbours matter; tours are equivalent under rotation/reflection). Operators must **preserve the permutation property** (each value once) — book §4.5, pp.67–75 ([[eiben-ch04-representation-variation]]). TSP has (n−1)! tours (n = 30 ⇒ ~10³²).

Two encodings: i-th element = the event at position i (common) or i-th element = position of event i.

## Mutation (probability applies to the whole chromosome)
Swap · Insert · Scramble · **Inversion** (reverse a substring; breaks only 2 links — the natural move for adjacency problems, the basis of 2-opt).

## Recombination — worked on the book's parents
P1 = [1 2 3 4 5 6 7 8 9], P2 = [9 3 7 8 2 6 5 1 4], cut segment = positions 4–7.
- **PMX** (partially mapped): copy P1 segment [4 5 6 7]; place P2's uncopied segment elements 8 and 2 by following the mapping (8 → slot of 4 in P2 = pos 9; 2 → 5 → 7 → pos 3); fill the rest from P2 ⇒ **[9 3 2 4 5 6 7 1 8]**. Good for adjacency, but violates *respect* (edge 7–8 common to both parents is lost).
- **Order crossover** (Davis; order-based): copy segment, then fill from the second cut point in P2's order, skipping used values (wrap-around): P2 from pos 8 = 1 4 9 3 7 8 2 6 5 → unused 1 9 3 8 2 ⇒ **[3 8 2 4 5 6 7 1 9]**.
- **Cycle crossover** (absolute position): cycles of aligned positions: {1,9,4,8}, {2,3,7,5}, {6}; take alternate cycles from each parent ⇒ **[1 3 7 4 2 6 5 8 9]**.
- **Edge-3 crossover** (adjacency, preserves common edges): build an *edge table* (adjacency lists, '+' = edge in both parents), pick next element = common edge, else the one with the shortest list, ties random. Book table for these parents: 1: 2,5,4,9 · 2: 1,3,6,8 · 3: 2,4,7,9 · 4: 1,3,5,9 · 5: 1,4,6+ · 6: 2,5+,7 · 7: 3,6,8+ · 8: 2,7+,9 · 9: 1,3,4,8 ⇒ one child, e.g. [1 5 6 2 8 7 3 9 4].

## Example use
8-queens: genotype = permutation of rows (one queen per column *and* row) so only diagonals can be violated; swap mutation + cut-and-crossfill crossover (book Fig. 3.3). Contrast with [[n-queens-prolog]].

Related: [[crossover-and-mutation]], [[genetic-algorithms]].

## Exam angles
- Perform PMX/order/cycle crossover on given parents; say which fits scheduling vs TSP.
