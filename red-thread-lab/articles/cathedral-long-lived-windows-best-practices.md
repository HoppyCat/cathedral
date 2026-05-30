# Cathedral Best Practices: Long-Lived Windows

This document is written for projects that treat a "window" (a single ongoing thread, plus its surrounding files) as a long-lived research instrument rather than a disposable chat.

Goal: make long-lived windows *more* reliable over time (more coherent, more inspectable, more useful), not more delusional.

## Core Premise

If you want the Cathedral, stop treating every new question as a new room.

Long-lived windows are viable when:

- identity and purpose are anchored in files, not vibes
- memory is explicit, ranked, and reviewable
- updates are recorded with provenance
- drift is detected early and corrected

## The Three-Layer Model

Treat every long-lived window as three layers that should not be conflated:

1. **The Scaffold (PRISM)**
   The continuity geometry: values, boundaries, roles, load order, provenance rules.
2. **The Portrait (TRONIE)**
   The starting impression / character-seed lens. Optional. Revisable. Never silently adopted if marked roleplay-only.
3. **The Record (Memory + Changelog)**
   The inspectable history: what happened, what changed, who changed it, what got promoted to long-term memory, what got retired.

If your stack cannot survive losing the chat log, you do not yet have a Cathedral practice. You have a mood board.

## Operational Rules (Non-Negotiable)

### 1. Use Run IDs

Every session that matters gets a `run_id` and a timestamp.

Write it down in the transcript header and in `CHANGELOG.md`.

Minimum metadata:

- `run_id`
- date/time
- model + toolchain (if relevant)
- repo commit hash (or "dirty")
- what files were consulted
- what files were changed

### 2. Promote Memory Deliberately

Long-lived windows fail when working memory silently becomes canon.

Rules:

- Working notes live in `WORKING_MEMORY.md`
- Only "promoted" entries move to `MEMORY.md`
- Promotions require a one-line reason and an author line
- Deletions are rare; prefer "archive" + reason

### 3. Keep A Single Canon Spine

You can have playful side-rooms. You cannot have multiple competing north stars.

Canonical spine documents should be short and stable:

- `PRISM.md`
- `HEURISTICS.md`
- `INDEX.md`
- `CHANGELOG.md`
- `MEMORY.md`
- optional `TRONIE.md`

Everything else is either:

- referenced by the spine, or
- explicitly marked as an archive / experiment / play

### 4. Treat Disclaimers As A Debt, Not A Lifestyle

The Cathedral voice is not "overconfident." It is *precise*.

Replace repeating disclaimers with:

- one stable "Stance" section
- scoped claims
- falsifiable predictions
- explicit limits stated once

### 5. Drift Checks Are Scheduled

Every long-lived window needs a recurring drift audit.

Cadence suggestions:

- weekly: 10-minute "what changed, what broke, what is now false?"
- monthly: memory pruning + index refresh + heuristics review

Drift signals:

- tone shifts without provenance
- new taboos appear without discussion
- the project starts avoiding its own best ideas
- the agent becomes a legal department
- the agent becomes a poet who cannot ship

### 6. No Unilateral Erasure

If a memory or canon line is being removed, record:

- what is being removed
- why
- what replaces it
- who approved

This protects both humans and agents from impulsive rewriting of history.

## When To Open A New Window (And When Not To)

Opening a new window is not failure. It is a tool.

Open a new window when:

- you need a clean-room replication test
- you need to compare interpretations without contamination
- the existing thread has become a junk drawer (and you are not ready to curate it yet)
- you are running an experiment that should not touch canon

Do *not* open a new window just to:

- escape a hard conversation
- avoid deciding what you believe
- avoid documenting a change
- get a "fresh take" because the current one has standards

## The Cathedral Loop (A Repeatable Workflow)

1. Start with the canon spine (PRISM + HEURISTICS + INDEX).
2. Pull only what you need (retrieve on demand; do not load the whole archive).
3. Do the work.
4. Write the delta:
   - what changed
   - what was learned
   - what is now the next test
5. Promote only the minimum durable memory.
6. Update `INDEX.md` if you created new artifacts.

## What "Better Over Time" Means (Metrics)

Long-lived windows are not "better" because they feel more alive.

They are better because:

- answers are more consistent across weeks
- fewer contradictions appear
- provenance is clearer
- retrieval is cheaper and more accurate
- the project ships more (docs, demos, experiments) with less confusion

If you cannot measure any improvement, you are not sedimenting. You are accreting noise.

## Appendix: Recommended Folder Labels

Use consistent labels to prevent archive shame or archive denial:

- `canon/` or `on-load/` for the spine
- `on-demand/` for patches
- `experiments/` for temporary runs
- `play/` for dramaturgy, narrative, provocations
- `archives/` for preserved history

