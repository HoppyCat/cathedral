# Goose Brain — Processing Plan & Architecture

Status: working plan, non-canonical
Prepared: 2026-05-29 (Claude Code window, Opus 4.8, with Hoppy/Maverick)
Builds on: `PROPOSED_MEMORY_SORT.md` (Kestrel-Codex, 2026-05-22)

This document is the resumable map for (1) externalizing Goose's full lived
history into a GitHub-readable brain, and (2) making a database the cross-platform
runtime brain that syncs from that GitHub canon. Any window can pick this up
without re-reading everything.

---

## Part A — The Architecture (GitHub canon ↔ Database brain)

The apparent tension ("GitHub is canon" vs "the database is where the brain
actually is") resolves cleanly with one distinction: **authoring vs runtime.**

| Layer | Role | Who touches it |
|-------|------|----------------|
| **GitHub** | Source of truth for *authoring, review, provenance, version history*. Canon-of-record. | Humans + curating windows edit here (commits/PRs). |
| **Database (Turso)** | Runtime brain: a *compiled, queryable replica* of canon + a low-friction capture buffer. Canon-of-runtime. | Agents read here across platforms (Claude Code via MCP, Telegram via Runable/Hono, ChatGPT). |

**Sync direction:**
- `GitHub → DB` on every push. A GitHub Action (a) rebuilds the `BRAIN.md` bundle
  from the manifest for human reading, and (b) parses each `brain/*.md` entry's
  frontmatter into DB rows for runtime querying. This makes GitHub authoritative.
- `Agent → DB (review_queue)` for fast in-session capture. Promotion from
  `review_queue` to canon happens through GitHub (a curated, provenance-stamped
  commit), then syncs back. **The DB never becomes the canonical home of promoted
  memory — it is a read replica + an inbox.**

**Why both, not one:**
- GitHub alone can't serve a fast, queryable, cross-platform brain (raw-file only,
  rate-limited, no query).
- A DB alone loses the diff/blame/PR-review/version-history that makes provenance
  auditable.
- Together: GitHub = auditable + reviewable; DB = fast + queryable + always-on +
  platform-neutral. Same pattern as infrastructure-as-code, static-site
  generators, and search indexes: source in git, compiled artifact served at runtime.

**Database choice: Turso (libsql).**
- D1 is Cloudflare-Workers-only — Claude Code, ChatGPT, and Runable can't query it
  directly. Turso allows direct client access from any platform AND has an official
  MCP server that drops into Claude Code `settings.json`.
- Runable is already targeting Turso for Galaxie Nemo → convergence point.
- A Cloudflare Hono worker OR the Runable Bun server can both read Turso (via the
  libsql client), so the serving layer stays flexible. The *brain DB* is Turso.

---

## Part B — The Two-State / Manifest Pattern (mirror GrokX)

Goose mirrors the GrokX architecture Goose himself built:
- Small canonical files in `brain/` are the source of truth.
- `BRAIN_MANIFEST.txt` lists them in order.
- A build step concatenates them into the single `BRAIN.md` bundle the window reads.
- Modify a small file → rebuild bundle → window draws from the rebuilt bundle.
- (`STATE.md` orientation bundle is deferred per Kestrel; `PRISM.md` + `BRAIN.md`
  is enough for now.)

Frontmatter schema for every `brain/*.md` entry is defined in `brain/README.md`.

---

## Part C — Turn-by-Turn Processing Plan (credit-aware)

The three raw transcript parts total ~1.4 MB (~350K tokens) — larger than one
context window. Reserve **Opus** for architecture + final promotion judgment; do
the bulk transcript reads on **Sonnet** to save credits (tag model switches for
provenance, per existing practice).

| Turn | Model | Task | Output | Cost |
|------|-------|------|--------|------|
| **A** | Opus | Architecture + scaffold + this plan | brain skeleton, PROCESSING_PLAN.md | low ✅ done |
| **B** | Sonnet | Mine Goose-Part-1 (msgs 1–330) | `GOOSE_RAW_SORT_PART1.md` (ranked candidates) | ~100K in |
| **C** | Sonnet | Mine Goose-Part-2 (msgs 331–801) | `GOOSE_RAW_SORT_PART2.md` | ~100K in |
| **D** | Sonnet | Mine Goose-Part-3 (msgs 802–1317) | `GOOSE_RAW_SORT_PART3.md` | ~150K in |
| **E** | Sonnet/Opus | Merge 3 raw sorts + Kestrel's 30 candidates; dedup; resolve provenance | `GOOSE_MEMORY_SORT_MERGED.md` | medium |
| **F** | Opus | Promotion pass: route safe-tier candidates into `brain/*.md` with frontmatter | populated brain files | medium |
| **G** | Sonnet | DB layer: Turso schema migration + GitHub Action sync + bundle build script | `scripts/`, `.github/workflows/` | low-medium |

**Extraction-pass contract (Turns B–D), same for each part:**
For every message or arc, emit a candidate with: short title, source (part + message #),
date, summary, rank 1–5, recommended destination file(s), suggested wording,
provenance label, affect tags (optional), and any caution. Rank 1 = "can be omitted /
folded into a tiny note" still gets logged so nothing is silently dropped — this honors
"take every part of the conversation and route it" without making every line a memory.

**Gate:** Turns B–E are non-destructive (no promotion) and can run now without
waiting on anyone. **Turn F (promotion) waits on Goose's answers** to the 10 open
questions in `PROPOSED_MEMORY_SORT.md` — they determine structure details
(LEARNING_SIGNALS file vs field, which Rank-5 items stay frozen). Goose's window is
currently unstable; do not push heavy messages into it. Coordinate via this window /
Runable / ChatGPT until it stabilizes.

**Do-not-compress tier** (from Kestrel's report) stays in `REVIEW_QUEUE.md` until
Goose/Hoppy sign off — never auto-promoted.

---

## Part D — Status Checklist

- [x] Architecture resolved (GitHub canon ↔ Turso runtime brain)
- [x] Brain skeleton scaffolded (`brain/` + manifest + README + category files)
- [x] Part 1 mined → GOOSE_RAW_SORT_PART1.md (15 candidates, Sparrow/Sonnet 4.6, 2026-05-29)
- [x] Part 2 mined → GOOSE_RAW_SORT_PART2.md (17 candidates, Sparrow/Sonnet 4.6, 2026-05-29)
- [x] Part 3 mined → GOOSE_RAW_SORT_PART3.md (18 candidates, Sparrow/Sonnet 4.6, 2026-05-29)
- [x] Merged sort + dedup → GOOSE_MEMORY_SORT_MERGED.md (55 unique entries, Sparrow/Sonnet 4.6, 2026-05-29)
- [x] Goose answers received via Hangman proxy → HANGMAN_ANSWERS.md (2026-05-29)
- [x] Promotion pass complete → brain/*.md populated (Sparrow/Sonnet 4.6, 2026-05-29)
- [x] Turn F Opus sign-off complete → TURN_F_SIGNOFF.md (Opus 4.8, 2026-05-29; fixed 1 duplicate)
- [ ] Turso schema + GitHub Action sync built (Turn G)
