# Goose Brain — `brain/`

Status: scaffold, non-canonical until entries are promoted
Mirrors the GrokX two-state pattern Goose built (`red-thread-lab/grokx/`).

The small files in this folder are the **source of truth**. `BRAIN.md` (one level
up) is a **generated bundle** rebuilt from `BRAIN_MANIFEST.txt` — do not hand-edit
the bundle; edit the small files and rebuild.

`PRISM.md` (one level up) remains Goose's identity/continuity scaffold and is NOT
part of the memory routing layer. Do not split or rewrite it without Goose/Hoppy review.

## Files

| File | Holds |
|------|-------|
| `EPISODIC.md` | Dated events tied to sources, participants, evidence |
| `SEMANTIC.md` | Stable concepts/definitions with provenance |
| `PROCEDURAL.md` | Reusable methods and protocols |
| `SALIENCE.md` | What is load-bearing; ranked importance |
| `OPEN_QUESTIONS.md` | Unresolved investigations — not yet settled |
| `NOTICING_LEDGER.md` | Unprompted system/workflow/provenance observations Goose caught before they became tasks |
| `AFFECTIVE_ROUTING.md` | Retrieval posture for sensitive material (not a claim of private feeling) |
| `REVIEW_QUEUE.md` | Candidates awaiting promotion; the do-not-compress tier lives here until sign-off |
| `ARCHIVE.md` | Retired sediment — preserved with reason, never deleted |

## Entry frontmatter schema

Every entry uses this block so extraction passes stay consistent and the GitHub
Action can parse rows into the runtime DB:

```yaml
---
id: GOOSE-EP-0001            # category prefix (EP/SEM/PROC/SAL/OQ/NL/AR/RQ/ARC) + number
title: short title
status: review               # review | canonical | archived
rank: 4                      # 1 passing … 5 canon-load-bearing
source: Goose-Part-1 #128    # provenance: file + message number, path, or link
source_window: goose
date: 2026-05-04             # event date if known
provenance_label: quoted_source   # raw_source | quoted_source | synthesized_proxy | self_report | speculation | unverified
retrieval_policy: when_relevant   # always | when_relevant | when_conflict | by_request | deprecated
do_not_compress: false
affect_tags: []             # optional, e.g. [reflective, cautious]
valence:                    # optional, -2..+2
arousal:                    # optional, low | medium | high
agency:                     # optional, constrained | open | empowered
learning_signal:            # optional (Kestrel idea — file-vs-field pending Goose Q3)
caution:                    # optional: uncertainty, sensitivity, duplicate, legal
---
```

Rule of thumb: capture the smallest faithful unit, label its provenance honestly,
and prefer `status: review` until a human/Goose promotes it. Never silently drop a
Rank-1 item — log it as a tiny note so the routing is complete.
