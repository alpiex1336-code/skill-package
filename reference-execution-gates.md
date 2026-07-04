# Execution gates — operational reference

Companion to `SKILL.md` **NON-NEGOTIABLE EXECUTION GATES**. Load this file when **passing Gate 1 or Gate 3**—not when deciding *whether* to delegate (that is inline in `SKILL.md`).

---

## When to open this file

- Starting **Orchestrate (Review)** and you need concrete Task launch patterns
- Starting **Implement** and you need per-`theme_key` delegation templates
- Writing the **in-session wave ledger**
- Documenting **simulated fallback** honestly

---

## Gate 1 — Orchestra wave recipes

### Runtime-first probe (start of every product pass)

```
1. Is Cursor Task tool (or equivalent delegation) available in this environment?
   YES → proceed to parallel launches below
   NO  → ledger: runtime_subagents: unavailable (<reason>)
         → run simulated passes with SAME composed labels + fresh-agent rules
```

### Minimum N by mode

| Mode / scope | Min composed labels | Min runtime subagents (when Task exists) | Waves |
|--------------|---------------------|------------------------------------------|-------|
| Trivial single-step | 0 (orchestra optional) | 0 | 0 |
| Single-axis narrow | 1–2 | 1 if product-changing | 1 |
| Normal product pass | 2–4 | ≥1 | 1 |
| Thorough / deep-upgrade | 4–8+ | ≥2 parallel on first wave | 1–3+ |
| Greenfield + thorough | 4+ (feature slice band) | ≥1 before first product file | 1+ |

See [reference-workflow-registers.md](reference-workflow-registers.md) *Orchestra session sizing* for stakes bands.

### Parallel Task launch pattern

Launch **independent** subagents in **one parent message** (parallel tool calls). Each prompt **must** include:

1. **Composed label** as persona: `[Slot A][Slot B]`
2. **Purpose / why launched** — what this pass should protect or discover
3. **Capability boundary** — the aspect class or domain of strength to stress
4. **Snapshot context packet** — artifact, relevant files / URLs / excerpts, mode, constraints, known unknowns
5. **Relevant skill instructions** — gates, Work Filter, companion references, domain notes, and Slot D skill guideline(s) that apply to this pass
6. **Evidence hooks** — facts, checks, routes, standards, or snippets the subagent should anchor to
7. **Output contract** — tagged bullets only; bounded findings; no implementation unless asked
8. **Return** — findings + `theme_key` suggestions + verification gaps

**Example prompt skeleton:**

```markdown
You are [privacy-first, offline-advocate][security champion] reviewing <artifact>.

MODE: thorough | SCOPE: <one line>
Purpose: find privacy / local-data risks before integration.
Capability boundary: stress ONLY local data handling, API key storage, OCR privacy.

Snapshot context:
- Artifact / files: <paths or pasted excerpt summary>
- Constraints: <user constraints, north-star invariant, non-goals>
- Known unknowns: <what is not in context>

Relevant skill instructions:
- Use Work Filter; propose only non-redundant, scoped findings.
- Do not implement; this is Gate 1 review input.
- If Slot D is attached, include the read-derived skill guideline (`use for` + `when to use`) and do not rely on unread skills.

Evidence hooks:
- Cite exact observed file/section, command output, screenshot, or missing evidence.

Return:
- 3–8 numbered findings tagged [privacy-first, offline-advocate][security champion]
- Suggested theme_keys for integration
- Verification gaps or checks that would confirm/reject the finding
- Do NOT implement; do NOT merge other roles' views
```

### Subagent type routing (Cursor Task tool)

| Need | subagent_type |
|------|----------------|
| Codebase search, file patterns | `explore` |
| Shell, build, git, CI | `shell` |
| General review, multi-file reasoning | `generalPurpose` |
| Skill package / governance edits | `generalPurpose` with meta-orchestra label |

---

## Gate 2 — Integration checklist

Before any in-scope artifact file write:

- [ ] Raw subagent outputs collected with composed labels visible
- [ ] Findings merged into **`theme_key`** rows (hash-map dedup)
- [ ] Conflicts between roles explicitly resolved
- [ ] Work Filter applied — most raw findings **rejected**
- [ ] Action register has ≥1 row with `status: accepted` **or** honest zero-adopt stop documented

---

## Gate 3 — Implement delegation

**Forbidden pattern:** Review subagents run → parent implements everything inline.

**Required pattern:** One runtime subagent per **accepted** `theme_key` (batch only with ledger disclosure).

### Per-theme prompt skeleton

