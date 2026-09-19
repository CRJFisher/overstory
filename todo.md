# Todo

The single funnel for this thread's work items. Each item is one line linking to the section that owns its detail — this file carries no content of its own.

## Now — writing, runs beside cairn

- [ ] Catalog by hand: one brownfield repo ariadne parses, its functionality tree at two levels, one subject bound three ways — `path#symbol`, in-source anchor, test (→ [simple way forward](analysis.md#simple-way-forward), [binding and liveness](3-canonical-docs/considerations.md#binding-and-liveness))
- [ ] Replay the catalog repo's last thirty commits through the detection rules by hand — dead bindings, suspects at each closure depth, coverage gaps per commit — the false-suspect rate and the ratification load, before anything is built (→ [lifecycle charts](drift-sync-lifecycle.html), [uncertainties](analysis-3.md#the-uncertainties-ranked))
- [ ] Live the loop on that repo: every plan a tree edit on a branch, every code change routed to its nodes; count what drifted unnoticed (→ [uncertainties](analysis-3.md#the-uncertainties-ranked))
- [ ] Apply Cockburn's per-level tests to the catalog; record whether anything demands a third level (→ [uncertainties](analysis-3.md#the-uncertainties-ranked))
- [ ] Ratify or reject the pending syntheses (→ [analysis-2](analysis-2.md#what-changes-where--pending-ratification), [analysis-3](analysis-3.md#what-changed-in-this-pass))

## Build — after cairn's release

- [ ] Liveness checker v0, deterministic: resolve every binding, report the dead; mark nodes suspect from a code diff through their bindings (→ [binding and liveness](3-canonical-docs/considerations.md#binding-and-liveness))
- [ ] Edit classifier v0: fingerprint over load-bearing text, judgment only for the residue; golden cases from real edits (→ [change classification](analysis-3.md#3-change-classification))
- [ ] Render the overlay in plannotator over the markdown; CriticMarkup for the highlight prototype (→ [4-planning-doc](4-planning-doc/considerations.md))
- [ ] Only then: an AI brownfield seed on a second repo, as a hypothesis under test (→ [simple way forward](analysis.md#simple-way-forward))

## Author's sequencing — private projects this depends on

- [ ] Cairn docs 10–16 through release — the sequencing anchor; consolidation waves start after (→ [cairn ships first](1-local-project-reorientation/considerations.md#cairn-ships-first))
- [ ] whatsapp-bridge: rebuild from the fix commit, redeploy under launchd, re-auth (→ [machine operations](1-local-project-reorientation/considerations.md#machine-operations))
- [ ] Rescope the functionality-docs probe programme to harnesses + checker evals + seed test before running any round (→ [analysis](analysis.md#of-overstory-in-light-of-it))
- [ ] Build the canonical-docs sync skill thin and standalone (→ [claude-config stays consistent](1-local-project-reorientation/considerations.md#claude-config-stays-consistent))

## Consolidation waves — after cairn's release

- [ ] Distil development-pathway's Capture/Scope/Prioritize into a bare-functionality idea-pipeline item here (→ [claude-config stays consistent](1-local-project-reorientation/considerations.md#claude-config-stays-consistent))
- [ ] Archive sweep to `_archive/`: skill-composition, cdoc, development-pathway, canonical-docs, transcript-lens-enhancements, meta-json-adoption, root `DEVELOPMENT_PATHWAY.md` + `.pipeline.html` (→ [claude-config stays consistent](1-local-project-reorientation/considerations.md#claude-config-stays-consistent))
- [ ] Port the drift eval stack into claude-config's sr- suite as the one eval home (→ [eval tooling has one home](1-local-project-reorientation/considerations.md#eval-tooling-has-one-home))
- [ ] Test the eval home in anger, in order: ariadne 190.31 → cairn dispatch eval set → drift grading (→ [ariadne proves the tooling](1-local-project-reorientation/considerations.md#ariadne-proves-the-tooling-in-anger))
- [ ] code-charter: fix the four red `project_manager` tests, green CI, park with a status note (→ [code-charter parks as a consumer](1-local-project-reorientation/considerations.md#code-charter-parks-as-a-consumer))

## Skill deliverables — advanced by probe verdicts

- [ ] Canonical-docs skill: seed, bind, and check the functionality tree, porting the index and anti-rot ideas (→ [3-canonical-docs](3-canonical-docs/considerations.md))
- [ ] Planning-doc skill: overlay on canonical docs, plannotator-compatible from the start (→ [4-planning-doc](4-planning-doc/considerations.md))
- [ ] Prototype the highlight question to a decision: pure marker vs expandable was/now (→ [4-planning-doc](4-planning-doc/considerations.md))
- [ ] Deterministic process-adherence check: a hook triggers a sub-agent review (→ [0-process](0-process/considerations.md#deterministic-enforcement-of-working-rules))

## Continual — research intake

- [x] Define the reference format: id, claim, source link, how-to-apply note (→ [quarry's data model](https://github.com/CRJFisher/quarry/blob/main/docs/data-model.md))
- [ ] Run the deepresearch jobs in programme order — G1.A2, G1.A5, G5.A6, G6.A3, G6.A6 done; G2 next, as the gate on binding identity (→ the corpus run order, private; [evidence](evidence.md#completed-jobs))
- [ ] Review "How I use LLMs to learn" — LLM-assisted learning workflow (→ the corpus review queue, private)
- [ ] Review mattpocock/skills — skill design, routing, small-composable-over-framework stance (→ the corpus review queue, private)
- [ ] Review mattpocock/sandcastle — relevance to cairn's agent-step and supervision questions (→ the corpus review queue, private)
