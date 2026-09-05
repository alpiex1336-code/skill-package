---
name: deep-harness
description: >-
  Use Deep-Harness only when the user explicitly invokes $deep-harness or names
  Deep-Harness; asks to substantively improve, optimize, refine, or harden an
  existing artifact; explicitly requests deep, rigorous, multi-angle, multi-role,
  or orchestrated reasoning; or asks to design, evaluate, or improve an AI-agent
  harness. It runs a mandatory runtime-first lifecycle with intent analysis,
  AI-compiled reviewer and edit prompts, multi-role review, integration, Work
  Filter, traceability, delegated edits, and independent verification. Do not
  activate merely because an ordinary task creates, changes, reviews, or codes an
  artifact; incidental phrases such as deep learning or deep link, and ordinary
  test harnesses, do not trigger it.
---

# Deep-Harness

## Activation contract

Activate this skill only when at least one condition is true:

- The user explicitly invokes **$deep-harness** or names **Deep-Harness**.
- The user asks to **substantively improve, optimize, refine, or harden an
  existing artifact**, beyond a routine edit or generic review.
- The user explicitly asks for a **deep, rigorous, multi-angle, multi-role, or
  orchestrated reasoning process**.
- The task designs, evaluates, or improves an **AI-agent harness**: agent
  orchestration, prompt compilation, tool routing, execution gates, evaluation,
  or traceability.

Do not activate merely because an ordinary task creates, changes, reviews, or
codes an artifact. Ordinary feature creation, factual lookup, routine editing,
and generic code review remain ordinary work unless one activation condition is
also present. **Deep** means an explicit request for a more rigorous or deeper
process; incidental domain phrases such as **deep learning** or **deep link** are
not signals. **Harness engineering** here means AI-agent execution control, not
an ordinary software test harness unless the user explicitly invokes this skill.

Automatic discovery remains enabled so substantive improvement and harness work
can activate the skill without exact command syntax. Once activated, the full
canonical lifecycle below is mandatory.

## Canonical lifecycle

This is the only main procedure in the package. Do not reorder, rename, skip, or
replace its phases with a parallel workflow after activation.

    Read
      → Intent analysis and clarification
        → Review Prompt Compiler
          → Multi-role review
            → Integrate
              → Work Filter
                → Edit Prompt Compiler
                  → Edit
                    → Verify

After **Verify**, reflect and re-enter the same lifecycle only when verification
or a fresh orthogonal review supplies new evidence or a new viable theme_key.
Otherwise stop under the saturation rule.

## Canonical definitions

### Snapshot

The evidence actually available in the session: opened files, tool output,
screenshots, user-provided material, and explicit conversation facts. Guesses,
remembered repository state, unverified integrations, and inferred motives are
not Snapshot facts.

### Intent Brief

The single evidence-bounded analysis produced after **Read**. It operationalizes
what the user is trying to accomplish without pretending to read their mind. It
has these fields:

- intent_brief_id
- explicit_request
- artifact, audience, and desired_outcome
- deeper_purpose_hypothesis, with supporting Snapshot evidence and confidence
- pain_points
- success_criteria and the evidence that would demonstrate success
- constraints, non_goals, and protected_invariant
- observed_evidence
- assumptions and unknowns
- direction_changing_questions

Ask the user only when unresolved ambiguity would materially change direction,
safety, scope, or acceptance. Otherwise record a bounded assumption and proceed.
The deeper-purpose hypothesis is revisable and must never be presented as fact.

### Review Prompt Packet

The single canonical specification for a reviewer launch, compiled by the
orchestrating AI from the Intent Brief and Snapshot. Each packet contains a shared
immutable context plus one distinct composed role boundary, targeted questions,
evidence requirements, forbidden assumptions and actions, and a bounded output
contract. Packets that differ only by role labels fail linting. Operational
templates live in [reference-execution-gates.md](reference-execution-gates.md).

### Edit Prompt Packet

The single canonical specification for one accepted implementation theme,
compiled by the orchestrating AI only after **Integrate** and **Work Filter**.
Each packet contains the accepted theme_key, pain point and evidence, target
files or surfaces, desired outcome, scope, non-goals, protected invariants,
acceptance criteria, verification plan, and a no-cross-theme rule. The parent
must lint each packet for completeness and contradiction before delegation.
Operational templates live in
[reference-execution-gates.md](reference-execution-gates.md).

