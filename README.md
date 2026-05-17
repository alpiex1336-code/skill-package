# prompt-upgrade skill package

`prompt-upgrade` is a Cursor Agent Skill for intent-based prompt handling, multi-role orchestration, recursive self-review, and evidence-grounded product or document improvement. It is Cursor-first, but the markdown contract is portable as a process document for other agent hosts.

Use it when you want an agent to move beyond a single generic reviewer voice. The skill teaches the assistant to identify the user's intent, choose an appropriate depth, sample multiple composed review roles, merge their findings into actionable `theme_key`s, verify what actually changed, and stop only when the scoped work reaches honest saturation.

## Why try it

- It gives broad requests a repeatable structure: understand the artifact, research weak dimensions, run a Stochastic Role Orchestra, prioritize, implement, verify, self-review, and stop.
- It keeps small requests lightweight. Narrow fixes, small talk, and single-concern changes can use `normal` or a scaled-down path instead of forcing expensive orchestration.
- It makes whole-product or all-aspects improvement explicit. When a prompt signals maximum breadth, the skill pins `thorough`, runs the Deep-upgrade procedural tier, and tracks skipped tools or substitute verification in a ledger.
- It reduces agent drift by requiring evidence, Work Filter adoption, and recursive self-application before non-trivial edits to the skill package itself.

## What is included

- `SKILL.md` - the authoritative contract. If companion files conflict with it, fix `SKILL.md` first.
- `reference-word-banks.md` - Slot A / Slot B / optional Slot C role banks plus P0 / P1 / P2 sampling guidance.
- `reference-depth-domains.md` - domain coverage maps for web, mobile, games, APIs, AI, operations, compliance, and adjacent product classes.
- `reference-workflow-registers.md` - action-register fields, severity, risk-triggered audits, stop rules, and final-response mapping.
- `reference-platforms-extended.md` - optional tool-class/vendor examples; not an endorsement or required checklist.

## Install in Cursor

Clone or copy this repository into your Cursor skills directory so the folder name matches the skill name:

```sh
git clone https://github.com/alpiex1336-code/skill-package.git ~/.cursor/skills/prompt-upgrade
```

If you clone elsewhere, copy or symlink the five skill markdown files into `~/.cursor/skills/prompt-upgrade/`. Keep `SKILL.md` at the folder root; the companion references use relative links.

## How the skill thinks

The skill starts with **improvement mode selection**. If the user's intent makes `normal` or `thorough` identifiable, the agent chooses that mode and proceeds. If the user is making or changing a product and the mode is not identifiable, the agent asks once and waits. This avoids both over-processing tiny tasks and under-processing wide product work.

The core engine is the **Stochastic Role Orchestra**. Instead of pretending to be one universal expert, the agent samples composed labels such as `[accessibility-led][UX researcher]`, `[zero-trust-minded][security champion]`, or `[maintainability-first][SDK maintainer]`. Each pass focuses on a different domain of strength. Raw findings are then merged, deduplicated, and weighted by evidence, severity, independence, and verification ease.

The package uses a **target coverage set** to avoid blind spots. A web app might need layout, accessibility, performance, routing, trust, and deployment coverage; a library might need API contracts, docs, examples, packaging, and error semantics. The word banks provide role variety, while the depth-domain reference helps aim those roles at the right surfaces.

For broad prompts, **Deep-upgrade** adds a procedural floor: cited research where the Snapshot is thin, runtime subagents or simulated substitutes, a wave ledger, P0/P1/complement-bias coverage, quintessence delegation where possible, and verification beyond compile-only when the artifact warrants it. Tool failures are recorded and substituted; disclosure alone is not treated as completion.

For skill-package changes, the same logic turns inward. The agent must read the package, run a meta-orchestra, integrate findings into `theme_key`s, apply the Work Filter, edit only what passes, verify, and stop on clear saturation signals.

## Usage

The skill is designed to be default-on. At the start of a task, read `SKILL.md` and follow its read order. In short:

- If the user makes `normal` identifiable with a small/narrow task, use `normal` or a scaled-down execution path.
- If the user makes `thorough` identifiable with whole-product, all-aspects, or maximum optimization language, use `thorough` and the Deep-upgrade procedural tier.
- If the user is making or changing a product and the mode is not identifiable, ask once and wait.
- For edits to this skill package, run the skill on itself: read, run a meta-orchestra, integrate by `theme_key`, apply the Work Filter, edit, verify, and stop only on clear saturation signals.

## Tool availability

The skill names optional tools such as runtime subagents, MCP servers, browser automation, Lighthouse-class audits, and GitHub-related tools. Those references do not install or grant access to those tools. If a tool is unavailable, omit that Slot C capability, record the substitute path, and continue with available means until the normal stop rules apply.

## Governance and safety

This package is process guidance, not legal, medical, financial, security, or compliance advice. Organizational policy, professional review, and applicable law override these documents. Vendor and product names are examples of tool classes and do not imply endorsement.

## Versioning

Changes to `SKILL.md` wording can change agent behavior. Treat contract-level changes as versioned releases and record them in `CHANGELOG.md`. Companion reference additions that only expand coverage can usually be minor changes.

## License

MIT. See `LICENSE`. The license covers this repository's documentation and examples; it does not license third-party products named as illustrative examples or guarantee rights in outputs produced by separate agent runs.
