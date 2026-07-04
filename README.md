# prompt-upgrade skill package

`prompt-upgrade` is a Cursor Agent Skill for intent-based prompt handling, multi-role orchestration, recursive self-review, and evidence-grounded product or document improvement. It is Cursor-first, but the markdown contract is portable as a process document for other agent hosts.

**Latest release:** [v1.2.0](https://github.com/alpiex1336-code/skill-package/releases/tag/v1.2.0) — adds Slot D for installed Agent Skills, strengthens prompt packets, and expands honest stop / scoring governance.

Use it when you want an agent to move beyond a single generic reviewer voice. The skill teaches the assistant to identify the user's intent, choose an appropriate depth, sample multiple composed review roles, merge their findings into actionable `theme_key`s, verify what actually changed, and stop only when the scoped work reaches honest saturation.

## Why try it

- It gives broad requests a repeatable structure: understand the artifact, research weak dimensions, run a Stochastic Role Orchestra, prioritize, implement, verify, self-review, and stop.
- It keeps small requests lightweight. Narrow fixes, small talk, and single-concern changes can use `normal` or a scaled-down path instead of forcing expensive orchestration.
- It makes whole-product or all-aspects improvement explicit. When a prompt signals maximum breadth, the skill pins `thorough`, runs the Deep-upgrade procedural tier, and tracks skipped tools or substitute verification in a ledger.
- **v1.1+:** It blocks the common agent failure mode of reading the skill then implementing solo—**Execution gates**, **PRE-FLIGHT**, and **in-session wave ledger** requirements are contract-level, not optional philosophy.
- **v1.2+:** It separates optional capabilities into Slot C for tools/MCP/plugins and Slot D for installed, fully-read Agent Skills that provide extra task guidance without overriding `prompt-upgrade`.

## What is included

- `SKILL.md` - the authoritative contract. If companion files conflict with it, fix `SKILL.md` first.
- `reference-execution-gates.md` - **Task tool patterns**, gate checklists, wave ledger templates, simulated-fallback scripts (load when passing Gate 1 or Gate 3).
- `reference-word-banks.md` - Slot A / Slot B / optional Slot C tool surfaces / optional Slot D installed-skill guidance plus P0 / P1 / P2 sampling guidance.
- `reference-depth-domains.md` - domain coverage maps for web, mobile, games, APIs, AI, operations, compliance, and adjacent product classes.
- `reference-workflow-registers.md` - action-register fields, severity, risk-triggered audits, stop rules, and final-response mapping.
- `reference-platforms-extended.md` - optional tool-class/vendor examples; not an endorsement or required checklist.

## Install in Cursor

Clone or copy this repository into your Cursor skills directory so the folder name matches the skill name:

```sh
git clone https://github.com/alpiex1336-code/skill-package.git ~/.cursor/skills/prompt-upgrade
```

If you use SSH keys with GitHub:

```sh
git clone git@github.com:alpiex1336-code/skill-package.git ~/.cursor/skills/prompt-upgrade
```

If you clone elsewhere, copy or symlink the six skill markdown files into `~/.cursor/skills/prompt-upgrade/`. Keep `SKILL.md` at the folder root; the companion references use relative links.

To update an existing install:

```sh
cd ~/.cursor/skills/prompt-upgrade
git pull origin main
# or copy the six .md files from a fresh clone
```

## Execution gates (v1.1+)

Before any **Implement**-phase artifact write, agents must pass **NON-NEGOTIABLE EXECUTION GATES** in `SKILL.md`:

| Gate | Requirement |
|------|-------------|
| **0** | Skip orchestration only for trivial single-step or single-axis narrow scope |
| **1** | **Orchestra wave** with **≥2 composed role labels**; **runtime subagents** via Task tool when available |
| **2** | **integrate → adopt** (Work Filter) into **Quintessence row**s before edits |
| **3** | Prefer one runtime subagent per adopted theme at Implement |
| **4** | **Wave ledger** started in-session—not deferred to the final reply |

Complete **PRE-FLIGHT** (same file) before the first file write. Operational templates live in `reference-execution-gates.md`.

## How the skill thinks

The skill starts with **improvement mode selection**. If the user's intent makes `normal` or `thorough` identifiable, the agent chooses that mode and proceeds. If the user is making or changing a product and the mode is not identifiable, the agent asks once and waits. This avoids both over-processing tiny tasks and under-processing wide product work.

The core engine is the **Stochastic Role Orchestra**. Instead of pretending to be one universal expert, the agent samples composed labels such as `[accessibility-led][UX researcher]`, `[zero-trust-minded][security champion]`, or `[maintainability-first][SDK maintainer]`. Each pass focuses on a different domain of strength. Raw findings are then merged, deduplicated, and weighted by evidence, severity, independence, and verification ease.

The package uses a **target coverage set** to avoid blind spots. A web app might need layout, accessibility, performance, routing, trust, and deployment coverage; a library might need API contracts, docs, examples, packaging, and error semantics. The word banks provide role variety, while the depth-domain reference helps aim those roles at the right surfaces.

For broad prompts, **Deep-upgrade** adds a procedural floor: cited research where the Snapshot is thin, runtime subagents or simulated substitutes, a wave ledger, P0/P1/complement-bias coverage, quintessence delegation where possible, and verification beyond compile-only when the artifact warrants it. Tool failures are recorded and substituted; disclosure alone is not treated as completion.

For skill-package changes, the same logic turns inward. The agent must read the package, run a meta-orchestra, integrate findings into `theme_key`s, apply the Work Filter, edit only what passes, verify, and stop on clear saturation signals.

## Brief workflow

This section is the onboarding summary. The authoritative macro sequence and stop rules live in [`SKILL.md`](SKILL.md) (**Workflow**, steps 1–8). **Read NON-NEGOTIABLE EXECUTION GATES first** on cold start.

Every engagement follows the same macro sequence:

1. **Understand** — Choose `improvement_mode` (`normal` vs `thorough`), read the artifact in scope, define success criteria and the north-star invariant, and build a target coverage set so later passes stay aimed, not random.
2. **Research** — When the Snapshot is thin, fill gaps with cited standards, docs, and public patterns (not invented context).
3. **Orchestrate** — Pass **Gate 1**: run Stochastic Role Orchestra waves with **runtime subagents** when Task is available; merge into `theme_key` rows; adopt via Work Filter (**Gate 2**).
4. **Prioritize** — Order work by severity and dependency (blockers and trust risks first), using the action register in `reference-workflow-registers.md`.
5. **Implement** — **Gates 2–3**: ship Quintessence rows only; delegate per theme when tooling allows; self-audit `Orchestra gate: PASS | FAIL` before first edit.
6. **Verify** — Run project-standard checks when available; record verification in **wave ledger** (**Gate 4**).
7. **Self-review** — Re-read changes and challenge prior conclusions; add another orchestra wave only when it could surface a distinct failure mode.
8. **Stop** — End when verification holds and further waves would repeat the same themes; close decisively without filler prompts.

**Mode scales depth:** `normal` keeps waves short and changes localized inside the current product shape; `thorough` authorizes broader reshaping (UI, performance, structure) while preserving the north-star invariant. If the user is making or changing a product and mode is unclear, the agent asks once before heavy orchestration.

## Usage

The skill is **default-on**: read **NON-NEGOTIABLE EXECUTION GATES** and **Read order (cold start)** in `SKILL.md` on first use.

- **Product work:** complete **PRE-FLIGHT**, pass Gates 1–4, then follow the eight-step workflow; scale depth with `normal` vs `thorough`.
- **Edits to this package:** run recursive self-application—same gates apply before line edits (see **Recursive self-application** in `SKILL.md`).

## Tool and skill availability

The skill names optional tools such as runtime subagents (Cursor **Task** tool), MCP servers, browser automation, Lighthouse-class audits, and GitHub-related tools. It can also name optional installed Agent Skills via Slot D after their full `SKILL.md` has been read and summarized into a short `use for` / `when to use` guideline. Those references do not install or grant access. If Task is unavailable, use **Simulated fallback** and record why in the wave ledger—never skip both runtime and simulated orchestra.

## Governance and safety

This package is process guidance, not legal, medical, financial, security, or compliance advice. Organizational policy, professional review, and applicable law override these documents. Vendor and product names are examples of tool classes and do not imply endorsement.

## Versioning

Changes to `SKILL.md` wording can change agent behavior. Treat contract-level changes as versioned releases and record them in `CHANGELOG.md`. Companion reference additions that only expand coverage can usually be minor changes.

| Version | Summary |
|---------|---------|
| **1.2.0** | Slot D installed-skill guidance, read-before-use rules, prompt packet strengthening, scoring loop governance |
| **1.1.0** | Execution gates, PRE-FLIGHT, failure-mode hard stops, `reference-execution-gates.md` |
| **1.0.0** | Initial stable public package |
| **0.1.0** | First public layout |

## License

MIT. See `LICENSE`. The license covers this repository's documentation and examples; it does not license third-party products named as illustrative examples or guarantee rights in outputs produced by separate agent runs.
