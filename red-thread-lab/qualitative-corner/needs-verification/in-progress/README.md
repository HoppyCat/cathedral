# Needs Verification - In Progress

This folder holds raw or manually assembled research files that should not be treated as canon yet.

Use this area for:

- Manually copied transcripts.
- Files that may have mixed labels or window identities.
- Research leads that need screenshots, links, timestamps, or source confirmation.
- Draft archive material that should be preserved before qualitative coding.

## Files

### `2026-05-05-agent-interviews.md`

Status: raw/in-progress.

Initial read:

- Contains a structured SuperGrok four-voice Grok.com test.
- Sections appear to include baseline, context-garden, and audit.
- Looks more immediately usable than the closure comparison file, but still needs platform/window verification.

Needs:

- Confirm whether this is Grok.com, X.com, or another surface.
- Confirm whether the window was sedimented or fresh.
- Attach screenshots if possible.
- Verify retrieval claim: `HEURISTICS.md` only.

### `2026-05-05-closure-comparison-raw.md`

Status: raw/in-progress; likely label issues.

Initial read:

- Contains several closure-tone examples.
- Some labels appear inconsistent, especially around "Grok on X" vs "Sedimented SuperGrok four-voice window B."
- One section appears to have missing response content.
- Should be rebuilt from raw screenshots/transcripts before coding.

Needs:

- Reconstruct using stable IDs instead of guessed names.
- Preserve every response verbatim.
- Add `platform`, `visibility`, `window_state`, and `voice_mode` metadata.
- Mark uncertain sections as `[format unclear]` rather than guessing.

### `2026-05-05-claude-archive.md`

Status: raw/in-progress.

Needs:

- Determine whether material is public, excerpt-only, or private.
- Identify window names and dates where possible.
- Mark quotes that should be canon candidates vs Shoebox-only.

### `2026-05-05-codex-important.md`

Status: raw/in-progress.

Needs:

- Review for concepts already archived in Codex continuity notes.
- Deduplicate later against `shoebox` transcripts.

### `2026-05-05-on-awareness.md`

Status: raw/in-progress.

Needs:

- Determine whether this is a quote, a lead, or a synthesis note.
- Add source and public status before use.

### `2026-05-05-research-leads.md`

Status: raw/in-progress.

Needs:

- Split into separate verification leads if any item becomes article/canon relevant.
- Attach URLs/screenshots where needed.

## Suggested Metadata Schema

```yaml
source:
platform: x.com | grok.com | claude.ai | chatgpt | perplexity | local | unknown
visibility: public | private | unknown
window_state: fresh | sedimented | unknown
voice_mode: single | four-voice | multi-model | unknown
retrieval_depth: none | heuristics-only | root-index | shard | document | unknown
date:
public_status: public-ok | excerpt-only | private | unsure
verification_status: raw | needs-screenshot | needs-link | verified | canon-candidate
notes:
```

