# Zero-skip compliance — operational reference

Load when: **complete skill compliance** is triggered; **`improvement_mode` = thorough** is pinned; **deep-upgrade intent**; governance or meta-review of this skill package; any suspicion of gate evasion.

Companion to `SKILL.md` **NON-NEGOTIABLE EXECUTION GATES** and [reference-execution-gates.md](reference-execution-gates.md).

---

## Pinned execution path (non-reorderable)

**Gate IDs ≠ chronological order:** ledger-start (Gate 4 row) precedes first implement writes (Gate 3 delegates).

1. Read `SKILL.md` in order + this file + `reference-execution-gates.md`
2. **PRE-FLIGHT** (all items) → declare `GATE: PASS` or `GATE: FAIL`
3. **Gate 1:** ≥2 runtime Task subagents in parallel (or ledger-documented simulated with same N and composed labels)
4. **Gate 2:** integrate → adopt → ≥1 accepted **`theme_key`** (Work Filter)
5. **Gate 4:** wave ledger row **in the session** before first in-scope artifact write
6. **Gate 3:** one runtime subagent per accepted **`theme_key`** when Task exists (parent orchestrates; parent does not implement themes inline)
7. **Verify** + **Self-review** + terminal ledger update

**Do not reorder.** Work Filter efficiency, urgency, or “minimal diff” **does not** waive a step when thorough or complete-compliance is pinned.

---

## Pre-write tool guard

**Forbidden before steps 3–5 complete:**

- `Write`, `StrReplace`, `EditNotebook` on in-scope artifacts
- Destructive shell mutations on product or skill-package files
- `TodoWrite` entries that imply implement before adopt

**Allowed before orchestra:** Read, Grep, SemanticSearch, Shell read-only, Task launches, user-facing PRE-FLIGHT / ledger text.

---

## Violation detectors (hard stop)

| Detector | Action |
|----------|--------|
| First artifact write with zero `[Slot A][Slot B]` tagged findings | **HALT** → Wave 1 |
| Task available, zero Task invocations, thorough / complete-compliance active | **HALT** → runtime orchestra |
| Ledger first appears only in final reply | **HALT** → rebuild in-session ledger |
| Parent `Write`/`StrReplace` on all adopted themes without Gate 3 delegate | **HALT** → delegate per `theme_key` |
| User pinned “follow skill completely” but Gate 0 scale-down used | **HALT** → pin thorough, close escapes |

---

## Violation recovery script

```
HALT — contract violation: <rule ids from Common agent failure modes>
PRE-FLIGHT: GATE FAIL — <which items>
Next: Wave 1 runtime orchestra (≥2 labels) → integrate → adopt → ledger row 1 in reply
Gate 3: one delegate per accepted theme_key
Resume writes only after: Orchestra gate: PASS
```

Do **not** “fix forward” without recovery and ledger disclosure.

---

## Parent vs subagent parity

| Parent may | Parent may not (when Task exists) |
|------------|-----------------------------------|
| PRE-FLIGHT, coverage, mode pin | First implement write on in-scope artifacts |
| Launch Task / subagents | Play all roles in one voice |
| Integrate, adopt, ledger | Implement every adopted theme inline |
| Verify, self-review, honest gaps | Claim thorough complete with zero Task calls |

---

## Complete-compliance checklist (blocking)

- [ ] **`improvement_mode` = thorough** pinned (unless user **explicitly** named `normal`)
- [ ] **Gate 0** closed (no trivial / single-axis escape unless explicit)
- [ ] **PRE-FLIGHT** 1–8 satisfied
- [ ] **Wave 1** runtime (or documented simulated substitute)
- [ ] **≥1** adopted **`theme_key`**
- [ ] **Ledger** visible in-session before first write
- [ ] **Gate 3** plan or execution per adopted row
- [ ] **`Orchestra gate: PASS`** line before first write (or honest FAIL + recovery)

---

## Orchestra gate self-audit (one line)

Emit before first in-scope write:

`Orchestra gate: PASS | FAIL — waves=<n>, labels=<n>, ledger=<location>, Task=<used|blocked>, themes_adopted=<list>`

If **FAIL**, do not write artifacts until recovery completes.