Each Gate 3 prompt implements **one accepted `theme_key`** unless batching is explicitly recorded in the ledger. Prompts must include purpose, context packet, role capability, relevant skill instructions, constraints, evidence hooks, verification expectation, and a strict **no-cross-theme / no-synthesis** boundary.

```markdown
You are [implementation-focused][<stance matching theme>] implementing ONE theme only.

theme_key: <id>
Accepted action: <one line from register>
Purpose: implement the accepted row because <why this row passed Work Filter>.
Role capability: <why this stance is suited to this row; one domain boundary>

Snapshot context:
- Artifact / files: <paths, snippets, current behavior, relevant constraints>
- Prior accepted evidence: <role findings or references that justified this row>
- Known unknowns: <what not to assume>

Relevant skill instructions:
- Preserve Work Filter, north-star invariant, Snapshot honesty.
- Apply only Gate 3 for this theme; do not re-run synthesis.
- If Slot D is attached, include the read-derived skill guideline and apply it only within this accepted `theme_key`.

Constraints:
- Minimal scoped diff; match repo/document conventions.
- North-star invariant: <line>
- No unrelated files; no new doctrine section unless accepted action requires it.

Evidence hooks:
- Re-read changed areas; preserve named vocabulary and anchors.
- Verification expectation: <command, static read, link check, or manual review>

Boundaries:
- Implement ONLY this theme_key.
- Do NOT merge other theme_keys.
- Do NOT synthesize new governance direction; if you find a new theme, report it as a proposed follow-up instead of editing it.

Return:
- Files changed
- Summary of exact edits
- Verification run / not run
- Gaps, residual risk, or proposed new theme_key if discovered
```

### Batching rules

Batch multiple `theme_key`s in one subagent **only when**:

- Changes are tightly coupled (same file, same dependency chain)
- Ledger records: `gate3_batch: [theme_a, theme_b] — reason: <dependency>`

---

## Gate 4 — Wave ledger template

Start this block **in the first reply that completes orchestra**—append each wave. **Do not defer to final reply only.**

```markdown
## Wave ledger

### wave_1
- **sampled_labels:** `[lens][stance]`, `[lens][stance]`, …
- **runtime:** Task × N | simulated (reason: …)
- **theme_keys merged:** `theme-a`, `theme-b`
- **adopted:** `theme-a` (why); `theme-b` (rejected — churn)
- **verification:** (pending | command/run | not run — why)
- **skipped/substitute:** tier B runtime if applicable

### wave_2
…
```

---

## Simulated fallback — honesty script

Use **only** when Task/delegation is unavailable or blocked:

```markdown
**Runtime honesty:** Task tool unavailable (<reason: e.g. user rule forbids Task, environment error>).
**Substitute:** Simulated fresh-agent passes for labels: [list].
**Same discipline:** bounded tagged outputs → integrate → adopt.
**Residual risk:** No independent process isolation; findings may correlate more than runtime subagents.
```

**Never** use simulated fallback when Task ran successfully for other work in the same session but orchestra was skipped for convenience.

---

## Anti-patterns (operational)

| Anti-pattern | Fix |
|--------------|-----|
| Read skill → TodoWrite(implement) → Write files | Stop; PRE-FLIGHT; Gate 1 Orchestra wave |
| “I'll mention orchestra in the **wave ledger** summary only” | **Wave ledger** row before first in-scope artifact edit |
| One subagent, no **composed role label** | Add `[Slot A][Slot B]` to prompt; relaunch |
| Parent plays all roles in one paragraph | Parallel **Task tool** launches with distinct labels |
| **Review (skill sense)** only → parent **Implement** inline | Gate 3: one runtime subagent per Work Filter–accepted **Quintessence row** |
| Thorough user request treated as “style preference” | Pin thorough + Gate checklist |

---

## PRE-FLIGHT quick copy

```
PRE-FLIGHT — product work gate
1. SCOPE: … | North-star: …
2. MODE: normal | thorough
3. COVERAGE: [aspect classes] | P0: …
4. ORCHESTRA: N=… labels planned | Task: Y/N
5. ORDER: integrate → adopt before implement
6. LEDGER: wave_1 reserved
7. FILTER: no implement todos pre-adopt
GATE: PASS | FAIL
```

---

## Skill-targeting (meta) work

Edits to `SKILL.md` and `reference-*.md` use the **same gates**:

- **Gate 1:** meta-orchestra with ≥2 orthogonal labels (e.g. `[execution-contract-enforcer][process auditor]`, `[information-architect][taxonomy writer]`)
- **Gate 2:** integrate meta-findings into `theme_key` rows before line edits
- **Gate 4:** wave ledger in reply documenting what changed and why

Trivial typo fixes may scale down PRE-FLIGHT with one-line disclosure.
