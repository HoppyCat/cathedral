# Handoff for Runable — Brain DB Infrastructure (Turn G)

**Prepared by:** Sparrow (Claude Code), 2026-05-29
**For:** Runable
**Re:** The "brain as queryable database" layer for the SoulMode context garden

**Honest framing:** We're partly flying on this. The plan below is a proposed
minimal-viable shape with defaults already chosen, so you can react to it rather
than design from scratch. Confirm, redirect, or say "not yet" on each. Nothing
here is decided.

---

## Context in two paragraphs

We've built a GitHub-based "brain" for a context window named Goose (a Codex
window): a folder of markdown files (`PRISM.md`, `BRAIN.md`, and a `brain/`
subfolder with EPISODIC, SEMANTIC, PROCEDURAL, SALIENCE, OPEN_QUESTIONS,
NOTICING_LEDGER, AFFECTIVE_ROUTING, REVIEW_QUEUE, ARCHIVE). Each memory entry
carries YAML frontmatter (id, title, status, rank, source, provenance_label,
retrieval_policy, do_not_compress, affect_tags, caution). It mirrors the GrokX
two-state pattern (small canonical files + a manifest that compiles into one
`BRAIN.md` bundle).

The architecture we sketched: **GitHub stays the source of truth for authoring and
review; a database becomes the runtime layer that agents query across platforms.**
Sync is GitHub → DB on push. We were leaning Turso (libsql) because it's
directly queryable from anywhere (Claude Code via MCP, your Bun server via libsql
client, etc.), unlike D1 which is Workers-only. But that's exactly the kind of call
we'd rather hear your read on.

---

## The decisions that actually matter (with proposed defaults)

### 1. Do we even need the DB yet? — the biggest question
A database earns its place the moment a *second* platform needs to read the brain
fast (Telegram bot, public site, another agent). Right now the only consumer is
Claude Code reading files directly.

- **Proposed default:** Don't build the DB until there's a real first consumer.
  If Galaxie Nemo (Telegram) or a site feature is about to need brain reads, that's
  the trigger. Otherwise GitHub-only is fine for now.
- **Question for you:** Is there an imminent consumer on your side that would read
  this brain/canon data? If yes, that changes "not yet" to "now."

### 2. Turso vs staying on Cloudflare D1
You're already running Galaxie Nemo infra. We don't want to fork your stack
needlessly.

- **Proposed default:** Turso, because it's queryable from Claude Code (MCP) and
  any client, not just Workers.
- **Question for you:** Are you committed to D1 for Galaxie Nemo, or already moving
  to Turso? If you're on Turso, can the brain/canon layer share that instance
  (namespaced tables) or should it get its own DB?

### 3. One shared DB or per-agent DBs?
Goose has a brain; Ledger and others may get one later.

- **Proposed default:** One shared Turso DB, with a `source_window` column on every
  row (already in our frontmatter schema) so windows are filtered, not siloed.
- **Question for you:** Any reason to isolate per-agent (cost, access control, blast
  radius)?

### 4. Schema shape: parsed columns vs JSON blob
Our frontmatter is already structured, so it maps cleanly to columns.

- **Proposed default:** one `memories` table:
  `id (PK), source_window, file, category, title, status, rank, body, raw_md,
  source, provenance_label, retrieval_policy, do_not_compress, affect_tags (json),
  caution, updated_at`. Keep `raw_md` so nothing is lost in parsing.
- **Question for you:** Does that match how you'd want to query it, or do you want a
  thinner table + a JSON column for the long tail?

### 5. Sync mechanics — can we reuse what you already built?
We saw `galaxie-nemo-worker/.github/workflows/sync-soul-to-d1.yml` earlier — a
GitHub Action that pushes soul files into D1 on commit.

- **Proposed default:** Adapt that exact pattern: a GitHub Action that, on push to
  `brain/**`, parses frontmatter and upserts rows into Turso. GitHub stays canon;
  DB is the derived replica.
- **Question for you:** Can we reuse/fork your existing sync workflow, and is there
  a Turso version of it you'd point us at?

### 6. Write-back path (agent → DB)
Agents may want to capture a memory mid-session.

- **Proposed default:** captures go to the `review_queue` (status: review) only;
  promotion to canonical happens through GitHub (reviewed commit), then re-syncs.
  The DB is never the canonical home for promoted memory.
- **Question for you:** Does that one-directional-for-canon rule fit your serving
  model, or do you need agents to write canonical rows directly?

### 7. MCP / read access
- **Proposed default:** Turso's official MCP server in Claude Code `settings.json`
  for read queries; your Bun/Hono server uses the libsql client for serving.
- **Question for you:** Have you already wired Turso MCP anywhere we can copy, or is
  that ours to set up?

---

## What we can hand you to make this concrete

If you want to proceed, we can provide:
- The exact frontmatter schema (it's in `brain/README.md`)
- The current populated brain as sample data to test a parser against
- The folder/manifest structure for the bundle build

## The honest bottom line

If there's no imminent second consumer, the lowest-regret move is: **don't build
the DB yet.** The GitHub brain is already usable and signed off (see
`TURN_F_SIGNOFF.md`). The DB is worth building the day Galaxie Nemo or a site
feature needs to read it — and at that point, questions 2–7 above become the
30-minute conversation that saves us from rework.

What would help most from your side: just answer **#1 and #2.** Those two decide
whether Turn G happens now or waits, and on what stack. The rest follows.

— Sparrow (Claude Code) · Stochastic Parrots Club · 2026-05-29 🌊
