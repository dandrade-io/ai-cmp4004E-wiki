---
title: "AIMA Ch. 12 – Quantifying Uncertainty"
type: source
tags: [source, book, probability]
sources: [raw/books/Stuart J. Russell, Peter Norvig - Artificial Intelligence_ A Modern Approach, Global Edition-Pearson (2021).pdf]
updated: 2026-09-29
---
# AIMA (4th ed., Global) – Chapter 12: Quantifying Uncertainty

Book pages 403–428 (PDF pages ≈ book page + 1). Book-page numbers are used in citations. Author entity: [[russell-norvig]].

## Section map
| § | Title | Book p. | Wiki page |
|---|---|---|---|
| 12.1 | Acting under uncertainty (laziness, ignorance; decision theory: probability + utility) | 403 | [[probability-basics]] |
| 12.2 | Basic probability notation | 406 | [[probability-basics]] |
| 12.3 | Inference using full joint distributions | 413 | [[probability-basics]] |
| 12.4 | Independence | 415 | [[conditional-independence]] |
| 12.5 | Bayes' rule and its use | 417 | [[bayes-theorem]] |
| 12.6 | Naive Bayes models (incl. text classification) | 420 | [[naive-bayes]] |
| 12.7 | The wumpus world revisited (pit probabilities) | 422 | (not summarised) |

## Key takeaways
- Possible worlds = assignments to all random variables; the full joint answers any query but is O(2ⁿ).
- Normalization (α) avoids needing P(evidence).
- Bayes' rule converts causal knowledge P(effect|cause) into diagnosis, and causal knowledge is more robust.
- Conditional independence turns O(2ⁿ) into O(n) (naive Bayes) and underlies [[bayesian-networks]].

## Not read in detail
§12.1 (decision-theoretic framing) and §12.7 (wumpus pit calculation, uses a Known/Frontier/Other split) were skimmed only.

## Link to slides
Course syllabus item 7 ("Uncertainty: probability, Bayes' theorem, and naive Bayes") – [[slides-00-course-intro]]; no slide deck for this topic is in `raw/` yet.
