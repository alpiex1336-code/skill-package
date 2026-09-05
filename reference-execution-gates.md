# Execution gates — operational reference

Companion to the governing contract in SKILL.md. This file supplies compiler
checks, launch templates, ledger fields, and violation recovery. It does not
define a second lifecycle.

## Canonical order

    Read
      → Intent analysis and clarification
        → Review Prompt Compiler
          → Multi-role review
            → Integrate
              → Work Filter
                → Edit Prompt Compiler
                  → Edit
                    → Verify

Load this file before compiling reviewer packets or edit packets and before the
first in-scope artifact write.

## Runtime-first probe

At the start of reviewer orchestration:

1. Check whether runtime subagent or equivalent delegation tooling is available.
2. If available, launch multiple independent reviewers with distinct composed
   labels and linted Review Prompt Packets.
3. If unavailable or blocked, record the reason in the ledger and run labeled
   simulated passes using the same packets.
4. Never treat one blended internal monologue as multi-role review.

## Sizing by evidence, stakes, scope, and coverage

| Engagement | Initial composed labels | Runtime reviewers when available | Further waves |
|---|---:|---:|---|
| Small behavior-changing artifact | 2–4 | at least 2 | until no new viable theme_key |
| Feature or multi-surface change | 4–8 | at least 2 in parallel | 1–3 or saturation |
| Release, launch, or broad governance | 8–18 | parallel by independent boundary | until coverage and audits close |
| Security incident or high-stakes change | 6–10 focused roles plus mandatory audits | parallel where safe | until acceptance holds |

These are starting bands, not quotas. Add roles when a new draw is likely to
cover a missing aspect class or failure mechanism. Stop on evidence, not volume.

## Intent Brief readiness check

Before compiling reviewer packets, confirm that the Intent Brief contains:

- a stable intent_brief_id;
- explicit request, artifact, audience, and desired outcome;
- a deeper-purpose hypothesis tied to observed evidence and confidence;
- named pain points;
- success criteria and observable evidence;
- constraints, non-goals, and protected invariant;
- observed evidence separated from assumptions and unknowns; and
- resolution of any question that could materially change direction, safety,
  scope, or acceptance.

If a field is unavailable, mark it unknown. Do not invent it. Ask the user only
for a direction-changing unresolved choice.

## Review Prompt Compiler

Compile one packet per reviewer from the same immutable Intent Brief and Snapshot.
The distinct boundary and targeted questions change by role; facts and protected
constraints do not.

### Review Prompt Packet template

    review_prompt_id: RPP-<wave>-<role>
    intent_brief_id: <id>
    composed_role: [Slot A][Slot B][optional Slot C][optional Slot D]

    PURPOSE
    Why this reviewer is launched and which Intent Brief pain point, criterion,
    or coverage gap it should protect or challenge.

    SHARED IMMUTABLE CONTEXT
    Artifact and audience:
    Explicit request and desired outcome:
    Deeper-purpose hypothesis, evidence, confidence:
    Protected invariant:
    Constraints and non-goals:
    Snapshot evidence:
    Assumptions and unknowns:

    DISTINCT ROLE BOUNDARY
    Domain of strength:
    Included surfaces:
    Excluded surfaces:
    Why this boundary is orthogonal to the other packets:

    TARGETED QUESTIONS
    1. <question tied to a pain point, criterion, or coverage gap>
    2. <question that asks for contrary evidence or a failure mechanism>
    3. <question that identifies a fitting verification check>

    EVIDENCE REQUIREMENTS
    Cite exact files, sections, observed behavior, command output, screenshots,
    standards, or explicitly missing evidence. Separate observation from inference.

    FORBIDDEN ASSUMPTIONS AND ACTIONS
    Do not infer private user motives. Do not implement, merge other roles,
    expand scope, invent tool results, or present the deeper-purpose hypothesis
    as fact.

    OUTPUT CONTRACT
    Return 3–8 numbered findings. Each must include composed_role, finding_id,
    linked criterion or pain_point, evidence, confidence, suggested theme_key,
    and verification gap. Do not synthesize or edit.

### Review packet lint

Block launch when any answer is yes:

- Does the packet lack an intent_brief_id or criterion/pain-point link?
- Does it alter shared facts or constraints?
- Does it rely on an unsupported motive or capability?
- Are its questions generic enough to fit any artifact unchanged?
- Is its role boundary indistinguishable from another packet except for the label?
- Does it omit evidence requirements, forbidden actions, or the output contract?
- Could its output not enter the trace chain as a finding_id?

Record PASS or FAIL and the corrected packet id in the ledger.

## Runtime launch pattern

Launch independent packets in parallel when their boundaries do not depend on one
another. Every launched prompt includes the full packet and relevant excerpts or
paths a fresh reviewer needs. Each reviewer returns only its bounded output.
Reject unlabeled findings, invented evidence, and cross-role synthesis.

For skill-package governance, useful orthogonal pairs include:

- [maintainability-first, structural-dedup-minded][information architect]
- [execution-contract-enforcing][process auditor]
- [intent-faithful, uncertainty-explicit][prompt engineer]
- [verification-first, contradiction-seeking][acceptance reviewer]

Labels are examples, not a fixed roster.

## Integration and Work Filter checklist

Before compiling any Edit Prompt Packet:

- [ ] All accepted raw findings have composed labels and finding_ids.
- [ ] Each finding traces to a Review Prompt Packet and criterion or pain point.
- [ ] Findings are merged into non-duplicative theme_key rows.
- [ ] Conflicts are resolved explicitly using evidence and impact.
- [ ] The Work Filter is applied to integrated rows, not raw comments.
- [ ] Accepted rows have evidence, scope, acceptance criteria, and verification.
- [ ] Rejected rows retain a reason.
- [ ] An honest zero-adopt stop is recorded if no row passes.

