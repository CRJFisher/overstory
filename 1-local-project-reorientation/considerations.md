# Local project reorientation — considerations

- Goal: consolidate, focus, and align all work projects on this machine — one solid foundation before building forwards
- Scope: claude-config (skills/hooks/rules), code-charter (`~/workspace/code-charter`), ariadne, cairn, pkm, private data pipelines, whatsapp-bridge
- Finishing line: a family of Claude Code plugins — code-charter is a consumer of the family, not the vehicle
- [Cairn ships first — the early win, and the execution engine for every later plan](#cairn-ships-first)
- [Eval and golden tooling gets one home in claude-config; consumers pull from it, never fork](#eval-tooling-has-one-home)
- [claude-config's own surface stays consistent — thin new skills, opt-in contracts, an archived past](#claude-config-stays-consistent)
- [code-charter stabilizes and parks as a consumer](#code-charter-parks-as-a-consumer)
- [Ariadne proves the ported tooling in anger](#ariadne-proves-the-tooling-in-anger)
- [Machine operations: only the broken notification path is foundation work](#machine-operations)

## Cairn ships first

The first shipped product, and the sequencing anchor: consolidation waves start after its release.

- Finish docs 10–16 through release before the consolidation waves
- Delivery follows the ratified spec (cairn's spec-delivery, private): a skill distributed as a Claude Code plugin from a public repo
- worktree-hydration stays an active plan in its role as the pilot execution target
- The dispatch eval set mandated by doc 15 is an early consumer of the shared eval home (→ [eval tooling](#eval-tooling-has-one-home))

## Eval tooling has one home

Everything graded, harvested, or judged lives in claude-config — a deep port of the drift stack, merged with the sr- suite.

- drift's run-grade / trajectory-spine / calibrate contracts land in sr-store as the canonical vocabulary
- drift-calibrate and the grading queue port as sr- lenses; the harvest and stitch_eval harness patterns generalise here
- Grading surface: a run diff rendered to HTML, annotated in plannotator, verdicts ingested through the run-grades contract — no bespoke grading UI
  - the ChartDiff / difference-map research informs the rendering, not a new surface
- Test-in-anger consumers, in order: ariadne task 190.31, cairn's dispatch eval set, drift grading

## claude-config stays consistent

The home repo's own decisions: new skills start thin, contracts are opt-in, superseded plans leave the active set.

- The canonical-docs sync is built thin and standalone during the functionality-docs probes; the shared-substrate decision with code-charter's drift-sync waits until both engines are real
- `SKILL.meta.json` is an opt-in sr-suite contract — a skill adopts it when a lens needs it; no corpus rollout
- Archive sweep — to `_archive/`: skill-composition, cdoc, development-pathway, canonical-docs, transcript-lens-enhancements, meta-json-adoption, root `DEVELOPMENT_PATHWAY.md` + `.pipeline.html`
  - before development-pathway archives, Capture/Scope/Prioritize distil to bare functionality ideas — what a user experiences, no implementation detail — landing as a new overstory item (5-idea-pipeline)
  - staying active: functionality-docs, plannotator-extensions, overstory, cairn, worktree-hydration

## code-charter parks as a consumer

Kept healthy, not driven: its tooling migrates out and its visual surface waits.

- Near-term: fix the four red vscode `project_manager` tests, green CI, park with a status note
- The eval stack migrates out (→ [eval tooling](#eval-tooling-has-one-home)); code-charter consumes it back, never forks
- drift-sync keeps maintaining the diagram store as-is; whether it shares a substrate with the canonical-docs sync is decided later (→ [claude-config](#claude-config-stays-consistent))
- The visual front-end (graph store, webview, vscode extension) comes later or never
- Its ideas and its reconcile engine are inputs to overstory's binding-and-liveness question — the engine re-derives on rename rather than preserving an authored link, which bounds what it can supply; the vehicle stays parked (→ [3-canonical-docs](../3-canonical-docs/considerations.md#binding-and-liveness))

## Ariadne proves the tooling in anger

The first real consumer of the shared eval home.

- Task 190.31 (growable classifier eval-sets) exercises the grades and eval-set tooling first — closing the loop the drift stack never closed
- The main-merge of the working branch stays outside this phase

## Machine operations

Only the broken notification path is foundation work.

- whatsapp-bridge: rebuild from the current fix commit, redeploy under launchd, re-auth — pkm's scheduled digests and job scans depend on it
