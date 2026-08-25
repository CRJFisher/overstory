# Planning doc — considerations

- Deliverable: a skill that produces planning docs showing how functionality changes with respect to what exists
- A planning doc is an overlay on the canonical docs:
  - reuses the canonical representation primitives (the functionality tree) — no second vocabulary
  - changed / new / removed functionality reads as a highlight at first glance — you see that and where something changes before any detail
  - left open — how much the highlight carries: pure marker vs an expandable diff-style was/now view; undecided, prototype to a decision
  - full context for free: existing functionality is the background, the delta reads in place against it
- Zoom works on the overlay too: top-level view of the change first, drill into sub-functionality deltas as needed
- Implementation planning stays separate — sub-task files naming where each change lands and the decisions needed there; the overlay shows what changes, not how
- Build plan-docs plannotator-compatible from the start — review and iteration ride on its agent ↔ plan-doc loop, never a re-implemented one
  - already decided once: [adopt plannotator, stop building plandoc](../../_archive/cdoc-interactive/decision-adopt-plannotator.md); gaps are [extension work](../../plannotator-extensions/raw-ideas.md), not a second surface
  - the markdown bullet tree lands on plannotator's strongest surface (version history, rendered diff, location anchors); HTML is its weakest — a further reason to stay primitive until richer forms earn their keep
- Plannotator's own trick — an interaction overlay that makes any arbitrary HTML file annotatable without owning its format — may generalise to how this overlay layers onto the canonical docs; mine it for patterns (→ [2-research](../2-research-into-knowledge-representations/considerations.md))
