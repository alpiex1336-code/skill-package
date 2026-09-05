# Workflow registers, rubrics, and session rules

Companion to SKILL.md. Registers make the canonical lifecycle auditable and help
many reviewer outputs converge into a few evidence-backed actions.

## Intent register

Store one row per Intent Brief:

| Field | Purpose |
|---|---|
| intent_brief_id | Stable id for the run |
| explicit_request | User's stated request |
| artifact | Artifact under review or change |
| audience | Intended user, reader, maintainer, integrator, or operator |
| desired_outcome | Observable result the user wants |
| deeper_purpose_hypothesis | Supported, confidence-labeled interpretation |
| pain_points | Stable ids for demonstrated problems |
| success_criteria | Stable ids for observable success conditions |
| success_evidence | Evidence that would demonstrate each criterion |
| constraints | Requirements the change must honor |
| non_goals | Explicitly excluded work |
| protected_invariant | Purpose or behavior that must remain coherent |
| observed_evidence | Snapshot pointers |
| assumptions | Bounded inferences used to proceed |
| unknowns | Items not established as fact |
| direction_changing_questions | Resolved answers or none |

## Action register

Each row is one integrated Quintessence theme, not one raw reviewer comment.

| Field | Purpose |
|---|---|
| id | Stable action id |
| intent_brief_id | Source Intent Brief |
| criterion_or_pain_point | Stable source id |
| review_prompt_ids | Reviewer packets that produced supporting findings |
| finding_ids | Integrated source findings |
| source_roles | Distinct composed labels |
| theme_key | Stable merge bucket |
| summary | One verb-led action |
| severity | blocker, high, medium, low, or chore |
| user_visible | yes, no, or mixed |
| evidence | Reproduction, file, screenshot, standard, or stated judgment |
| acceptance_criteria | Observable definition of success |
| verification_plan | Command, manual flow, audit, or review |
| edit_prompt_id | Packet compiled after acceptance |
| changed_artifacts | Exact paths or surfaces |
| verification_ids | Evidence returned after Edit |
| status | proposed, accepted, in_progress, done, or wontfix |
| work_filter | Acceptance or rejection rationale |
| residual_risk | Honest unresolved uncertainty |

Rejected rows remain as wontfix with reasons to prevent rediscovery loops.

## Trace register

Every changed artifact must resolve this chain:

    intent_brief_id
      → criterion or pain_point
        → review_prompt_id
          → finding_id
            → theme_key
              → edit_prompt_id
                → changed artifact
                  → verification_id

Before Edit, verification_id may be pending; every earlier link must resolve.
After Verify, unresolved final links prevent acceptance.

## Severity rubric

- **Blocker:** data loss, account takeover, illegal exposure, unshippable failure
  on a primary journey, or a contradiction that makes safe execution impossible.
- **High:** serious security weakness, accessibility barrier, broken primary flow,
  chronic corruption risk, or governance that permits unauthorized change.
- **Medium:** material confusion, performance regression, missing common state,
  internationalization gap, or incomplete prompt boundary.
- **Low:** small but defensible clarity or consistency improvement.
- **Chore:** hygiene that removes real noise or enables accepted work.

Weight support by severity, independence, evidence, and verification ease, not
role count.

## Coverage register

Maintain a set of relevant aspect ids for the engagement. A useful starting
universe is:

correctness, security, privacy, performance, accessibility, internationalization,
user_experience, visual, motion, audio, gameplay, economy, multiplayer, ai_safety,
cost, deployment, observability, compliance, documentation, maintainer_experience,
prompt_precision, contract_consistency

Derive the actual target set from the Snapshot and Intent Brief. After each review
wave, union the aspects substantively covered. Bias later role packets toward
target-set gaps while information gain remains.

## Risk-triggered mandatory audits

Run an explicit evidence-seeking reviewer packet when any of these surfaces appear:

- authentication, payments, health, financial, or other sensitive data;
- public user-generated content;
- AI or automation able to mutate data, spend money, or perform irreversible acts;
- security, privacy, accessibility, or regulatory claims;
- deployment or migration with material rollback risk.

Random role selection does not satisfy these audits accidentally. Record the
dedicated review_prompt_id and resulting verification obligation.

## Session sizing

| Stakes and scope | Suggested roles per wave | Suggested waves |
|---|---:|---:|
| Small behavior-changing artifact | 2–4 | 1 or saturation |
| Feature or multi-surface change | 4–8 | 1–3 |
| Broad governance or release candidate | 8–18 | 2–4 |
| Security incident follow-up | 6–10 focused roles plus mandatory audits | until acceptance holds |

These are starting bands. Increase or reduce subsequent draws only from evidence:
coverage gaps, new failure mechanisms, duplicated outputs, and acceptance results.

## Integration order

When ordering accepted actions, compare:

1. severity;
2. user-harm and correctness impact;
3. dependency order;
4. reversibility and option value;
5. verification ease when otherwise tied.

Represent blocks and depends-on relationships explicitly when multiple themes
interact.

## Conflict resolution

When reviewers disagree:

1. Prefer reproducible evidence over taste.
2. Prefer user-harm reduction and correctness.
3. Prefer the smallest reversible change that satisfies the Intent Brief.
4. Check whether one proposal violates a constraint or protected invariant.
5. Ask the user only if the remaining choice materially changes direction, safety,
   scope, or acceptance.

Record the resolution and rejected alternative in the theme row.

## Stop rule for reviewer waves

Stop drawing roles when all applicable conditions hold:

- the target coverage set is sufficiently represented;
- the latest wave adds no new viable theme_key;
- new findings repeat existing rows or lack new evidence;
- mandatory audits have findings, verification, or an explicit residual-risk path;
- packet lint and independent acceptance expose no new failure mechanism; and
- remaining proposals fail the Work Filter.

Do not stop because the document is long or continue because more role names are
available. Re-enter the canonical lifecycle after Verify only for new evidence, a
failed criterion, or a new Work Filter-viable theme.

## Acceptance rubric

For each changed or adopted part, evaluate only relevant dimensions:

- intent fidelity and pain-point targeting;
- clarity and usability;
- safety and protected-invariant preservation;
- internal and companion consistency;
- maintainability;
- prompt distinctness and boundary quality;
- trace completeness;
- verification strength; and
- honest residual-risk handling.

A weak dimension cannot be averaged away. If acceptance reveals a new viable
theme, re-enter at Read with the new evidence. If it only restates a rejected or
resolved concern, stop.

## Final response mapping

Report:

- completed theme_keys and user-visible outcome;
- verification actually performed;
- residual risk when material;
- configuration or run instructions when useful; and
- a concise ledger summary when auditability matters.

Do not dump every raw reviewer comment unless the user asks.
