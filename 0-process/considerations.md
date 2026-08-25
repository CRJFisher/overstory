# Process considerations

- The central unsolved problem: prompting AI to describe work at the functionality layer — the two failure directions are bloat, and assuming the reader already knows the area
- Comprehension remains the goal throughout; it becomes implicit in managing canonical + planning docs well
- Decide the finishing line up-front — a shipped product that lands well — and filter every scoping decision through it
  - the route emerges through probes; the destination doesn't
  - how it lands is open — code-charter as the distribution point, and/or a modular standalone plugin for claude-code and other coding agents (codex, opencode) — tracked in [1-local-project-reorientation](../1-local-project-reorientation/considerations.md)
- Get something small and useful working early, then iterate — aiming for productivity self-acceleration (the tooling improves the process that builds the tooling)
- [Too complex to plan upfront — work in short probe → feedback → re-plan cycles; the plan emerges](#the-probe-loop)
- [Capture every confirmed win before moving on](#capture-every-confirmed-win)
- [Apply the principles of the target functionality as part of the process](#apply-the-principles-of-the-target-functionality)
  - practising them needs no implementation, and stress-tests them before any tooling exists
- Research is continual, not a phase — external findings distilled into routable references (→ [2-research](../2-research-into-knowledge-representations/considerations.md))
  - motive, reuse: working patterns already exist in the wild — find them rather than reinvent them
  - motive, landing: see what exists and what people are writing about, then decide how this ships
    - e.g. the "comprehension debt" discourse resonates with the mission — comprehension and plan-verification/refinement speed is the main bottleneck once coding agents arrive
- When translating functionality into implementation plans, name the major patterns being applied and draw module boundaries along them
  - pattern-aligned modules are maximally reusable and carry minimal maintenance burden
  - a module definition acts as a functionality moat, keeping its core pattern from dissolving into surrounding code

## The probe loop

How each probe round is set up, judged, and closed.

- Prototype on real deliverables only — never generate a document just to review it
- Probe one variable at a time; keep feedback terse and typed (B bloat / M mechanism / F foreign)
- Generate several outputs per variant before judging — same-prompt variance can exceed the difference between variants
- Include one rule-free variant per round — otherwise the process can only converge on current taste
- Adopt strong-prior ideas by decision; spend feedback time only on genuinely open questions
- Test docs by use, not style: can a context-free reader answer capability questions from the doc; can an agent plan the right change from the doc alone
- After each feedback round: fold the verdicts into rules/examples, regenerate the same source, advance only when it comes back clean
- The loop is proven once already ([plandoc responder-brevity](../../_archive/cdoc-interactive/01.4-responder-brevity.md)): quote the bad output → root cause → template + ban-list fix → re-run the same round
- Full probe programme with sequencing and evidence: [functionality-docs](../../functionality-docs/README.md)

## Capture every confirmed win

What a captured win looks like, and how the resulting rules and checks stay honest.

- Each win is captured as one of:
  - a deterministic validation script, where the feature is countable
  - a golden/anti example with expected check results — so later "improvements" can't silently unlearn a past verdict
  - a noted-but-uncodified observation — never force taste into a bogus rule
- Golden eval sets are how AI functionality gets "captured", making forward iteration safe
- Every rule records the verbatim feedback that created it; contradictions surface for a decision; prune rules periodically
- Every automatic check names how it can be gamed, and which judgment check catches that

## Apply the principles of the target functionality

The principles in question are those embedded in the functionality this project aims to build downstream.

### Hierarchical functionality description

- These considerations files use the functionality-tree form from [3-canonical-docs](../3-canonical-docs/considerations.md): simple-as-possible bullets, each able to link to a sub-heading expanding its sub-functionality (this section is the form in use)
  - sub-bullets only for notes that would otherwise be lost, such as subtle or non-obvious motivations
  - until the prompting problem is solved, prefer primitive representations (bullet trees) over prose
  - the tree is imposed; relationships that escape it become sparse cross-links (→ [tree, not graph](../3-canonical-docs/considerations.md#tree-not-graph))

### Complexity management

- A file's top level stays short and distributes its concerns well to the eye, so the reader routes to the relevant section quickly
  - the check is human for now — the user returns to these docs and feeds back when they can no longer hold the structure in working memory; a deterministic validation component may come later

### Deterministic enforcement of working rules

- Enforce adherence to the principles deterministically — e.g. a hook triggers a sub-agent review of what has just been done
  - the same ratchet logic as [capture every confirmed win](#capture-every-confirmed-win): that locks in probe verdicts, this polices process adherence
