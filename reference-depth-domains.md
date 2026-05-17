# Depth domains — orchestra coverage map

Use this file when sampling roles or biasing coverage: each section lists **failure modes** and **review surfaces**. Pair with [reference-word-banks.md](reference-word-banks.md) for composed labels.

---

## Web applications (document, SPA, SSR)

**Routing and navigation**

- Deep links survive refresh; back button does not trap; guarded routes match server authorization.
- 404 and soft-404 behavior; canonical URLs; trailing slash policy consistent.
- History state does not leak sensitive data in URLs.

**Forms and input**

- Client validation mirrored server-side; field-level errors accessible to assistive tech.
- Autocomplete attributes sensible; password managers not broken by anti-patterns.
- File uploads: size limits, type validation, virus scanning policy if applicable, storage URLs not guessable.

**Performance**

- Critical CSS or equivalent; font loading strategy (swap, optional); subset fonts where possible.
- Image `srcset`, modern formats, lazy loading where safe; LCP element not delayed by JS.
- Third-party scripts gated; consent where required.

**Security (browser-facing)**

- CSP, XSS sinks, JSON injection in HTML; postMessage origin checks; `rel=noopener` on external links.
- Cookies: `Secure`, `HttpOnly`, `SameSite`; CSRF tokens on mutating routes.
- Subresource integrity where CDN assets are pinned.

**PWA / installable**

- Service worker update strategy; offline queue conflict resolution; cache versioning.

---

## Mobile apps (native and cross-platform)

**Lifecycle**

- Cold start vs warm start; state restoration after process death; background task limits.

**Platform conventions**

- iOS Human Interface Guidelines alignment where custom; Android Material or deliberate deviation documented.
- Safe areas, notches, dynamic island, foldables; keyboard overlap on forms.

**Permissions**

- Pre-permission rationale copy; degraded mode when denied; re-request paths.

**Distribution**

- Store listing truth; screenshot accuracy; privacy nutrition labels match behavior.

**Networking**

- Certificate pinning tradeoffs; retry storms; airplane mode UX.

---

## Games (real-time, narrative, economy)

**Clarity**

- Objective readable in 5 seconds; next recommended action obvious without wiki.

**Feedback loop**

- Input latency vs tick rate; buffer windows fair and documented in feel, not only in code.
- Hitboxes vs hurtboxes; i-frames readable; damage numbers optional clutter audit.

**Economy and progression**

- Sources and sinks; inflation; pity systems; duplicate reward frustration.
- Pay-to-win perception vs reality; cosmetic-only claims verifiable.

**Multiplayer**

- Desync handling; reconnect; griefing vectors; chat moderation hooks.

**Narrative**

- Branching state machine testable; localization length overflow on dialogue UI.

**Audio**

- Mix buses: music duck under VO; combat readability; mono compatibility.

---

## Backend and APIs

**Contracts**

- OpenAPI or equivalent truth matches implementation; breaking change policy.

**Validation**

- Schema at boundary; coercion rules explicit; rejection messages safe (no stack traces to clients).

**AuthZ**

- Object-level permissions; IDOR tests; admin impersonation audited.

**Idempotency**

- Retries safe for POST where required; idempotency keys documented.

**Rate limiting**

- Fair limits; backoff hints; abuse differentiation from viral success.

**Migrations**

- Expand-contract pattern; backfill jobs; rollback story.

---

## Data stores and consistency

**Transactions**

- Isolation level justified; deadlock retries; long transactions avoided.

**Indexes**

- Query plans for hot paths; partial indexes where applicable.

**Caches**

- TTL vs explicit invalidation; stampede protection; cache key versioning.

**Search**

- Relevance tuning; synonym maps; PII in index audit.

---

## AI and agentic features

**Grounding**

- Citations or abstain when facts matter; confidence surfaced when user must decide.

**Tools**

- Schema strict; timeouts; partial failure; human-in-the-loop for irreversible tools.

