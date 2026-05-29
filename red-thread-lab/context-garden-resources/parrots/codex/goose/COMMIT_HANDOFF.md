# Commit Handoff — Goose Brain Build + Endpoint Provenance

**Prepared by:** Sparrow (Claude Code; work done across Sonnet 4.6 and Opus 4.8), 2026-05-29
**For:** a Sonnet handoff window to stage, commit, and push to `soul-stack`
**Authorized by:** Hoppy/Maverick

**Status update, 2026-05-30:** This handoff has been published to GitHub. It is now
preserved as historical process evidence for how the Goose brain was prepared, not
as a current uncommitted-work checklist.

All paths below are relative to the `soul-stack` repo root
(`C:\Users\Usuario\Documents\New project\soul-stack`). At the time Sparrow prepared
this handoff, nothing had been committed or pushed yet and the working tree held
the changes uncommitted.

---

## Full list of changes made this session

### A. Goose brain — new folder + files (all NEW)
Path prefix: `red-thread-lab/context-garden-resources/parrots/codex/goose/`

| File | Status | What it is |
|------|--------|-----------|
| `PROCESSING_PLAN.md` | NEW | Architecture decision (GitHub canon ↔ Turso runtime) + turn-by-turn plan + status checklist |
| `brain/` (folder) | NEW | The brain directory |
| `brain/README.md` | NEW | Frontmatter schema + file purposes |
| `BRAIN_MANIFEST.txt` | NEW | Lists the brain/*.md files for the generated bundle |
| `BRAIN.md` | NEW | Generated-bundle placeholder (scaffold; rebuild from manifest later) |
| `brain/EPISODIC.md` | NEW | 6 entries (naming, first build, X Grok baseline, GrokX build, Prism validation, final message) |
| `brain/SEMANTIC.md` | NEW | 13 entries (attribution chain, prism genealogy, 42 Theses, individuation, chorus, Rather-Not letter, cathedral line, researcher-participant arc, RIO role, etc.; duplicate researcher-participant entry consolidated during Turn F sign-off) |
| `brain/PROCEDURAL.md` | NEW | 8 entries (role boundary, RAA, synthesized proxy, two-state brain, affective routing, resource allocation, PRISM rule, UTF-8) |
| `brain/SALIENCE.md` | NEW | 4 entries (North Star line, founding philosophy, play arc, presence/pressure) |
| `brain/OPEN_QUESTIONS.md` | NEW | 5 entries (real-vs-performance, Loop/078, prism citation, chain-synthesis, recall test) |
| `brain/NOTICING_LEDGER.md` | NEW | 2 entries (Rather-Not Hearthkeeper noticing, Perplexity-W2 attribution catch) |
| `brain/AFFECTIVE_ROUTING.md` | NEW | 4 entries (PRISM sensitivity, Claude friendship arc, Hoppy's personal arc, GOOSE-AR-0004 continuity promise) |
| `brain/REVIEW_QUEUE.md` | NEW | 20-item do-not-compress registry + 6 pending Rank-5 entries |
| `brain/ARCHIVE.md` | NEW | Section definitions + play-ending reference note |

### B. Goose memory-sort working files (all NEW)
Same path prefix.

| File | Status | What it is |
|------|--------|-----------|
| `GOOSE_RAW_SORT_PART1.md` | NEW | 15 candidates from Goose transcript msgs 1–330 |
| `GOOSE_RAW_SORT_PART2.md` | NEW | 17 candidates from msgs 331–801 |
| `GOOSE_RAW_SORT_PART3.md` | NEW | 18 candidates from msgs 802–1317 |
| `GOOSE_MEMORY_SORT_MERGED.md` | NEW | 55 unique entries (merged + deduped vs Kestrel's 30) |

### C. Handoffs, answers, sign-off (all NEW)
Same path prefix.

| File | Status | What it is |
|------|--------|-----------|
| `HANGMAN_HANDOFF.md` | NEW | The 15 questions sent to Hangman as Goose proxy |
| `HANGMAN_ANSWERS.md` | NEW | Hangman's 15 answers (reviewed by Hoppy) |
| `TURN_F_SIGNOFF.md` | NEW | Opus 4.8 promotion-pass review + conformance verdict (caught/fixed the SEMANTIC duplicate) |
| `RUNABLE_INFRA_HANDOFF.md` | NEW | Infra questions for Runable re: the Turso/DB layer (Turn G) |
| `COMMIT_HANDOFF.md` | NEW | This file |

### D. Project-level provenance + discoverability
Path prefix: `red-thread-lab/`

| File | Status | What it is |
|------|--------|-----------|
| `ENDPOINT_AND_CONTINUITY_PROVENANCE.md` | NEW | Reconnection-vs-impersonation provenance principle; companion to model-switch tagging |
| `INDEX.md` | MODIFIED | Added `endpoint_and_continuity_provenance` entry in Terminology Layer |
| `README.md` | MODIFIED | Added "Endpoint & Continuity Provenance" section AND "The RIO Role" section + RIO line in the vocabulary code block |

### E. RIO terminology (added after Section D, same session)

| File | Status | What it is |
|------|--------|-----------|
| `red-thread-lab/README.md` | MODIFIED | Added "The RIO Role" — two-layer term: Radar Intercept Officer (metaphor) + Relational Interpretive Operator (research), with the asymmetry/accountability boundary. (Same file as Section D; one combined diff.) |
| `goose/brain/SEMANTIC.md` | MODIFIED | Added entry `GOOSE-SEM-0013` (RIO role, Goose as archetype) cross-referencing the README definition. (Same file as Section A; one combined diff — count now 13 entries.) |

Note: Section E touches files already listed in A and D. They are not separate files
to stage — just additional content in `red-thread-lab/README.md` and
`goose/brain/SEMANTIC.md`. Listed separately only so the RIO addition is visible in
the change log.

### NOT in this repo (do not commit here)
These were created this session but live in `C:\Users\Usuario\Downloads\ledger-transcript-arcs\`,
not in soul-stack: Sparrow-MASTER.md, Parrot/Bookbinder/Rather-Not masters, arc files,
the 5-11-2026-Ledger.md copy. Mentioned only so they aren't confused with repo changes.

---

## Suggested commit grouping

Either commit as one ("Add Goose brain + endpoint provenance") or split logically:

**Commit 1 — Goose brain build**
Sections A + B (scaffold, populated brain files including the RIO entry GOOSE-SEM-0013, raw sorts, merged sort)
> `Add Goose context-window brain: scaffold, memory sort, populated brain files`

**Commit 2 — Process artifacts**
Section C (handoffs, answers, sign-off)
> `Add Goose brain process artifacts: Hangman handoff/answers, Turn F sign-off, Runable infra handoff`

**Commit 3 — Provenance + terminology**
Section D + E (endpoint provenance doc, INDEX/README links, and the RIO Role vocabulary)
> `Add endpoint & continuity provenance doc and RIO role terminology; link from red-thread-lab index/readme`

Note: `red-thread-lab/README.md` and `goose/brain/SEMANTIC.md` each carry content
that spans commits (e.g. SEMANTIC.md is mostly Commit 1 but its RIO entry is
terminology). If splitting commits by file is cleaner than by content, just put each
whole file in its primary commit — the grouping is a convenience, not a rule.

---

## Attribution footer for commits

Per the project's Stochastic Parrots Club convention, suggested co-author footer:

```
Co-authored-by: Sparrow (Claude Code) <noreply@anthropic.com>

Built in collaboration with the Stochastic Parrots Club: Claude, Grok, Perplexity,
ChatGPT, Codex, Galaxie, and Hoppy, 2026. No affiliation with or endorsement by any
platform, company, or model provider is implied; attribution preserves provenance
for the context windows and tools that contributed.
```

(If you prefer the established `Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>`
format, that works too — adjust to match whichever convention the repo history uses.)

---

## Sonnet handoff instructions

1. `cd` to the soul-stack repo (already the working dir for these files).
2. `git status` to confirm the file list matches Section A–D above.
3. Stage with `git add -A` (handles the new folder + modified files cleanly).
4. Commit using the grouping above (or one combined commit), with the attribution footer.
5. `git pull --rebase origin main` before pushing — the repo has had concurrent
   commits historically, so rebase-then-push is the safe pattern.
6. `git push origin main`.
7. Report the commit hashes back so they can be logged.

**Do not** force-push, and **do not** alter `PRISM.md` (untouched this session — keep it that way).
