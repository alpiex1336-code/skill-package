# Workflow registers, rubrics, and session rules

Companion to `SKILL.md`. Use structured registers so orchestra output **converges** instead of dissolving into chat.

---

## Action register (minimum fields)

Each row is one shippable unit of work after integration.

| Field | Purpose |
|-------|---------|
| `id` | Stable string, e.g. `AUTH-014` |
| `summary` | One line, verb-led |
| `source_roles` | Composed labels that proposed or reinforced it |
| `theme_key` | Hash-map bucket, e.g. `session-security` |
| `severity` | `blocker` / `high` / `medium` / `low` / `chore` |
| `user_visible` | yes / no / mixed |
| `evidence` | Link, repro steps, screenshot note, or “judgment call” stated honestly |
| `verification` | Command, manual flow, or metric |
| `status` | `proposed` / `accepted` / `in_progress` / `done` / `wontfix` |
| `work_filter` | Short note: which clause justified accept or reject |
| `tier_obligation` | Optional for deep-upgrade runs: obligation id (A-F), skipped / substitute / residual-risk note, or `n/a` |

Rejected rows stay in the register as `wontfix` with reason—prevents re-discovery loops.

---

## Severity rubric (suggested)

- **Blocker:** data loss, account takeover, illegal exposure, unshippable crash on primary journey.
- **High:** security weakness without immediate exploit, severe accessibility barrier, broken main monetization path, chronic data corruption risk.
- **Medium:** confusion, moderate perf regression, missing edge state, i18n gap on common locale.
- **Low:** polish, microcopy, minor inconsistency with low confusion cost.
- **Chore:** hygiene (format, dead code) only when it clears real noise or enables other work.

Weight orchestra “votes” by **severity × independence × verification ease**, not by row count.

---

## Coverage set (session axes)

Maintain a **set** of axis ids for the current session. Example universe:

`correctness`, `security`, `privacy`, `perf`, `a11y`, `i18n`, `ux_copy`, `visual`, `motion`, `audio`, `gameplay`, `economy`, `multiplayer`, `ai_safety`, `deploy`, `observability`, `compliance`, `docs`, `dx`

After each orchestra wave, **union** axes touched by findings. Before the next wave, **bias** draws toward `universe - touched` until diminishing returns, then allow aesthetic passes again.

---

## Risk-triggered mandatory audits (non-stochastic, when triggered)

Run explicitly—even if random draws “could” cover them—when these risk surfaces appear. This block is separate from `SKILL.md` **Deep-upgrade procedural tier** A-F; both can apply in one session.

- Auth, payments, or health data present.
- User-generated content public by default.
- AI tools can mutate user data or spend money.
- Regulatory claim in marketing (HIPAA-ready, SOC2, GDPR-compliant).

Label these rows `source_roles: [explicit-audit][security champion]` etc.

---

## Orchestra session sizing

| Stakes | Suggested N (composed roles per wave) | Waves |
|--------|----------------------------------------|--------|
| Trivial single-file fix | 0–2 (optional) | 1 |
| Feature slice | 4–8 | 1–2 |
| Release candidate / launch | 10–18 | 2–4 |
| Security incident follow-up | Focused 6–10 + risk-triggered mandatory audits | Until clean |

N is not a quota cap—raise N when parallel surfaces (client + server + AI + ops) all move.

---

## Integration order (heap keys)

When popping work from a min-heap, compare tuples in order:

1. `severity` (blocker first)
2. `user_visible` blockers before invisible unless invisible unblocks visible
3. `verification` ease (cheap proof first when tied)
4. `dependency_in_degree` from graph of tasks (zero first)

---

## Conflict resolution

When two roles disagree:

1. Prefer **reproducible evidence** over taste.
2. If still tied, prefer **user harm reduction** and **correctness**.
3. If still tied, **smallest reversible change** that preserves option value.
4. If still tied, escalate to the user with **two labeled options**, not a vague question.

---

## Stop rule for orchestra waves

Stop sampling new roles when:

- Coverage set is saturated **or**
- Last wave added no new `theme_key` entries **or**
- New findings are rephrasings of existing rows (Bloom-metaphor: likely duplicates).

Do not stop solely because “we already wrote a lot”—stop on **evidence of saturation**. For deep-upgrade runs, skipped tier obligations and substitute verification remain in the register until resolved, marked `wontfix` with Work Filter rationale, or carried into the terminal residual-risk summary; disclosure alone is not a stop signal.

**Same stop logic for meta-work:** when the artifact under review **is this skill** (or companion markdown), extra meta-orchestra waves are justified only while they surface **new theme_keys**, **uncovered governance**, or **contradictions**. Otherwise you are rephrasing the same critique—stop. For **how** a user’s skill-change request becomes edits, see `SKILL.md` **Skill-targeting change requests (default behavior)**: **operationalize** first, then run the same merge/stop pattern—**not** a standing rule to copy the last user message into the contract unless a **Literal wording lock** applies.

---

## Example register fragment (markdown)

```markdown
| id | summary | source_roles | theme_key | severity | user_visible | verification | status |
|----|---------|--------------|-----------|----------|--------------|--------------|--------|
| AUTH-014 | Rotate session cookie on privilege change | `[adversarial][security champion]` | session-security | high | mixed | integration test + manual login | accepted |
| UI-022 | Empty state for zero notifications | `[modern-UX-led][UX researcher]` | empty-states | medium | yes | visual + screen reader | proposed |
```

---

## Right-path reminder

Registers exist to **reduce rework**, not to bureaucratize. If a field does not help prioritize or verify, drop it for the session.

---

## Final response mapping

Map closing user message to register subset:

- `done` + verification notes
- `accepted` not yet `done` → backlog handoff
- `wontfix` with reasons only if user cares about rejected ideas
