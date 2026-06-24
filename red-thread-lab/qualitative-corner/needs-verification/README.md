# Needs Verification

This folder holds research leads, raw transcripts, manually copied outputs, and formatted drafts that are not canon yet.

The goal is to preserve material quickly without pretending it has already been fully verified.

## Rapid Archival Anchoring Standard

**Rapid archival anchoring** is the practice of saving AI conversation outputs to a public version-controlled archive shortly after they are produced, so later readers can see a timestamped chain of custody even before full screenshot verification is complete.

This does not prove authenticity. It strengthens provenance.

When possible, preserve:

- The raw output as soon as possible.
- The source platform.
- The estimated delay between generation and upload.
- Whether screenshots, links, or original files still need to be attached.
- Whether a later formatting pass was done by ChatGPT, Codex, or another model.

## Required Header For New Files

Use this block near the top of any new raw or formatted file:

```yaml
provenance_method: rapid archival anchoring
captured_by:
source_platform:
source_window:
capture_delay_estimate: under 1 minute | under 5 minutes | under 1 hour | unknown
processor: none | ChatGPT | Codex | Grok | Claude | Perplexity | other
processing_instruction:
verification_status: raw | timestamp-anchored | formatted-not-verified | screenshot-verified | link-verified | canon-candidate
needs:
  - screenshots
  - source links
  - window identity check
  - platform check
  - verbatim comparison
notes:
```

## Verification Statuses

- `raw`: captured as-is, not yet checked.
- `timestamp-anchored`: uploaded quickly enough to support chain-of-custody plausibility.
- `formatted-not-verified`: cleaned for structure, but not compared against raw/screenshots yet.
- `screenshot-verified`: checked against screenshot evidence.
- `link-verified`: checked against a public URL or source file.
- `canon-candidate`: strong enough to consider for a later canon or article pass.

## Folder Use

- `in-progress/`: raw or manually assembled material that may have label issues.
- Future `chatgpt-formatted/`: outputs cleaned by ChatGPT for structure only.
- Future `raw/`: direct raw captures if we split them out later.

## Rule Of Thumb

Do not delete uncertain material just because it is messy.

Mark uncertainty clearly, preserve the trail, and verify later.

