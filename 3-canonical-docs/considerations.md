# Canonical docs — considerations

- Why: a high-level view of the functionality the user decided to build, separate from code — code always carries implementation detail and is harder to reason about than the high-level flows
- Deliverable: a skill that creates and maintains these docs
- Core representation: a functionality tree in plain markdown — bullets only, no prose
  - each bullet is a pragmatic statement of desired functionality (e.g. "keep docs in sync with code")
  - a bullet may link to a sub-heading carrying its sub-functionality bullets (features/considerations one level down)
  - the reader takes as much context as they need: top-level view first, zoom into lower levels on demand
- The tree is the deliberate primitive: statements of functionality and nothing else — it sidesteps the unsolved functionality-layer prompting problem instead of gating on it
- [The large-scale structure is an imposed tree with sparse cross-links](#tree-not-graph)
- Richer prose forms come only after the tree works — probe program in [functionality-docs](../../functionality-docs/README.md)
- Port the good ideas from [canonical-docs](../../canonical-docs/design.md), re-expressed in this distilled style:
  - one index per repo mapping each doc to the code paths it covers — so a code diff routes to its owning doc
  - anti-rot sweeps: dead paths traced, unindexed docs surfaced, stale claims flagged
  - route the diff to its doc and read the doc before deciding nothing needs updating
  - trivial subjects get no doc; a doc stays lighter than what it explains
- Keeping the tree true against code overlaps code-charter's drift-sync → relationship decision in [1-local-project-reorientation](../1-local-project-reorientation/considerations.md)

## Tree, not graph

Functionality relationships are really a graph — a lens such as "how this lands as a product" or "which pattern implements this" links areas right across the hierarchy. The structure imposed on files, folders, and headings is nevertheless a tree, deliberately.

- Containment is the high-frequency relationship; "related" is low-frequency — a tree spine with sparse cross-links matches that distribution and contains the complexity
- The tree gives the reader one spine to zoom along, and gives every node exactly one owning location — diff-routing and anti-rot sweeps depend on single ownership
- A lens is a link-only index file gathering its nodes from across the spine — a view into the tree, never a second home for content
- Cross-links rot silently, so anti-rot sweeps also check link integrity: dead anchors, orphaned references
- Plain markdown handles this shape natively; what it cannot do — transclusion, multi-parent nodes — is excluded by design rather than worked around
