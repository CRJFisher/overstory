# Analysis 3 — foundation review

Discussion capture (2026-09-07): every document in the repository read against the research corpus and the sibling projects they cite, to find where the foundation contradicts itself, which uncertainties carry the most weight, and what a self-consistent version of the programme says. Companion reading: [analysis](analysis.md), [analysis-2](analysis-2.md), [evidence](evidence.md) — the one-line digest of every research finding cited below.

## What the review found

- The decay research does not undermine the premise; it describes the regime the premise is built to leave. Every population it measured was hand-maintained, updated by hand, far from the code, with nothing proposing the repair — so its findings are constraints on the loop's shape, not refutations: the update must be small, adjacent, and surfaced at the edit (R-019, R-025); noticing alone is not enough, the repair must be at hand (R-023); and something downstream must use the tree so ratifying stays worth doing (R-022). Overstory's loop is designed to that shape. What stays open is the one step no mechanism removes — the author's verdict — and whether a capability's truth can be bounded from a diff tightly enough to keep that step cheap (→ [lifecycle charts](drift-sync-lifecycle.html))
- The README and the considerations files described two different projects: the README a human-authored tree with machine binding and classification; the considerations files, untouched since 2026-08-13, the pre-inversion programme in which AI writes and the human reviews — the evolution [analysis](analysis.md#proposed-evolution-of-overstory-losing-nothing) prescribed was never folded in
- No specimen of the primary artifact exists: the form (bullets with linked sub-headings) is exercised by every considerations file; the vocabulary (capability statements bound to code) by none — every claim about the representation is untested
- Two capability claims were overstated: no resolver keeps a `path#symbol` link live across a rename — ariadne resolves a snapshot with no cross-commit identity, and code-charter's reconcile engine retires the old id and derives a fresh one — so liveness is deterministic for detecting death and a judgment for repair
- The public artifact cited evidence and documents a reader cannot open: roughly twenty-five finding ids and fifteen relative links resolved only inside the author's private workspace
- [The ideas as a dependency chain](#the-ideas-as-a-dependency-chain) — what rests on what, and where the evidence stops
- [The uncertainties, ranked](#the-uncertainties-ranked) — by how much rests on each, against how little is known
- [What changed in this pass](#what-changed-in-this-pass) — the fixes applied, and the syntheses left for ratification

## The ideas as a dependency chain

Each layer assumes the one above it. What the corpus has settled is named; the rest is design.

### 0. The loop's required shape

- What the decay research measured, and why it sits before this design rather than against it: decay is the steady state for hand-updated docs (R-018, R-020); humans do not sustain hand-maintained models of their own systems (R-021); showing divergence without a repair at hand gets the model edited to match the code (R-023); the survivors are docs whose update is small, adjacent, and rides an existing workflow step (R-019), records that surface at the code edit (R-025), and models that mechanically produce something the project runs on (R-022). In every case the update was human labour and nothing proposed it
- The constraints that yields for a mechanised loop, and how the design meets each
  - small and adjacent: detection is deterministic and the proposal is drafted at the edit — the Stop hook and the PR are where it surfaces
  - a repair at hand, not a warning: every suspect arrives with its proposal; mechanical repairs apply themselves under the mixed-authorship rule
  - consumed downstream: the overlay renders from the tree and agents plan from it, so ratifying is on the path to the next change rather than a chore beside it
- The residue the mechanism cannot remove: the author's verdict, and the semantic gap it exists to close — a capability's truth is not decidable from a diff, so the loop bounds where to look and leaves whether to judgment. The charts in [drift-sync-lifecycle.html](drift-sync-lifecycle.html) map which drift classes are mechanical and which rest on that judgment
- Note on the agent-context consumer: committed context files help marginally where generated ones cost more and help nothing (R-035, R-036, R-043) — support for human authorship, and a reason not to lean on agent context as the main consumer

### 1. The representation

- The spine — capability statements, one owning location per node, tree not graph — is better supported by the corpus than the docs yet say
  - a level is an audience contract with a membership test, never a size ratio (R-034): Cockburn's user-goal test — "can the primary actor go away happy?" (R-007) — and KAOS's single-agent realizability (R-002) are the two published tests that fall back on neither call-graph nor taste. Q2 has an answer the docs have not absorbed
  - a parent re-registers for the zoomed-out reader; it does not compress its children — no curated tier in shipped practice is a subset of the tier below it (R-034), and zoom-as-truncation is the anti-pattern a judge must catch
  - the minimum vocabulary a completeness check forces is two kinds, capability and assumption; motives are the upward link and decisions are link attributes (R-003) — analysis-2's spine-plus-attachments synthesis matches the one formal tradition that tried it
  - the repair moves are published: ask WHY to rise a level, keep fan-out within budget, merge trivia (R-008, R-012)
- The risk the corpus adds: every capability-first doc observed in the wild is shallow-and-wide or exactly two levels (R-045); nothing measured carries the multi-level zoom the docs imagine (R-038). Everything in this repository is two levels too. Depth must earn its keep
- Single ownership partitions statements, not code: two nodes may bind one symbol (a permissions filter serves "search" and "permissions" alike), so a diff routes to a set of suspect nodes, never exactly one

### 2. Binding

- Banked already: the axis is where identity lives, not granularity. A computed symbol string dies on rename; an anchor written into source survives rename and move and is never rewritten — dissolving the mixed-authorship rule rather than satisfying it; a path pattern never dangles and is precise about nothing
- Verified this pass: ariadne's symbol identity is per snapshot with no continuity across commits, and code-charter's reconcile engine absorbs a rename by retiring the old flow id and hydrating a fresh one — neither preserves a human-authored link. "The resolver keeps links live" is true for detecting death and false for repair
- The candidate [analysis](analysis.md#critique) lists and never develops: a test as the binding. The node names the test that demonstrates it; liveness is the test existing and passing; renames of production symbols are invisible; CI is the checker and already sits on the critical path. This is Specification by Example's actual mechanism (G2.A1's text-keyed binding is the same family) and the only zero-maintenance primitive that also carries evidence the capability _holds_ rather than where its mechanism _lives_. Its own death condition: functionality with no test is unbound
- Three live options, then; the catalog should bind one subject all three ways before choosing

### 3. Change classification

- Banked: Q1 and Q5 may be one decision — a declared partition of load-bearing fields plus a content fingerprint answers "did this edit invalidate the node" with no model in the loop (Doorstop, G3.A1), leaving only the reworded-but-unchanged residue for judgment
- Both sync directions then share one shape: suspect-marking is deterministic (the fingerprint changed; a code diff touched a bound symbol), the text that resolves it is a proposal, the author ratifies. The "edit classifier" of the way forward shrinks to fingerprint plus residue, and the reverse direction — the one with no human who already knows the answer — gets its deterministic v0 for free from the bindings
- Named and undecided: how far a high-level edit propagates downward — Doorstop breaks the cascade deliberately

### 4. The overlay

- Leans computed (J-G6A6's verdict) and, per layer 0, is the shape under which every change begins as a tree edit — the strongest downstream consumer the design has
- Two dependencies: a move-aware diff needs stable node ids in the file (G3.A4 — its one genuinely undecided question, on which three features now hang: the overlay, the meta sidecar, reader state); the highlight form has a cheap first answer in one syntax — CriticMarkup carries both the bare marker and the was/now substitution (G3.A5)

### 5. Extensions — not foundation

- Statement kinds: synthesis available and consistent with R-003; ratify on the catalog
- Session capture: speculative; reintroduces machine-written text at volume and threatens the ratification economy the inversion depends on; quarantined until the reverse direction alone has been lived with
- Reader state: deferred; a third id-keyed store

## The uncertainties, ranked

By how much of the programme rests on each, against how little is known. Each names what would settle it.

1. **The semantic gap: can suspect-marking be tight enough?** A capability's truth is not decidable from a diff, so the loop marks every edit to bound code — and to code within call-graph depth k of it — as suspect and leaves the verdict to judgment. Depth k trades false suspects against silent misses, and it sets both failure modes at once. Settle by replaying the catalog repo's last thirty commits through the rules by hand at each depth: suspects per commit, and drifts missed. Nothing to build
2. **Whether the author's verdict keeps pace.** The mechanism removes noticing and drafting; deciding stays human, and the tree is exactly as true as its last ratification. The bet is that node-level verdicts surfaced at the edit are cheap enough where document review was not — and that the overlay and agent context consume the tree enough to make ratifying part of the next change. Session capture would multiply the volume. Settle from the same replay: proposals per week under the reverse direction alone
3. **Where binding identity lives.** Symbol string, in-source anchor, or test. Settle by binding the same catalog subject all three ways and running it over ten real commits: deaths, and the effort to repair each
4. **Whether the tree needs more than two levels.** Observed practice is two levels; the design assumes arbitrary zoom. Settle on the catalog with Cockburn's per-level tests — if nothing demands a third level, the design simplifies to index → feature-doc
5. **The node vocabulary.** Capability-only spine, or capability plus assumption (R-003). Collapses into deciding what is load-bearing (Q1≡Q5). Settle on the catalog by declaring the field partition and seeing what a completeness check needs
6. **Machine-written ids in a hand-authored file.** Gates the overlay's reliability and two later features. Settle by trying block-property ids on the catalog and hand-editing it for a month
7. **The highlight form.** Low stakes; CriticMarkup likely answers it in one syntax
8. **Session capture** — whether the volume overwhelms curation. Deferred behind 2
9. **Reader state** — admissible evidence, at what cost to the reader. Deferred

## What changed in this pass

Applied now — consequences of decisions the README already ratified at publication, and corrections of fact:

- [README](README.md): premise kept as written; the resolver sentence made precise; each file described as it is; the convention for private material stated
- [3-canonical-docs](3-canonical-docs/considerations.md): rewritten around the inversion as [analysis](analysis.md#proposed-evolution-of-overstory-losing-nothing) prescribed — human-authored spine, Q1–Q3 named as open, the mixed-authorship rule, both sync directions under one shape, deliverable seed + bind + check
- [0-process](0-process/considerations.md): the central problem relocated; the practice docs noted as exercising form, not vocabulary; the probe programme noted as rescoped
- [4-planning-doc](4-planning-doc/considerations.md): the computed candidate added beside the authored one, with the decay research's survival conditions as its motive; CriticMarkup named for the highlight prototype
- [1-local-project-reorientation](1-local-project-reorientation/considerations.md): the one line analysis prescribed — code-charter's ideas and reconcile engine are inputs; the vehicle stays parked
- [todo](todo.md): the way forward is the "Now" list, split into writing that runs beside cairn and build that waits for it; the author's private sequencing items sit under their own heading
- [evidence](evidence.md): every cited finding id expanded to one line, so the analyses read without the corpus
- [drift-sync-lifecycle.html](drift-sync-lifecycle.html): the sync lifecycle as flow charts — the loop, both directions, a node's states, ratification, the binding primitive's effect, a map of every drift class by who decides, and the verdict on precariousness
- Every link into the author's private workspace replaced by its plain name marked (private)

Pending ratification — syntheses from this pass. Where one appears in a considerations file it is marked as the working model, not a decision:

- level semantics: a level is an audience contract with a membership test, and a parent re-registers rather than compresses (→ 3-canonical-docs, Q2)
- design for two levels first; a third earns its place on the catalog (→ 3-canonical-docs, Q2)
- test-as-binding as a live option for Q3; its adoption waits on the three-way catalog trial
- the deterministic-suspect / proposed-text / human-ratifies shape for both directions; confirmed only when the v0 checker produces it
- [analysis-2](analysis-2.md#what-changes-where--pending-ratification)'s changes stand as listed there, still pending

## Open questions

- Does surfacing proposals at the edit keep the verdict cheap when the author is in a hurry — or does the queue need a gate that blocks the merge?
- If a test is the binding, is "unbound" the right verdict for functionality with no test, or the signal to write one?
- Does a catalog written by the one person who already knows the answers test anything — or does the first honest test need a second repo and a second reader?
