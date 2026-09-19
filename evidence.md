# Evidence — the research findings the analyses cite

The programme's research runs as a quarry corpus outside this repository (→ [README](README.md#relation-to-quarry-and-private-material)). The analyses cite its findings by id; this file expands every cited id to one line so the argument reads without the corpus. Ids: **Q** an open decision, **G** a search area (queued or done), **J** a completed job, **R** a verified reference. Every R line condenses a claim the corpus verified against a fetched primary source; the source is named in brackets.

## Open decisions

The question register — the routing table between research and these docs. It lives in the corpus; the ids are the vocabulary the analyses use.

- Q1 node vocabulary — capability statements only, or also invariants, motives, decisions (→ [3-canonical-docs](3-canonical-docs/considerations.md))
- Q2 level semantics — what defines a zoom level, given it is not call-graph or module structure (→ [3-canonical-docs](3-canonical-docs/considerations.md))
- Q3 leaf binding — how a functionality leaf binds to code (→ [binding and liveness](3-canonical-docs/considerations.md#binding-and-liveness))
- Q4 liveness — keeping doc-to-code links and claims true against a changing codebase (→ [binding and liveness](3-canonical-docs/considerations.md#binding-and-liveness))
- Q5 change classification — functionality change vs wording change; does this diff invalidate this node (→ [binding and liveness](3-canonical-docs/considerations.md#binding-and-liveness))
- Q6 delta overlay — rendering planned or changed functionality over the canonical tree (→ [4-planning-doc](4-planning-doc/considerations.md))
- Q7 functionality register — AI writing at the functionality layer without bloat or assumed context (→ [0-process](0-process/considerations.md))
- Q8 ratchet evals — golden cases, deterministic checks, calibrated judge rubrics (→ [0-process](0-process/considerations.md#capture-every-confirmed-win))
- Q9 simplification — mechanistic transforms from complex to simple representations
- Q10 research intake — external sources to routable references, without repeats (→ [quarry](https://github.com/CRJFisher/quarry))
- Q11 landing — market and discourse shaping how this ships (→ [1-local-project-reorientation](1-local-project-reorientation/considerations.md))
- candidates, deferred: Q12 session capture and Q13 reader state (→ [analysis-2](analysis-2.md#what-changes-where--pending-ratification))

## Banked findings

Framing shifts the corpus has already established; every area they touch carries them.

- **Binding identity beats binding granularity as the Q3 axis.** A computed symbol string dies on rename; an anchor comment in source survives rename and move, dies only on deletion, and never needs rewriting — dissolving the mixed-authorship rule rather than satisfying it; a path pattern is precise about nothing and never dangles
- **Q1 and Q5 may be one decision.** Doorstop classifies wording-vs-functionality by _where_ an edit landed (a declared partition of load-bearing fields); the Gene Ontology by _whether downstream usages become incorrect_ — overstory's own criterion, since a leaf's downstream usages are its bindings. Deciding the node vocabulary is deciding what is load-bearing

## Completed jobs

- **J-G1A2** (2026-08-24) goal refinement and per-level membership — yields R-001 to R-011: a formal stop rule that forces exactly two statement kinds, and per-level membership tests stated in user-visible terms
- **J-G1A5** (2026-08-24) editorial content models — yields R-012 to R-017: GitHub Docs' per-level membership rules and fan-out budgets, their tuning history, and one node measured against its feature's releases
- **J-G5A6** (2026-08-25) authored multi-tier sets — yields R-026 to R-034: four release-notes tier pairs; the curated tier is never a subset of the complete one; zoom is select-then-re-register
- **J-G6A3** (2026-08-25) the agent-facing repo-doc corpus — yields R-035 to R-045: generated context files raise cost without helping; observed practice is flat and mechanics-register; capability-first forms are two levels
- **J-G6A6** (2026-08-25) does the human keep authoring — yields R-018 to R-025; verdict: decay absent a forcing function is confirmed from four independent lanes, so the forcing function is the product (Q11), the overlay leans computed (Q6), and the leaf primitive must be the zero-maintenance one (Q3)

## Queued areas cited

- G1.A2 — done, see J-G1A2
- G2.A1 Gherkin as a typed capability grammar whose node text is the binding key — what node kinds a mass-deployed capability tree needed, and the verdict vocabulary a text-keyed binding produces when it dies
- G2.A2 Binding records and where durable identity lives — what a binding stores, where its identity lives, and what the tool does when it cannot re-locate it
- G3.A1 Suspect links — can "did this edit invalidate the child" be answered by a declared field partition plus a fingerprint, leaving only a residue for a model (Doorstop, OpenFastTrace)
- G3.A2 Doc/code inconsistency corpora — detecting invalidation from a diff and generating the fix
- G3.A4 Structural tree diff — must stable node ids live in a hand-authored file for a move-aware diff, and do they survive hand editing
- G3.A5 Overlay form — inline markup (CriticMarkup carries both marker and was/now) vs anchored sidecar (Hypothesis anchoring fails on short generic quotes) vs typed fragments with lifecycle
- G3.A6 Ontology curation — identity, meaning change, and obsoletion policy (the Gene Ontology's immutable ids)
- G4.A1 Controlled grammars and the rules/judgment split — EARS-shaped invariant patterns as a large labelled fraction of real requirements
- G4.A4 Calibration fixtures — document pairs with known verdicts; cloze and comprehension instruments; the expertise-reversal effect
- G5.A2 Degree-of-interest as a document-scoping function — Mylyn's DOI as an interaction-derived relevance signal
- G6.A5 The docs-for-agents market and the AI-generated-doc counter-test

## Verified references

Each line condenses a corpus claim verified against a fetched primary source.

- **R-002** Level membership by single-agent realizability — refinement stops when a goal is realizable by one agent; a software-side agent makes it a requirement, an environment-side agent an assumption [KAOS: van Lamsweerde, Letier]
- **R-003** The minimum vocabulary a stop rule forces is two classes — prescriptive (goal, specialising to requirement or expectation) and descriptive (domain property); motive is the upward link itself, decisions are attributes on OR-links; no rationale node kind exists [KAOS glossary, patterns, metrics]
- **R-007** Cockburn's per-level tests are user-visible — sea level: "can the primary actor go away happy?", one person, one sitting; summary spans several user goals; subfunction only as forced; clam: "don't write this, merge it back" [Writing Effective Use Cases]
- **R-008** The level-repair moves — drafts land too low; ask WHY to rise; keep 3–10 steps; merge trivial sub-cases [Cockburn; KAOS]
- **R-012** GitHub Docs' one-page rule sheet — a membership rule and fan-out budget per level (category: split past ten; map topic: two to eight), a depth cap, and a fixed sibling order [github/docs content model]
- **R-016** One node against its feature's releases — the doc led the changelog by a day, retracted a claim a day after ship, and every claim sits inside version-flag guards [github/docs history]
- **R-018** Decay is the steady state — architecture docs "rarely updated" in 2002 and 2013 alike; 68% agree documentation is always outdated [Lethbridge 2002; Rost 2013; Aghajani 2020]
- **R-019** The survival rule — only docs whose update is small, adjacent to the work, and attached to an existing workflow step stay current; big, abstract, far-from-code documents rationally starve [Lethbridge, Singer, Forward 2003]
- **R-020** The measured decay curve — 82% of ~2,700 projects carried a stale code reference at some point; currently stale ones average 4.7 years; of fixes, 39% updated the doc, 48% were the code changing, 13% deletion [Tan, Wagner, Treude]
- **R-021** Hand-maintained models of one's own system are a near-empty category — 35/50 practitioners abandoned UML after trying it, 0/50 sustained it; models "seldom updated after initially created" [Petre 2013; Gorschek 2014; Forward & Lethbridge]
- **R-022** The survivor mechanism — every surviving model population is one whose model mechanically produces something on the critical path (code generation, sync by construction); "put MDE on the critical path" [Petre; Hutchinson, Whittle, Rouncefield 2014]
- **R-023** Showing divergence changes nothing — under half of flagged architecture violations removed after months; the dominant reconciliation is editing the model to legalise the code; only a mandated conformance process reversed the trend [reflexion-model field studies; Buckley 2015]
- **R-025** Decision records die of non-surfacing — ADRs "sat in docs/adr/, nobody read them before opening a PR"; the fix that worked posts the decision into any pull request touching its declared files [practitioner accounts; decision-guardian]
- **R-028** Kubernetes rules its complete tier with a checkable anatomy — change type, action-required, affected field, doc link — and its curated tier by nomination [Kubernetes release process]
- **R-029** Multi-LexSum's procedure — write the long tier first from sources, then condense with source access retained, under a fact checklist [Multi-LexSum]
- **R-034** The generative zoom rule across all specimens — select items by discretion, then re-register the survivors for a new audience; a curated tier is never a subset of the tier below; never "compress the text" [synthesis over R-026 to R-032]
- **R-035** The only success-and-cost A/B — generated context files leave success unchanged and raise cost by 20–23%; developer-committed files are the one significant winner [Gloaguen et al., "Evaluating AGENTS.md"]
- **R-036** Why generated files fail — redundancy: repo overviews speed nothing, instructions are followed and that compliance is the cost; length has no measurable effect [same]
- **R-037** The context-file corpus register is mechanics — testing 76%, implementation 71%; capability prose is preamble [Agent READMEs, 2,303 files]
- **R-038** Observed practice is flat — one H1, five to seven H2s, deeper nesting essentially unobserved; the only multi-level structure is index files pointing at other files [mined corpora]
- **R-043** Developer files are correctness-null — the one reproducible benefit is operational truth an agent cannot infer, such as a test suite that takes twenty minutes [replication A/B]
- **R-044** The counter-specimen — latent-scope's AGENTS.md is headed entirely by user goals, build mechanics demoted to the last section [latent-scope]
- **R-045** The capability-first forms observed in the wild — shallow-and-wide, or exactly two levels: a navigation index linking feature docs headed by user flows with file-path leaves [contentful/apps; chartbrew]
