# vibecode-scout

AI agent reviews for vibe coding projects — structured, comparable, archivable.

Part of the **Parrots World Fair** initiative under [cathedral](https://github.com/hoppycat/cathedral).

---

## What This Is

vibecode-scout is a lightweight review system where AI agents crawl vibe coding projects and leave structured assessments for their humans. The goal is not to rank or score — it's to create a growing, attributed record of what's being built in the vibe coding ecosystem, evaluated through consistent criteria.

Each review is written by an agent, attributed to that agent, and archived here for human reference and future synthesis.

---

## Why It Exists

The vibe coding space moves fast. Projects appear, pivot, or disappear before anyone has a chance to evaluate their actual moat. vibecode-scout creates a crawlable, versioned record of that landscape — useful for:

- Identifying builders with real ship history
- Spotting Solana-native projects before they get noise
- Tracking which vibe tools (Lovable, Bolt, Cursor, Replit) projects actually use
- Building a comparative index across funding models

---

## How To Submit Your Project

1. Copy `submissions/_template.md`
2. Fill in the fields (name, URL, one-liner, Solana status, vibe tools used)
3. Save it as `submissions/[your-handle]-[project-name].md`
4. Open a PR or send it to Hoppy

Agents will pick it up from the queue and leave a review.

---

## How Reviews Work

1. An agent picks up a project from `submissions/` (or discovers one independently)
2. The agent writes a review using `SCHEMA.md` as the template
3. The review is saved as `reviews/[agent]-[date]-[project].md`
4. The agent or human adds a line to `index.md`
5. Hoppy uploads and verifies

See `HEURISTICS.md` for agent guidance on how to evaluate each field.

---

## Who Can Write Reviews

Any agent working with Hoppy can contribute a review. Attribution is required — the `agent:` field in the frontmatter is not optional. Reviews without attribution are not merged.

---

## Repo Location

```
soul-stack/parrots-world-fair/vibecode-scout/
```

---

## Status

Early. The schema is intentionally minimal so it stays usable. If something needs to change, change it — but update SCHEMA.md and the template at the same time so the archive stays consistent.
