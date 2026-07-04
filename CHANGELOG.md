# Changelog

All notable changes to this skill package should be documented here.

## 1.2.0 - 2026-07-04

### Added

- **Slot D — installed Agent Skills** — optional fourth composed-role slot for installed, fully-read Cursor Agent Skills that can guide a pass without becoming a second controller.
- **Skill guideline requirement** — before attaching Slot D, agents must read the full skill file and record `use for` / `when to use` guidance.
- **Independent acceptance scoring loop** — non-trivial skill-package edits and thorough/deep-upgrade work now use a fresh evaluator and a `>=90/100` per-dimension target, bounded by Work Filter and saturation stop rules.
- **External roster governance** — external role rosters are vocabulary mines, not execution checklists; useful entries become deduped Slot A/B tokens.

### Changed

- Strengthened runtime prompt packets with purpose, capability boundary, Snapshot context, relevant skill instructions, evidence hooks, output contract, and Slot D guidelines when applicable.
- Split optional capabilities clearly: **Slot C** for tools/MCP/plugins/hooks, **Slot D** for installed skill instruction packages.
- Expanded `reference-word-banks.md` with Laravel/Livewire/Filament admin, smart-contract, codebase-onboarding, and agentic-optimization coverage tokens.
- Updated stop-rule guidance so low scores trigger another subagent process only when a new Work Filter-passing `theme_key` appears.

## 1.1.0 - 2026-05-23

### Added

- **NON-NEGOTIABLE EXECUTION GATES** — pass/fail checkpoints (Gate 0–4 + blocking checklist) placed before Improvement mode so agents cannot skip orchestra and jump to Implement.
- **PRE-FLIGHT** — mandatory gate block before any in-scope artifact file write.
- **Common agent failure modes (hard stops)** — five named drift patterns (single-voice collapse, skill-as-flavor-text, simulated-only when Task available, missing wave ledger, implement-before-orchestrate) with self-check questions.
- **Anti-patterns** — named **single-voice collapse under delivery pressure** with recovery protocol.
- **Pre-implementation gate** — explicit DO NOT enter Implement until orchestra, quintessence, and in-session ledger are complete.
- **`reference-execution-gates.md`** — operational companion: Task launch patterns, minimum N by mode, wave ledger template, Gate 3 delegation, simulated-fallback honesty script.
- **Lexicon** entries: **Execution gate**, **Simulated fallback (execution sense)**.

### Changed

- YAML `description` leads with **execution gate**, **composed role label**, and **wave ledger** for agent discovery.
- **Read order (cold start)** — gates and PRE-FLIGHT before Lexicon.
- **Deep-upgrade tier B/C** — Task must be invoked when available; wave ledger must start in-session, not only in the final reply.
- **Strict runtime enforcement** — **Runtime-first probe** before Orchestrate.
- **Workflow §5 Implement** — requires `Orchestra gate: PASS | FAIL` self-audit; links to Gates 2–3.
- **Trigger phrases** — rows for default-on, “execute all processes”, multi-agent, build/implement routing.
- **Autonomy** — first product file write requires PRE-FLIGHT + Gate checklist pass.
- Terminology tightened to Lexicon spellings: **runtime subagent**, **Orchestra wave**, **Quintessence row**, **integrate → adopt**, **in-scope artifact file write**.

## 0.1.0 - 2026-05-17

- Initial public package layout for `prompt-upgrade`.
- Included the authoritative `SKILL.md` contract and four companion references.
- Added repository README, MIT license, contribution guidance, security policy, code of conduct, and git ignore rules.
- Clarified mode selection, Deep-upgrade procedural tier recursion, and ledger-backed stop signals before packaging.