**Prompt injection**

- Untrusted document in RAG; email body driving tools; delimiter discipline.

**Evals**

- Golden sets versioned; regression on model swap; non-flaky assertions.

**Cost**

- Token budgets per user tier; streaming vs batch; cache embeddings where licensed.

---

## Observability and operations

**Logs**

- Structured fields; correlation IDs; PII scrubbing; sampling under load.

**Metrics**

- RED/USE as appropriate; SLOs with error budgets; alert fatigue review.

**Tracing**

- Critical path spans; propagation into async workers.

**Runbooks**

- On-call steps; escalation; customer comms templates.

---

## Compliance and trust (sector-agnostic strip)

- Data inventory: what is collected, why, retention, deletion.
- subprocessors listed if claimed; region-specific behavior (EU, US state laws) when product says it cares.
- Accessibility conformance statement honest to tested scope.
- Children: age gates, parental controls, COPPA-style caution when relevant.

---

## Content, editorial, and growth

- Editorial calendar vs code deploy coupling; stale CMS content in app.
- SEO: titles, meta, structured data honest; no cloaking.
- Email/push: unsubscribe one-click; frequency caps; quiet hours optional.

---

## Design systems and tokens

- Single source of truth for color, type, spacing; generated artifacts stay in sync.
- Deprecated tokens migration path; no zombie components in public docs.

---

## Internationalization and locales

- Pseudolocale QA; string freeze process; ICU message format correctness.
- Plural, gender, ordinals where grammar demands; do not concatenate translated fragments blindly.
- RTL mirroring of icons and gestures; number and currency formatting on server and client agreement.

---

## Accessibility (cross-cutting)

- Focus order matches visual order; skip links; landmark regions.
- Live regions for async updates; polite vs assertive.
- Touch target 44px class targets where platform allows; focus visible.
- Charts: data table alternative or accessible description.

---

## Supply chain and dependencies

- Lockfile policy; renovate/dependabot noise vs security.
- License compatibility for bundled deps; optional native addon risk.

---

## Incident readiness

- Feature flags kill switch; config-only rollback; database backward compatibility one version.

---

## Real-time collaboration (docs, whiteboards, co-editing)

- **Conflict algorithms:** CRDT vs OT; undo/redo across peers; cursor presence not leaking private doc titles.
- **Permissions:** share link scope; guest vs member; comment-only vs edit.
- **Export:** lossless export; version history retention promises match storage.

---

## Email, notifications, and deliverability

- SPF/DKIM/DMARC alignment when product sends mail; bounce handling; unsubscribe and preference center truth.
- Push: permission prompts justified; quiet hours; dedupe notifications across devices.

---

## CRM, sales, and support stacks

- Lead PII minimization; pipeline stage definitions stable; automation not creating duplicate contacts.
- Support ticket ↔ engineering link; SLA fields honest in UI.

---

## Browser extensions and plugins

- Minimal host permissions; content script isolation; update channel security; store listing matches manifest.

---

## Cryptographic and wallet-adjacent surfaces (high risk)

- Never roll custom crypto for production secrets; use vetted libraries and parameters.
- Seed phrases, private keys: clear UX that they are secret; clipboard clearing policy; screenshot warnings.
- Chain IDs and address checksums; human-readable confirmations before irreversible sends.

---

## Machine learning training pipelines (when product trains models)

- Data consent lineage; leakage from validation into train; reproducible splits.
- Model cards honest to eval scope; drift monitoring in production.

---

## How to use this file in the orchestra

1. Before a large pass, **hash-map** product type → relevant sections above (not every section every time).
2. Build a **set** of section ids not yet covered; sample roles biased toward those ids.
3. After integration, **heap** remaining risks by user impact × likelihood.

This file should grow with your domains (hardware, robotics, scientific computing): append new sections rather than bloating `SKILL.md` with duplicates.
