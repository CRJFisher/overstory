# Analysis 2 — typed statements, session capture, and reader state

Discussion capture (2026-08-25): evaluating four new thoughts against the corpus — multiple kinds of statement beyond functionality, session analysers mining the user's own inputs, a markdown + meta.json source of truth, and per-reader comprehension tracking. Companion reading: [analysis](analysis.md), [3-canonical-docs](3-canonical-docs/considerations.md), [question register](2-research-into-knowledge-representations/question-register.md).

## The thoughts, decomposed

1. Functionality is not the only kind of statement worth capturing — decisions, principles, and others need a home ("thought primitives")
2. GranuSum's premise re-read: a summary serves different users with different priorities — the kind of statement is a reader-preference axis, like granularity
3. Session analysers asynchronously classify the user's prompts and answers into statement kinds and feed a curated source of truth
4. That source of truth is markdown paired with an `X.meta.json` sidecar tagging snippets; edits mark snippets changed and can trigger drift agents that investigate blast radius and propose changes
5. Per-reader comprehension state: evidence that a specific user has engaged with a node, stored as metadata, rendered as a UI highlight, testable by quiz; agent-autonomous decisions the user never saw are the debt unit

## 1. Multiple statement kinds — this is Q1, with a synthesis available

- Not a new question: Q1 (node vocabulary — capability only, or also invariants, motives, decisions) has been open since [analysis](analysis.md#open-questions)
- What is new is the reading of GranuSum: the kind axis is a **reader-preference axis**, parallel to granularity — different readers foreground different kinds
  - partially banked already: R-028 (tiers address different actors), R-029 (a level is where the text appears), G4.A4's expertise-reversal consequence (the audience split belongs at the zoom level); the kind axis is the second preference axis beside zoom
- Evidence against kinds-as-tree-nodes, already in hand: G1.A2 (the minimum vocabulary supporting a stop rule is capability + assumption; motives and decisions appear nowhere in it); the capability-only fiat in [3-canonical-docs](3-canonical-docs/considerations.md); the banked Q1≡Q5 finding (vocabulary = what is load-bearing)
- Evidence that other kinds need a home somewhere: G4.A1 (EARS invariant-shaped patterns are a large labelled fraction of real requirement corpora); [0-process](0-process/considerations.md) already admits motives as sub-bullets; the considerations files mix all four kinds in practice
- The synthesis that keeps both: **the spine stays capability statements; other kinds attach, typed, to the node they qualify; a kind is a lens** ([tree-not-graph](3-canonical-docs/considerations.md#tree-not-graph) already defines lens = link-only view)
  - decisions attach to the nodes they changed (ADR-shaped)
  - principles span many nodes, so they live in their own small tree with cross-links — this repo already practises exactly that split (`rules/` beside the functionality docs)
- If ratified, this updates one bullet in 3-canonical-docs: "statements of functionality and nothing else" becomes a claim about the spine, not about what the source of truth may carry

## 2. Session capture — genuinely new, and it answers the corpus's biggest confirmed risk

- Nothing in the corpus mines the user's own session inputs; the existing intake lanes are external research and probe feedback
- [analysis critique 4](analysis.md#critique) named two sync directions (tree edit → code-change flag; code diff → proposed node edit); this is the **third, upstream direction**: intent captured at prompt time, before it is lossily compiled into a diff — G3.A2's diff-mining approximates downstream what the prompt states directly
- It bears on J-G6A6's confirmed finding (decay absent a forcing function is reliable): mining prompts makes authoring a **byproduct of prompting rather than a discipline** — the one capture path needing no forcing function on the human; and R-022's survivor mechanism (the model produces something on the critical path) is satisfied once the tree feeds agent context
- Tension to state plainly: this reintroduces AI-written node text — the Q7 register problem the authorship inversion was designed to shrink. Contained only if
  - the pipeline's output is **proposals for approval**, never direct writes (the same loop as the reverse direction), and
  - the source is the user's own words, so the task is R-034's select-then-re-register, not free generation
- The same classifiers also capture **agent-autonomous decisions** as unratified statements — the input that reader state (below) consumes

## 3. markdown + X.meta.json — a candidate already priced by queued research

- Sidecar vs inline markup vs typed fragments is G3.A5 verbatim, with the counter-evidence already priced: Hypothesis anchoring fails on short generic quotes, and a functionality-tree bullet is definitionally a short generic quote
- A sidecar keyed on **stable node ids** escapes that — and whether machine-written ids belong in a hand-authored file and survive hand-editing is G3.A4's one genuinely undecided question, with GO's immutable-id finding (G3.A6) as the supporting specimen
- Verdict: meta.json enters as a G3.A5 candidate **conditional on G3.A4's id verdict**, not as a decision; in-repo precedent for the shape is `SKILL.meta.json` as an opt-in contract ([1-reorientation](1-local-project-reorientation/considerations.md#claude-config-stays-consistent))
- The rest of the thought is the corpus's existing core loop, confirmed not extended: edits mark nodes changed (Q5 forward classification), drift agents investigate blast radius (G3.A1's suspect-link cascade — propagation depth is its named open decision), and propose changes (G3.A2's generation half)

## 4. Reader state — the one genuine framing extension

- Today's framing is two-way truth maintenance between tree and code; this adds a third party: **a node can be stale with respect to the code, and a reader can be stale with respect to a node** — the same suspect-link machinery pointed at a person
- The mechanism already exists in the corpus at one-bit, per-team resolution: Doorstop's `reviewed:` stamp (G3.A1) is comprehension evidence — "a human saw this version"; per-reader state generalises it
- Evidence sources, weakest to strongest: interaction-derived signals (Mylyn's DOI, G5.A2, is the same signal family); session-capture (thought 2) yields engagement evidence for free — a prompt referencing a node is evidence; quizzes are the strong-but-intrusive end, and the instruments are already queued (G4.A4's cloze and comprehension measures; functionality-docs/04's fresh-reader exam is the harness form of the same feature)
- The unification: **an agent-authored statement with zero reader evidence is the comprehension-debt unit** — capture (2) produces it, reader state renders it, the UI guides the eye to it
- Honest concerns:
  - engagement proxies are weak evidence of understanding; only use-based tests (answered a capability question, edited the node, planned from it) meet the corpus's own "test docs by use, not style" bar
  - per-reader state cannot live in the shared file — it is a second store keyed reader × node id, making it the **third** feature hanging on G3.A4's ids (after the overlay diff and the meta sidecar)
  - it presumes a rendering surface; "plannotator over markdown, no custom UI" is settled, so this lands as a tracked question, not a near-term deliverable — sequencing unchanged, cairn ships first
- G6.A5's strike ("nothing in comprehension-debt discourse plausibly changes how a delta renders") stands: this is not a Q6 payload; it is a new question

## Terminology

"Thought primitives" names the author's cognition; this realm names the artifact and the audience:

- the taxonomy of what a unit says: **statement kind** — the corpus already speaks Q1 as "node vocabulary" / "node kinds"
- the reader-preference axis: **concern** (ISO/IEC/IEEE 42010: stakeholders hold concerns, viewpoints frame them, views render them — the GranuSum reading is that standard's model exactly)
- the decisions-and-principles cluster specifically: **design rationale** (IBIS/QOC/ADR lineage)
- if one umbrella word is wanted: **intent** — typed intent statements; matches the constitution's intention tree and covers agent-made decisions the user has not ratified

Recommendation: statement kinds inside the tree, concerns for the per-reader axis; retire "thought primitives".

## What changes where — pending ratification

- [3-canonical-docs](3-canonical-docs/considerations.md): the capability-only bullet becomes a spine claim; add typed attachments and kind-as-lens; add session capture as an intake consideration; note meta.json as the G3.A5-conditional candidate
- [0-process](0-process/considerations.md): "comprehension … becomes implicit" weakens — reader state would make comprehension explicit product functionality; the comprehension-debt line under research motives gains that note
- [4-planning-doc](4-planning-doc/considerations.md): one line — a reader-state overlay is a further overlay type, explicitly deferred
- [question register](2-research-into-knowledge-representations/question-register.md): candidate Q12 session capture (utterance → classified statement → proposed tree edit; prior art: intent mining from developer conversations, commit-intent classification) and candidate Q13 reader state (evidence, storage, rendering; prior art: degree-of-knowledge models — Fritz & Murphy's DOK, Mylyn DOI — and knowledge tracing / spaced repetition); both deferred behind G1–G3
- [context.md](2-research-into-knowledge-representations/context.md) and the premise sentence stand unchanged until the above is ratified
- [todo](todo.md) and sequencing: unchanged

## Open questions

- Does the spine-plus-typed-attachments synthesis survive contact with real material — or do decisions and principles demand spine positions of their own?
- What counts as admissible comprehension evidence, at what cost to the reader? (the Q13 framing question)
- Does session capture stay within proposals-for-approval, or does the volume of captured statements overwhelm the curation the inversion depends on?
