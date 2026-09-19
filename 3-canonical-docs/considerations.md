# Canonical docs — considerations

- Why: a high-level view of the functionality the user decided to build, separate from code — code always carries implementation detail and is harder to reason about than the high-level flows
- The human writes the tree; tooling seeds it once on a brownfield repo, binds leaves to code, and checks it — the authorship inversion of [analysis](../analysis.md#what-the-framing-actually-changes)
  - classifiers and resolvers have ground truth; "write in my register" does not — the reason the inversion is right
  - the seed is a hypothesis under test, not a shipped feature: generated repo docs measurably fail where committed ones marginally help (→ [evidence](../evidence.md#verified-references), R-035)
- Deliverable: a skill that seeds, binds, and checks these docs — never one that writes them
- Core representation: a functionality tree in plain markdown — bullets only, no prose
  - each bullet is a pragmatic statement of desired functionality (e.g. "keep docs in sync with code")
  - a bullet may link to a sub-heading carrying its sub-functionality bullets (features/considerations one level down)
  - the reader takes as much context as they need: top-level view first, zoom into lower levels on demand
- The spine is statements of functionality and nothing else — it sidesteps the unsolved functionality-layer prompting problem instead of gating on it
  - open, Q1: whether the spine also admits assumptions and invariants, and whether decisions and principles attach typed to the nodes they qualify (→ [analysis-2](../analysis-2.md#1-multiple-statement-kinds--this-is-q1-with-a-synthesis-available))
  - open, Q2: what makes one level different from the next — containment of functionality chosen by the author, never call-graph or module structure; the research answer awaiting ratification is an audience contract with a membership test (→ [analysis-3](../analysis-3.md#1-the-representation))
- [Leaves bind to code, and the binding is kept honest in both directions](#binding-and-liveness)
- [The large-scale structure is an imposed tree with sparse cross-links](#tree-not-graph)
- Richer prose forms come only after the tree works — the functionality-docs probe programme (private) owned that question under the pre-inversion premise and is rescoped to its harnesses (→ [analysis](../analysis.md#of-overstory-in-light-of-it))
- Port the good ideas from the canonical-docs design (private), re-expressed in this distilled style:
  - one index per repo mapping each doc to the code paths it covers — so a code diff routes to its owning doc
  - anti-rot sweeps: dead paths traced, unindexed docs surfaced, stale claims flagged
  - route the diff to its doc and read the doc before deciding nothing needs updating
  - trivial subjects get no doc; a doc stays lighter than what it explains

## Binding and liveness

A leaf binds to code; tooling keeps the binding honest without ever touching the author's words. The working model below is stated for the catalog to test; only the mixed-authorship rule and the identity axis are settled.

- The mixed-authorship rule: the tool rewrites link targets, never node text — the only rule under which "guaranteed live" and "plain markdown, hand-authored" are both true
- Open, Q3: the binding primitive, decided on where identity survives rather than on granularity (→ [evidence](../evidence.md#banked-findings))
  - a `path#symbol` string dies on rename; an anchor written into source survives rename and move and is never rewritten; a path pattern never dangles and is precise about nothing; a test carries evidence the capability holds and is already kept alive by CI (→ [analysis-3](../analysis-3.md#2-binding))
  - decay research says the primitive must be the zero-maintenance one (→ [evidence](../evidence.md#completed-jobs), J-G6A6)
- Liveness is deterministic for death and a judgment for repair: a resolver reports a binding that no longer resolves; re-anchoring onto a renamed symbol is a proposal for the author, never a silent rewrite — no existing engine does it mechanically
- Both sync directions, one shape (Q5): a tree edit to load-bearing text marks the node as implying a code change; a code diff touching a bound symbol marks the node suspect. Suspect-marking is deterministic; the text that resolves it is proposed; the author ratifies
  - open: how far a high-level edit propagates downward through its children
- Single ownership partitions statements, not code — two nodes may bind one symbol, so a diff routes to a set of suspect nodes, never exactly one
- Keeping the tree true overlaps code-charter's drift-sync; its ideas and reconcile engine are inputs here and the shared-substrate decision waits (→ [1-local-project-reorientation](../1-local-project-reorientation/considerations.md#code-charter-parks-as-a-consumer))

## Tree, not graph

Functionality relationships are really a graph — a lens such as "how this lands as a product" or "which pattern implements this" links areas right across the hierarchy. The structure imposed on files, folders, and headings is nevertheless a tree, deliberately.

- Containment is the high-frequency relationship; "related" is low-frequency — a tree spine with sparse cross-links matches that distribution and contains the complexity
- The tree gives the reader one spine to zoom along, and gives every node exactly one owning location — diff-routing and anti-rot sweeps depend on single ownership
- A lens is a link-only index file gathering its nodes from across the spine — a view into the tree, never a second home for content
- Cross-links rot silently, so anti-rot sweeps also check link integrity: dead anchors, orphaned references
- Plain markdown handles this shape natively; what it cannot do — transclusion, multi-parent nodes — is excluded by design rather than worked around