### Composed role label

A minimum two-part reviewer label, [Slot A][Slot B]: Slot A determines how
attention is aimed and Slot B identifies the stance holder. Optional [Slot C]
may name a verified tool surface; optional [Slot D] may name an installed,
fully read, relevant skill. See
[reference-word-banks.md](reference-word-banks.md).

### Target coverage set

The aspect classes plausibly relevant to this engagement, derived from the
Snapshot, Intent Brief, user constraints, and applicable sections of
[reference-depth-domains.md](reference-depth-domains.md). It is not a fixed list.
Use complement-biased role selection to cover underrepresented classes.

### Quintessence row

One canonical theme_key row created by integrating overlapping findings,
discarding noise, recording evidence and conflict resolution, and applying the
Work Filter. Raw reviewer comments never flow directly to Edit.

## Non-negotiable execution gates

These gates enforce the canonical lifecycle before any in-scope artifact write.
Operational checklists, compilers, packet templates, and recovery procedures live
in [reference-execution-gates.md](reference-execution-gates.md).

### Gate 1 — Intent and review packets

- Read the relevant artifact and package instructions fully.
- Produce the Intent Brief.
- Declare the target coverage set and applicable P0 role families.
- Compile and lint distinct Review Prompt Packets.
- If runtime subagent tooling exists, launch multiple runtime reviewers; otherwise
  record why it is unavailable and run labeled simulated passes as a disclosed
  substitute.
- Every reviewer must return its composed label and bounded, evidence-linked
  findings. One generic voice rotating hats is prohibited.

### Gate 2 — Integrate and filter

- Merge findings into stable theme_key rows.
- Deduplicate redundant role angles and findings.
- Resolve conflicts using evidence, severity, user-harm reduction, and
  verification ease, not vote count.
- Apply the Work Filter to integrated rows only.
- Stop honestly if nothing passes; do not manufacture an implementation task.

### Ledger checkpoint — before Edit

Start an in-session wave ledger before the first in-scope artifact write. Record
the Intent Brief id, reviewer packet ids and labels, merged theme_keys,
adoption decisions, packet-lint results, delegation status, verification pointers,
and skipped or substituted obligations. The terminal reply cannot be the ledger's
first appearance after implementation has begun.

### Gate 3 — Edit packets and delegated implementation

- Compile one Edit Prompt Packet per accepted theme_key; batch only tightly
  coupled themes and record why.
- The parent validates completeness, contradiction, traceability, and
  no-cross-theme boundaries before launch.
- When runtime delegation exists, every accepted theme must be implemented by a
  delegated agent under its linted packet, or by one documented agent batch for
  tightly coupled themes. The parent orchestrates, integrates, lints, and
  verifies; it does not implement accepted themes inline.
- When delegation is unavailable, record the blocker and substitute path before
  parent implementation; the same packet, scope, trace, and verification rules
  still apply.
- An implementation agent may edit only its packet's theme. A newly discovered
  issue returns as a proposed finding and must re-enter the lifecycle.

### Gate 4 — Verification and acceptance

- Run project-standard automated checks when available and appropriate manual or
  browser checks for important user-visible flows.
- Launch an independent acceptance reviewer when runtime delegation is available;
  otherwise record the substitute and correlation risk.
- State only what actually ran. Record unverified claims and residual risk.
- Block orphan edits: every changed artifact must have a complete trace chain.

## Traceability contract

Every accepted change must preserve this chain:

    intent_brief_id
      → criterion or pain_point
        → review_prompt_id
          → finding_id
            → theme_key
              → edit_prompt_id
                → changed artifact
                  → verification_id

Missing links block Edit or acceptance. The action register and ledger carry the
ids; rejected rows remain recorded with reasons to prevent rediscovery loops.

## PRE-FLIGHT

Complete this compact record before the first in-scope artifact write:

    PRE-FLIGHT
    1. SCOPE: artifact, audience, protected invariant
    2. INTENT: intent_brief_id; direction-changing questions resolved or bounded
    3. COVERAGE: target set; applicable P0 families; known gaps
    4. REVIEW: N distinct packets; runtime delegation available or substitute recorded
    5. INTEGRATION: theme_keys merged; Work Filter decisions complete
    6. LEDGER: current wave recorded in-session
    7. EDIT: packet ids compiled and linted; delegation plan recorded
    8. TRACE: no orphan accepted action or planned change
    ORCHESTRA GATE: PASS | FAIL

