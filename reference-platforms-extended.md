# Extended platform and vendor map (optional)

**Tool-class map, not a mandate:** each row is an **example** of a product category (design tooling, hosting, observability, etc.). Prefer **Reference-informed domain coverage** in `SKILL.md` for how to pick by **job** without hardcoding vendors. Use only when the stack or user workflow touches these systems. **Verify current pricing, ToS, and data handling** before recommending a dependency. This list is **not exhaustive** and not endorsement.

| Name | Typical jobs in product iteration | Risks / notes |
|------|-------------------------------------|---------------|
| **GitHub** | Source, Issues, Projects, Actions, Codespaces, Packages (artifact registries), Advisory DB | Secret scanning; fork license confusion; Actions minute billing; do not confuse GitHub Packages with this Codex **skill package** folder. |
| **GitLab / Bitbucket** | Same class as GitHub; some orgs self-host | Runner security; upgrade cadence. |
| **Vercel** | Next.js previews, edge functions, analytics | Bandwidth billing; serverless limits; env var blast radius. |
| **Netlify** | Static + serverless, forms, split testing | Function cold starts; identity bridging. |
| **Cloudflare** | Workers, Pages, R2, WAF, CDN, Tunnel | Global key management; Workers CPU limits; cache purge discipline. |
| **Railway / Render / Fly.io** | Long-lived services, databases, simple deploy | Sleep policies; disk ephemerality; egress cost. |
| **AWS / GCP / Azure** | Full cloud primitives, compliance programs | IAM complexity; bill shock; region data residency. |
| **Supabase / Firebase / Appwrite** | Auth + DB + realtime + storage bundles | Row-level security correctness; vendor pricing tiers; migration off. |
| **InsForge** | Managed REST-style backend (auth, DB, storage, functions, AI hooks) | Lock-in vs speed; JWT handling; rate limits. |
| **Figma / Figma Make** | Design system, prototypes, AI-assisted flows | Seat model; export fidelity; dev mode contract. |
| **Google Stitch** | Prompt-to-UI exploration, design constraints | Labs product churn; accessibility not automatic; license on output. |
| **Google AI Studio** | Prompt iteration, small apps, API keys | Data retention settings; paid tier after quota. |
| **Google Antigravity** | Multi-agent IDE workflows, artifacts | Same as any agent host: verify diffs, no secret paste. |
| **OpenAI / Anthropic / etc. dashboards** | Key rotation, usage caps, eval logs | Spend caps; logging of customer data toggles. |
| **Linear / Jira / Height** | Issue hygiene, release tracking | Field entropy; automation noise. |
| **Sentry / Datadog / Honeycomb** | Errors, APM, traces | PII scrubbing; sampling; cost. |
| **Codex / IDE agents** | Local iteration and delegated review | Workspace trust; command allowlists. |

**Rule:** If the product does not use a row, **do not** drag it into the conversation—toolchain tourism fails the Work Filter.
