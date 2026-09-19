# Overstory

Overstory is a documentation methodology built on one representation: the **functionality tree** — a plain-markdown bullet tree stating what a piece of software lets a user do, see, and be affected by, with every node owned by exactly one location and sparse cross-links serving as lenses over the imposed hierarchy. A human writes the tree. Canonical docs describe the system as it is; planning docs are **computed overlays** on those trees, showing a proposed delta rather than restating the world. Leaves bind to code; a resolver detects bindings that have died, an edit classifier marks the nodes a change puts in doubt, and repairs land as proposals for the author to ratify.

The premise: most documentation rots because it has no single owned location per fact and no mechanism that notices drift. A functionality tree gives every claim one home, and the overlay discipline makes plans reviewable as diffs against that home.

## Reading order

- [analysis.md](analysis.md) — the core argument: the authorship inversion, its own strongest counterarguments, and the reduction of the hard problem to three tractable tasks (seed, resolver, edit classifier), with prior art named: Living Documentation, Specification by Example, traceability matrices, C4.
- [analysis-2.md](analysis-2.md) — later capture: statement kinds beyond functionality, session analyzers mining the author's own inputs, a markdown + meta.json source of truth, and per-reader comprehension tracking.
- [analysis-3.md](analysis-3.md) — foundation review: the ideas as a dependency chain, the uncertainties ranked by weight, and the consistency fixes applied.
- [evidence.md](evidence.md) — one line per research finding the analyses cite, and the open decisions they route to.
- [drift-sync-lifecycle.html](drift-sync-lifecycle.html) — flow charts of the sync lifecycle: how each class of drift is detected and repaired, where the loop is mechanical and where it rests on judgment, and a verdict on how precarious that leaves it.
- [0-process/](0-process/considerations.md) — how the programme works: probe, capture, ratchet, research.
- [3-canonical-docs/](3-canonical-docs/considerations.md) — the functionality-tree representation itself, its binding to code, and liveness.
- [4-planning-doc/](4-planning-doc/considerations.md) — deltas as highlighted overlays on canonical docs.
- [1-local-project-reorientation/](1-local-project-reorientation/considerations.md) — the author's consolidation plan for the sibling projects this depends on (cairn, ariadne, code-charter); context, not methodology.
- [todo.md](todo.md) — the single funnel for the thread's work items.

## Relation to quarry, and private material

The programme's external-research method — mining prior art into decision-routed references without repeats — is published separately as [quarry](https://github.com/CRJFisher/quarry). The research corpus that method produced is working material and is not part of this repository; [evidence.md](evidence.md) digests what the analyses cite from it. Other names marked _(private)_ in these documents — the functionality-docs probe programme, the canonical-docs design, sibling plans — are the author's working material in the same sense.

## Status

Overstory is a design programme: these documents are the artifact, and no implementation exists yet. The design is published so the methodology can be read, challenged, and built against.

## License

MIT — see [LICENSE](LICENSE).
