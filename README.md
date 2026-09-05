# Deep-Harness skill package

Deep-Harness is a Codex skill for rigorous, multi-role improvement work and
AI-agent harness engineering. It turns a substantive improvement request into
one traceable lifecycle:

```text
Read
→ Intent analysis and clarification
→ Review Prompt Compiler
→ Multi-role review
→ Integrate
→ Work Filter
→ Edit Prompt Compiler
→ Edit
→ Verify
```

## When it activates

Deep-Harness is available through normal skill discovery, but it is intentionally
not a default workflow for every task. It applies when the user:

- explicitly invokes `$deep-harness` or names Deep-Harness;
- asks to substantively improve, optimize, refine, or harden an existing artifact;
- explicitly requests deep, rigorous, multi-angle, multi-role, or orchestrated reasoning; or
- designs, evaluates, or improves an AI-agent harness.

Routine feature creation, factual lookup, ordinary edits, generic code review,
incidental phrases such as “deep learning,” and ordinary software test harnesses
do not activate it by themselves.

## What the skill provides

- Evidence-bounded Intent Briefs that separate facts, hypotheses, assumptions,
  unknowns, and direction-changing questions.
- AI-authored, linted Review Prompt Packets for distinct runtime roles.
- Integration and Work Filter convergence into traceable `theme_key` actions.
- AI-authored Edit Prompt Packets aimed at the demonstrated pain point.
- Runtime-first delegated implementation, pre-edit ledgers, independent
  acceptance verification, honest residual-risk reporting, and saturation stops.

## Package contents

- `SKILL.md` — the governing contract.
- `reference-execution-gates.md` — operational gate, prompt-packet, ledger,
  delegation, verification, and recovery templates.
- `reference-word-banks.md` — composed-role vocabulary and coverage guidance.
- `reference-depth-domains.md` — domain coverage and failure-mode maps.
- `reference-workflow-registers.md` — trace, action, severity, conflict, and
  stopping registers.
- `reference-platforms-extended.md` — optional platform and tool-class examples.

## Install or update in Codex

The GitHub repository keeps its historical repository name, `skill-package`,
while the installed skill name is `deep-harness`.

```sh
git clone git@github.com:alpiex1336-code/skill-package.git ~/.codex/skills/deep-harness
```

For an existing checkout:

```sh
cd ~/.codex/skills/deep-harness
git pull origin main
```

If this Codex installation uses the personal agent-skill directory instead,
place the same folder at `~/.agents/skills/deep-harness/`. Keep `SKILL.md` at
the folder root and keep the companion references beside it so relative links
continue to resolve.

After installation, reload or restart Codex if the skill catalog does not show
`deep-harness` immediately.

## Verification

Validate the package with Codex’s bundled skill validator:

```sh
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

The validator checks the frontmatter, skill name, and package structure. Also
confirm that local Markdown links resolve and that no old `prompt-upgrade`
identity remains in active package files.

## License

MIT. See `LICENSE`. Product, vendor, and tool names in the references are
illustrative and do not grant access or rights to their services or outputs.
