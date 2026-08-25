# Analysis — the user-authored functionality-tree framing

Discussion capture (2026-08-19): comparing the "user writes the tree, AI seeds/binds/checks it" framing against the existing overstory plan, and a proposed way forward. Companion reading: [README](README.md), [3-canonical-docs](3-canonical-docs/considerations.md), [4-planning-doc](4-planning-doc/considerations.md), [functionality-docs probe programme](../functionality-docs/README.md).

## What the framing actually changes

The big move is not "add code-charter back in" — it is an **inversion of authorship**:

- Overstory today: *AI writes the functionality docs, the human reviews* — the central unsolved problem is prompting AI into the functionality register ([0-process](0-process/considerations.md), the whole functionality-docs probe programme).
- The new framing: *the human writes the tree*; AI seeds it once (brownfield), binds leaves to live code, and judges whether edits imply real change.

That relocates the hard prompting problem rather than solving it — but it shrinks to three much more tractable AI tasks:

- a one-off **seed** (reviewable, brownfield only)
- a **classifier** — does this tree edit imply a functionality change? does this code diff invalidate this node?
- a **resolver** — keep leaf→code links live, which ariadne already does mechanically

Classifiers and resolvers have ground truth; "write in my register" doesn't. That is the main reason the framing is right.

## Comparison with what overstory already has

| The framing | Already in overstory | What's genuinely new |
|---|---|---|
| Zoomed-out functionality view | 3-canonical-docs: bullet tree, linked sub-headings, tree-not-graph; the considerations files practise it | Nothing new in *form* — but the form has not yet been applied to **code**, only to plans |
| Zoomed-in view, live links to code | canonical-docs index: doc → code **path globs**, anti-rot sweeps | Symbol-level binding via ariadne; "guaranteed live" needs a resolver that rewrites links |
| Catalog of example representations | "capture every win" as golden/anti cases; "apply the principles" | Specimens as the **primary** capture form, authored directly, not harvested from AI output feedback |
| Hybrid planning/canonical doc, diff highlight on semantic edits | 4-planning-doc overlay, highlight, pure-marker vs was/now open | The overlay becomes *computed* (tree diff in git + classifier verdict) rather than a separately authored doc |
| Brownfield seed by agent | — | code-charter's "agent-detected flows" is the existing attempt at this |
| User-authored | — | The inversion above |

Nothing in overstory is contradicted. The deliverable description in 3-canonical-docs ("a skill that creates and maintains these docs") is what shifts — *maintains/checks* becomes primary, *creates* becomes seed-only.

## Critique

### Of the framing

1. **"How to represent the high-level view" is less open than it looks.** The bullet-tree-with-linked-sub-headings form in the considerations files *is* a candidate and is already working for plans. The genuinely undecided parts are narrower:
   - the **node vocabulary** — only capability statements, or also invariants, motives, decisions? (the considerations files mix all four, plus process rules)
   - what a **level** means — containment of functionality, chosen by the user; explicitly *not* the call-graph or module structure (code-charter's flows are call-graph umbrellas — a mechanism grouping, which the zoomed-out view must not mirror)
   - the **leaf binding primitive** — symbol? entry-point symbol + ariadne call-graph closure (= a code-charter flow)? test? file glob?
2. **The practice docs can't demonstrate the essential feature.** Leaf→code binding never appears in the considerations files because they are about plans. The catalog needs at least one code-bound specimen from day one.
3. **"Guaranteed live" + "plain markdown, no transclusion" is consistent only with a mixed-authorship rule**: the tool rewrites link targets, never node text. Worth stating as a principle.
4. **"User writes mostly" is aspirational in one respect**: many code changes arrive via agents from chat, not from tree edits. The reverse direction (code diff → proposed node edits for approval) is equally load-bearing. Overstory already has that half (route-diff-to-doc, anti-rot); the framing adds the forward half (tree edit → "implies code change" flag). Both directions + the representation = the whole product.
5. **Merging planning and canonical into one tree with per-node state is elegant**, but "implementation planning stays separate" (4-planning-doc) still needs its home — the sub-task files. Keep that.

### Of overstory in light of it

- **The functionality-docs probe programme is built on the old premise** (AI generates, terse typed feedback, ~2h budget). Tasks 02/03 (AI writes canonical + delta docs) lose centrality; 04-harnesses (fresh-reader exam, plan-from-doc) stay valuable because they test the *tree* regardless of author; 01's golden ledger becomes the catalog's home. The todo item "Run the functionality-docs probe rounds" should be rescoped, not run as-is.
- **The code-charter relationship moves earlier.** 1-local-project-reorientation parks code-charter and defers the shared-substrate decision with drift-sync. The framing doesn't un-park the vehicle (VSCode/React Flow), but it makes ariadne a direct dependency of the representation, and makes the drift reconcile engine (hook → sub-agent → re-anchor onto renamed symbol) the obvious existing implementation of "keep links live". Still keep that decision *after* the representation is hand-designed, so link machinery doesn't dominate.
- **2-research gets a sharper question.** The strongest prior art for "human-authored functionality, machine-bound to code, checked for drift": **Living Documentation** (Martraire), **BDD / Specification by Example** (Adzic — human-written behaviour bound to code via step definitions is literally this pattern), **requirements traceability matrices** (requirement ↔ code ↔ test), **C4** (zoom levels with one rule per level), **user-story mapping** (activities → tasks tree). Worth queueing ahead of the current general list.

## Proposed evolution of overstory (losing nothing)

- **3-canonical-docs**: rewrite the top bullets around the inversion — human-authored tree; node vocabulary; leaf binding primitive; the mixed-authorship rule; both sync directions. The skill deliverable becomes *seed + check + bind*, not *write*.
- **Representation catalog as a first-class item**: a small set of hand-authored specimens on real subjects, each naming the feature it locks in — zoomed-out node, mid node with intro sentence, code-bound leaf, motive sub-bullet, lens/cross-link, planned-unbuilt node, drifted node. It absorbs the golden ledger idea from functionality-docs/01.
- **4-planning-doc**: add the "computed overlay" candidate (git diff of the tree + classifier highlight, rendered in plannotator) alongside the authored-overlay one; the highlight question stays open.
- **functionality-docs programme**: rescope to harnesses + checker evals + an honest test of whether the catalog suffices as a seed spec.
- **1-reorientation**: one line — code-charter's *ideas and drift engine* are inputs to this; the vehicle stays parked.

## Simple way forward

1. **Catalog by hand** (writing time, nothing to build): pick one brownfield repo ariadne parses and the user knows well — code-charter's `drift` package or ariadne core — and write its functionality tree by hand, ~2 levels, leaves as plain `path#symbol` links. This *is* the specimen set; it also pre-empts the seed question.
2. **Liveness checker v0** (deterministic, no AI, small): walk the tree, resolve every `path#symbol` through ariadne, report dead/moved links. First real ariadne dependency, minimal.
3. **Edit classifier v0** (the one AI task): given a tree diff, verdict per changed node — wording vs functionality change — with golden cases from real edits. Gradeable; slots into the eval home.
4. **Render** via plannotator over the markdown; no custom UI.
5. **Only then** try an AI brownfield seed on a second repo, to test whether the catalog really locks in what is wanted.

Sequencing caveat: this competes with "cairn ships first" for attention. Step 1 is pure writing and could run alongside; steps 2–3 are build work and probably belong after cairn.

## Open questions

- **Node vocabulary** — capability statements only, or capabilities + invariants + motives?
- **Leaf binding** — single symbol, or entry-point + call-graph closure (the code-charter flow)?