## Edit Prompt Compiler

Compile one packet per accepted theme_key. Batch only tightly coupled themes whose
implementation or verification cannot be separated; record the dependency reason.

### Edit Prompt Packet template

    edit_prompt_id: EPP-<theme>
    intent_brief_id: <id>
    theme_key: <id>
    source_review_prompt_ids: <ids>
    source_finding_ids: <ids>

    PAIN POINT AND EVIDENCE
    Criterion or pain point:
    Failure mechanism:
    Accepted evidence:
    Why the row passed the Work Filter:

    TARGET
    Files or surfaces:
    Current behavior:
    Desired outcome:

    BOUNDARIES
    In scope:
    Non-goals:
    Protected invariant:
    No-cross-theme rule:
    No unrelated files or behavior:

    ACCEPTANCE
    Acceptance criteria:
    Verification plan:
    Evidence to return:
    Residual-risk handling:

    EXECUTION
    Implement only this theme_key.
    Match repository or document conventions.
    If a new issue appears, report a proposed finding_id; do not edit it.
    Return changed artifacts, exact changes, verification performed, and gaps.

### Edit packet completeness and contradiction lint

Block delegation when any answer is yes:

- Is the theme absent from the accepted register?
- Does any source id or trace link fail to resolve?
- Is the pain point vague, unsupported, or detached from the Intent Brief?
- Are files or surfaces, desired outcome, or scope missing?
- Does the requested change contradict a constraint, non-goal, protected invariant,
  or another accepted packet?
- Are acceptance criteria subjective or unverifiable?
- Is verification absent or incapable of proving the desired outcome?
- Could the agent implement another theme without violating the packet?
- Does batching hide separable themes?

The parent records PASS or FAIL before launch. A failed packet is corrected, not
delegated.

## Delegated Edit rule

When runtime delegation exists, every accepted theme must be implemented by a
delegated implementation agent operating under its linted Edit Prompt Packet.
One agent may implement multiple themes only when they are tightly coupled and
the ledger records the dependency reason and packet ids. The parent may read,
compile, integrate, filter, lint, coordinate, and verify; it may not implement
accepted themes inline after using subagents only as reviewers.

When delegation is unavailable, the ledger records the blocker and substitute
path before parent implementation. The parent then follows the same linted packet,
scope, no-cross-theme, trace, and verification obligations.

## Wave ledger template

Create this ledger in-session before Edit and update it through Verify:

    wave_id: wave_<n>
    intent_brief_id: <id>
    coverage_set: <aspect ids>
    applicable_P0: <families or N/A with reason>
    review_prompt_ids:
      - <id>: <composed label> — lint PASS
    runtime: subagents × N | simulated substitute because <reason>
    findings: <finding_ids>
    merged_theme_keys: <ids>
    adoption:
      - <theme>: accepted or rejected — Work Filter reason
    edit_prompt_ids:
      - <id>: <theme> — lint PASS or FAIL
    delegation: <agent mapping or recorded blocker>
    trace_status: PASS | FAIL
    verification_ids: <ids or pending>
    residual_risk: <honest gaps>
    saturation_status: continue | stop — <evidence>

The ledger may point to stored packets rather than duplicating their full text.

## Trace guard

Before Edit, verify:

    intent_brief_id
      → criterion or pain_point
        → review_prompt_id
          → finding_id
            → theme_key
              → edit_prompt_id
                → planned changed artifact

After Verify, append verification_id. An unresolved or orphan link blocks the
associated change from implementation or acceptance.

## Verification and independent acceptance

Run checks proportionate to the artifact:

- project-standard format, type, test, build, or static checks when present;
- manual or browser smoke checks for important visible flows;
- document link, heading, terminology, and contradiction checks for governance;
- security, privacy, accessibility, performance, or compliance checks when their
  risk surfaces apply.

Then launch a fresh acceptance reviewer when runtime delegation is available. Its
prompt receives the Intent Brief, accepted packets, changed artifacts, acceptance
criteria, and verification output, but not a request to defend the implementation.
It must try to disprove success and return verification_ids, failed criteria,
or residual risks. State any substitute when independent execution is unavailable.

## Violation detectors and recovery

| Violation | Required recovery |
|---|---|
| Artifact write before Intent Brief and reviewer packets | Halt; return to Read |
| Generic reviewer prompts differing only by label | Recompile and relint packets |
| Raw finding implemented without integration and Work Filter | Revert the proposal path; create a theme row |
| Ledger first appears after Edit begins | Halt; reconstruct the ledger from evidence before continuing |
| Parent implements any accepted theme while delegation exists | Halt; map every accepted theme to a delegated packet or documented tight batch |
| Edit packet lacks trace or acceptance criteria | Block launch; correct and relint |
| Orphan changed artifact | Do not accept; restore trace or remove the unrelated change |
| Verification claim without evidence | Correct the claim and record the gap |

Recovery never fabricates missing evidence. Resume only when the affected gate
passes and the ledger records the repair.

## PRE-FLIGHT quick copy

    PRE-FLIGHT
    1. SCOPE: artifact, audience, protected invariant
    2. INTENT: intent_brief_id; unresolved direction-changing questions
    3. COVERAGE: target set; P0; gaps
    4. REVIEW: packet ids and lint; runtime or substitute
    5. INTEGRATION: theme_keys and Work Filter decisions
    6. LEDGER: in-session location
    7. EDIT: packet ids and lint; delegation mapping
    8. TRACE: PASS or unresolved links
    ORCHESTRA GATE: PASS | FAIL

If FAIL, do not edit.