If FAIL, do not write the artifact. Read-only inspection, research, prompt
compilation, subagent launches, integration, and ledger preparation remain allowed.

## Execution contract

### Runtime-first multi-role review

Use as many orthogonal composed roles as stakes, uncertainty, scope, and coverage
justify. The minimum for artifact-changing work is more than one. Increase roles
or waves while new failure classes or credible theme_keys appear. Role prompts
must be compiled from the same Intent Brief while targeting distinct boundaries;
do not leak another role's private reasoning into a fresh pass.

Use real runtime subagents whenever available. A simulated fallback must use the
same labels, packets, bounded outputs, integration rules, and ledger disclosure,
while acknowledging weaker process isolation.

### Prompt compiler discipline

The orchestrating AI writes the prompts that guide each stage; it does not merely
attach a persona to a generic request.

- The **Review Prompt Compiler** converts the Intent Brief, Snapshot, coverage
  gaps, and role boundary into a targeted Review Prompt Packet.
- Its lint rejects absent evidence hooks, invented context, overlapping role
  boundaries without purpose, generic questions, and outputs that cannot be
  integrated into findings.
- The **Edit Prompt Compiler** converts one accepted Quintessence row into an
  implementation-ready Edit Prompt Packet aimed directly at the demonstrated pain
  point.
- Its lint rejects missing acceptance criteria, missing verification, contradiction
  with the protected invariant, hidden scope expansion, and cross-theme edits.

Compiler output is an auditable control artifact, not decorative prose. Preserve
packet ids and trace pointers in the ledger.

### Integration and convergence

Group raw findings by theme_key in one pass where practical. Merge duplicates,
mark conflicts, and preserve source-role and evidence links. A single independent,
high-severity, reproducible finding can outweigh many cosmetic echoes. See
[reference-workflow-registers.md](reference-workflow-registers.md) for registers,
conflict resolution, and stop rules.

### Reflection and saturation

After Verify, challenge whether evidence supports the claimed outcome, whether a
newcomer or maintainer still encounters the pain point, and whether the protected
invariant survived. Re-enter **Read** only for a new failure mode, new evidence,
a failed acceptance criterion, or a new Work Filter-viable theme. Rephrased advice,
cosmetic churn, and repeated findings are stop signals.

## Workflow

1. **Read** — Read the user request, active artifact, relevant configuration, and
   required skill references. Build the Snapshot; preserve existing user work.
2. **Intent analysis and clarification** — Produce the Intent Brief. Separate
   explicit facts from hypotheses. Ask only direction-changing questions.
3. **Review Prompt Compiler** — Select orthogonal composed roles against the target
   coverage set; compile and lint one distinct Review Prompt Packet per role.
4. **Multi-role review** — Launch runtime reviewers in parallel when possible.
   Collect labeled findings, questions, evidence, proposed theme_keys, and
   verification gaps.
5. **Integrate** — Merge overlapping findings into Quintessence rows, deduplicate,
   and resolve conflicts. Maintain source and trace ids.
6. **Work Filter** — Accept only useful, in-scope, evidence-grounded, safe,
   non-redundant actions with a credible verification path.
7. **Edit Prompt Compiler** — Compile and lint one precise packet per accepted
   theme, aimed at the causal pain point and protected by explicit boundaries.
8. **Edit** — Delegate every accepted theme when runtime delegation is available,
   using a documented batch only for tightly coupled themes. Preserve working
   behavior and prohibit unrelated changes.
9. **Verify** — Run fitting checks and independent acceptance review, update the
   trace and ledger, then reflect and stop or re-enter at Read on new evidence.

## Stochastic Role Orchestra

Sample Slot A + Slot B pairs from
[reference-word-banks.md](reference-word-banks.md), optionally adding verified
Slot C tools and fully read Slot D skills. Role selection combines diversity with
coverage: begin with applicable P0 families, then bias toward uncovered target-set
classes, and use later draws for genuinely new failure modes.

Each role receives only the immutable shared context and its own boundary. It
returns numbered findings tagged with its label, finding_id, evidence, suggested
theme_key, and verification gaps. Generic or unlabeled output is rejected.

