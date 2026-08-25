# Overstory

Overstory is a documentation methodology built on one representation: the **functionality tree** — a plain-markdown bullet tree stating what a piece of software lets a user do, see, and be affected by, with every node owned by exactly one location and sparse cross-links serving as lenses over the imposed hierarchy. Canonical docs describe the system as it is; planning docs are **computed overlays** on those trees, showing a proposed delta rather than restating the world. Leaves bind symbol-level to code, and a resolver plus an edit classifier keep the binding live as the code moves.

The premise: most documentation rots because it has no single owned location per fact and no mechanism that notices drift. A functionality tree gives every claim one home, and the overlay discipline makes plans reviewable as diffs against that home.

## Reading order

- [analysis.md](analysis.md) — the core argument, its own strongest counterarguments, and the reduction of the hard problem to two tractable ML tasks (the edit classifier and the resolver), with prior art named: Living Documentation, Specification by Example, traceability matrices, C4.
- [analysis-2.md](analysis-2.md) — later capture: statement kinds beyond functionality, session analyzers mining the author's own inputs, a markdown + meta.json source of truth, and per-reader comprehension tracking.
- [0-process/](0-process/considerations.md) — how the programme works: probe, capture, ratchet, research.
- [1-local-project-reorientation/](1-local-project-reorientation/considerations.md) — consolidating existing projects onto one documentation foundation.
- [3-canonical-docs/](3-canonical-docs/considerations.md) — the functionality-tree representation itself.
- [4-planning-doc/](4-planning-doc/considerations.md) — deltas as highlighted overlays on canonical docs.
- [todo.md](todo.md) — the single funnel for the thread's work items.

## Relation to quarry

The programme's external-research method — mining prior art into decision-routed references without repeats — is published separately as [quarry](https://github.com/CRJFisher/quarry). The research corpus that method produced is working material and is not part of this repository.

## Status

Overstory is a design programme: these documents are the artifact, and no implementation exists yet. The design is published so the methodology can be read, challenged, and built against.

## License

MIT — see [LICENSE](LICENSE).
