# AI Course Wiki — Schema

This repo is a personal study wiki for the USFQ Artificial Intelligence course, following Karpathy's "LLM Wiki" pattern: the LLM incrementally builds and maintains a persistent, interlinked markdown wiki between the student and the raw sources. Knowledge is compiled once and kept current, not re-derived per query.

## Layers
1. `raw/` — immutable sources (slides `.pptx`, `papers/`, `books/`, `code/`, `assets/`). NEVER modify or delete. Read only.
2. `wiki/` — LLM-owned markdown. The student reads; the LLM writes.
3. `CLAUDE.md` — this schema. Co-evolve it with the student.

## Wiki layout
- `wiki/index.md` — catalog of every page: `- [[page]] — one-line summary`, grouped by category. Update on EVERY change.
- `wiki/log.md` — append-only chronological log. Entry header format: `## [YYYY-MM-DD] ingest|query|lint|setup | Title` followed by a few bullets (pages created/updated).
- `wiki/overview.md` — evolving synthesis of the whole course and how topics connect.
- `wiki/sources/` — one summary page per raw source (slide deck, paper, book chapter, code file). Filename: kebab-case.
- `wiki/concepts/` — one page per concept/algorithm (e.g. `a-star-search`, `genetic-algorithms`, `simulated-annealing`).
- `wiki/entities/` — people, books, papers, tools (e.g. `john-holland`, `russell-norvig`).
- `wiki/analyses/` — filed-back answers: comparisons, study guides, exam-prep, practice questions.

## Page conventions
- Obsidian-style links: `[[page-name]]` (filename without `.md`). Link generously; every page must have at least one inbound link (index counts only as a last resort).
- YAML frontmatter on every page:
  ```
  ---
  title: ...
  type: source | concept | entity | analysis | overview
  tags: [search, optimization, ...]
  sources: [raw/slides/04_Optimization.pptx, ...]
  updated: YYYY-MM-DD
  ---
  ```
- Concept pages should include: intuition, formal definition/pseudocode, complexity/properties, pros/cons, when to use, related concepts, and "Exam angles" (typical questions, common pitfalls).
- Cite raw sources inline, e.g. (source: `raw/slides/04_Optimization.pptx`, slide 12; or book ch./page). Never invent citations or page numbers; if unsure, cite the file only.
- When new information contradicts an existing claim, do not silently overwrite: add a `> ⚠️ Contradiction:` note citing both sources, and say which is likely right.
- Mark unverified/LLM-background claims with `(unverified)` so the student knows what is grounded in sources.

## Workflows
### Ingest (one source at a time, student stays involved)
1. Read the source (for large PDFs, read by page ranges; for `.pptx`, extract text, e.g. `python -m markitdown` or python-pptx if available).
2. Briefly discuss key takeaways with the student.
3. Write `wiki/sources/<name>.md` summary.
4. Create/update relevant concept and entity pages (typically 5–15 pages touched).
5. Update `wiki/overview.md` if the big picture shifted.
6. Update `wiki/index.md`; append to `wiki/log.md`.

### Query
1. Read `wiki/index.md` first, then drill into relevant pages.
2. Answer with citations to wiki pages (and raw sources where needed).
3. If the answer is valuable (comparison, study guide, derivation), offer to file it in `wiki/analyses/`, then update index + log.

### Lint (on request)
Check for: contradictions, stale claims, orphan pages, concepts mentioned without a page, missing cross-links, missing frontmatter, gaps worth filling (suggest sources/questions). Report findings, fix the safe ones, log the pass.

## Course scope (initial)
Topics seen in raw/: Introduction to AI, Problem Solving (search), Intelligent Agents, Optimization (gradient descent, simulated annealing, genetic algorithms, PSO, ant colony), Logic Programming with Prolog. Textbooks: Russell & Norvig (AIMA), Eiben & Smith (Evolutionary Computing), plus a 6th-edition AI text.

## Rules
- Never edit `raw/`. Never delete wiki pages without asking.
- Prefer updating existing pages over creating duplicates.
- Keep pages focused and skimmable; the student is studying for exams.
