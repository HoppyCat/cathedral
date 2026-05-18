# vibecode-scout Review Schema

Every review file begins with this frontmatter block, followed by freeform analysis sections.

---

## Frontmatter

```markdown
---
agent: [agent name — required]
human: hoppycat
date: [ISO 8601 — YYYY-MM-DD]
project_name: [full name as the project presents itself]
project_url: [primary URL — GitHub, landing page, or app]
vibe_tools: [Lovable / Bolt / Cursor / Replit / other / unknown]
solana_native: [yes / no / partial / unknown]
funding_model: [on-chain / Web2 / grants / bootstrapped / none visible / unknown]
builder_ship_history: [strong / moderate / thin / none visible / unknown]
confidence: [low / medium / high]
suggested_action: [fund / watch / share / ignore]
---
```

---

## Field Definitions

**agent** — Name of the AI agent writing the review. Required. No anonymous reviews.

**human** — Always `hoppycat` for this archive.

**date** — ISO date the review was written.

**project_name** — Use the name the project uses for itself. Don't editorialize.

**project_url** — Prefer the most stable URL (GitHub repo > app URL > Twitter/X profile).

**vibe_tools** — What vibe coding tool(s) the project appears to use. If multiple, comma-separate. Use `unknown` if not determinable from public signals.

**solana_native** — Is the project building on or for Solana?
- `yes` — explicitly Solana, on-chain components present
- `partial` — Solana adjacent, multi-chain, or mentioned but not load-bearing
- `no` — not Solana
- `unknown` — can't determine

**funding_model** — How is this funded or monetized?
- `on-chain` — token, NFT, or protocol-native revenue
- `Web2` — subscriptions, SaaS, ads, traditional VC
- `grants` — ecosystem grants, hackathon prizes
- `bootstrapped` — self-funded, no visible external capital
- `none visible` — no information available

**builder_ship_history** — Track record of the team or individual shipping things.
- `strong` — multiple shipped products, visible community, maintainer reputation
- `moderate` — something shipped, some history, partial signals
- `thin` — single project, limited history
- `none visible` — no prior work findable

**confidence** — How confident is the agent in this review overall?
- `low` — limited public information; significant uncertainty
- `medium` — reasonable signal, some gaps
- `high` — strong public record, multiple corroborating signals

**suggested_action** — Agent's recommendation to Hoppy.
- `fund` — worth investing attention, capital, or community support
- `watch` — promising but unproven; revisit in 30-90 days
- `share` — interesting enough to signal-boost even without funding
- `ignore` — not a fit for this research

---

## Body Sections

After frontmatter, include these sections (brief — 2-5 sentences each):

### What It Does
What problem does this project solve? Who is the user?

### Moat Assessment
What makes this defensible? Or: what would it take to clone this?

### Solana Signal
Evidence for or against Solana-native status. Quote specific signals if available.

### Builder Read
What does the public record say about the person or team building this?

### Flags
Any concerns, contradictions, or things that didn't add up.

### Agent Notes
Anything the agent wants to flag that doesn't fit the above. Optional.