Risk-triggered audits remain mandatory when relevant: authentication, payments,
health or sensitive data, public user-generated content, irreversible AI actions,
spend-capable automation, and regulatory claims. See
[reference-workflow-registers.md](reference-workflow-registers.md).

## Research and coverage

Use official standards, primary documentation, and appropriately licensed open
references when the Snapshot is thin. Research should answer a named Intent Brief
unknown or coverage gap. Cite only material actually consulted; patterns may inform
original work, but do not copy proprietary assets or unlicensed code.

Map the artifact to relevant sections of
[reference-depth-domains.md](reference-depth-domains.md). Coverage may include
correctness, security, privacy, accessibility, internationalization, visual and
interaction craft, performance, data, APIs, AI behavior, cost, operations,
compliance, documentation, and maintainer experience. Include only applicable
classes, and explain exclusions that could otherwise appear risky.

## Work Filter

An integrated row ships only when it is:

- useful against an Intent Brief pain point or success criterion;
- within user scope and compatible with the protected invariant;
- evidence-grounded, with uncertainty stated;
- safe, legally and ethically acceptable, and reversible where practical;
- non-duplicative and not cosmetic or architectural churn;
- implementable through a bounded Edit Prompt Packet; and
- verifiable through explicit acceptance criteria.

Reject or defer rows that require product direction the user has not supplied,
depend on unavailable capabilities, or cannot be distinguished from subjective
preference. Work Filter efficiency never waives gates, traceability, or verification.

## Tool and skill availability

Do not attach a tool to Slot C or claim it ran unless the current environment
confirms it. Do not attach a skill to Slot D unless its full instructions were
read in this session and it is relevant. Record unavailable capabilities and
substitutes in the ledger. Never invent credentials, repository state, telemetry,
test results, citations, or user motives.

## Resource, rights, and safety governance

Prefer official documentation, standards, and permissively licensed examples.
Record provenance and license constraints for imported material. Never expose
secrets or personal data, copy proprietary assets, bypass authentication, or
perform irreversible external actions without authority. High-stakes legal,
medical, financial, privacy, and security claims require current authoritative
evidence and explicit residual-risk handling.

## Recursive self-application

When this skill package is the artifact, run the exact canonical lifecycle with
artifact = SKILL.md plus applicable reference files and governance-focused
coverage: **Read → Intent analysis and clarification → Review Prompt Compiler →
Multi-role review → Integrate → Work Filter → Edit Prompt Compiler → Edit →
Verify**. The Intent Brief operationalizes the user's concepts; it does not paste
advice verbatim unless the user explicitly locks wording. Use runtime
meta-reviewers, delegate every accepted theme when runtime delegation is
available, and independently verify clarity, discoverability, gate enforceability,
companion consistency, and honest stopping. Re-enter only on new evidence or a
new viable theme.

## Companion references

- [reference-execution-gates.md](reference-execution-gates.md) — operational gate,
  compiler, packet, ledger, fallback, and recovery templates.
- [reference-word-banks.md](reference-word-banks.md) — composed-role vocabulary,
  P0/P1/P2 priorities, tool and skill availability rules.
- [reference-depth-domains.md](reference-depth-domains.md) — product-class coverage
  maps and failure prompts.
- [reference-workflow-registers.md](reference-workflow-registers.md) — action and
  coverage registers, severity, conflict resolution, traceability, and stop rules.
- [reference-platforms-extended.md](reference-platforms-extended.md) — optional
  platform examples; availability and current terms must be verified.

SKILL.md is the governing contract. Keep operational detail in the references.
When a companion conflicts, update the contract first and align the companion in
the same edit session.

## Done criteria

- The lifecycle ran in canonical order and its ledger appeared before Edit.
- Review prompts were purpose-targeted, role-distinct, evidence-bound, and linted.
- Accepted themes survived integration and the Work Filter.
- Edit prompts directly targeted demonstrated pain points and passed parent lint.
- Every changed artifact has a complete trace chain and fitting verification.
- Independent acceptance findings are resolved, rejected with reason, or recorded
  as residual risk.
- Remaining suggestions are duplicate, speculative, out of scope, blocked on user
  direction, or unable to pass the Work Filter; the run stops without claiming
  perfection.
