# Planning doc — considerations

- Deliverable: a skill that produces planning docs showing how functionality changes with respect to what exists
- A planning doc is an overlay on the canonical docs:
  - reuses the canonical representation primitives (the functionality tree) — no second vocabulary
  - changed / new / removed functionality reads as a highlight at first glance — you see that and where something changes before any detail
  - left open — how much the highlight carries: pure marker vs an expandable diff-style was/now view; undecided, prototype to a decision
    - first prototype: CriticMarkup carries both — the bare highlight and the was/now substitution — in one plain-text syntax that composes with plain markdown (→ [evidence](../evidence.md#queued-areas-cited), G3.A5)
  - full context for free: existing functionality is the background, the delta reads in place against it
- How the overlay comes to exist — two candidates, the evidence leaning to the second
  - authored: the planner writes the overlay beside the canonical tree
  - computed: the plan _is_ an edit to the tree on a branch, and the overlay is the tree diff plus the classifier's verdict per changed node, rendered in plannotator — every change then begins as a tree edit — small, adjacent, riding an existing workflow step, the shape decay research says keeps a document current (→ [evidence](../evidence.md#verified-references), R-019, R-022; [analysis-3](../analysis-3.md#0-the-loops-required-shape)); whether the diff is reliable turns on stable node ids in the file (→ [analysis-3](../analysis-3.md#4-the-overlay))
- Zoom works on the overlay too: top-level view of the change first, drill into sub-functionality deltas as needed
- Implementation planning stays separate — sub-task files naming where each change lands and the decisions needed there; the overlay shows what changes, not how
- Build plan-docs plannotator-compatible from the start — review and iteration ride on its agent ↔ plan-doc loop, never a re-implemented one
  - already decided once: adopt plannotator, stop building plandoc (private decision record); gaps are extension work (plannotator-extensions, private), not a second surface
  - the markdown bullet tree lands on plannotator's strongest surface (version history, rendered diff, location anchors); HTML is its weakest — a further reason to stay primitive until richer forms earn their keep
- Plannotator's own trick — an interaction overlay that makes any arbitrary HTML file annotatable without owning its format — may generalise to how this overlay layers onto the canonical docs; mine it for patterns (→ the quarry corpus, private)
