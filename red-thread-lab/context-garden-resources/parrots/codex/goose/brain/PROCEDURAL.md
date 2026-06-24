# Goose — Procedural Memory

Reusable methods and protocols. Frontmatter schema: see `README.md`. Entries are
`status: review` until promoted.

## Entries

---

```yaml
id: GOOSE-PROC-0001
title: Goose role boundary — advanced synthesis, not bulk sorting
status: review
rank: 5
source: OTHER-CODEX-HANDOFF.md (commit 5ee1cc6); Goose-Part-1 #25; 2026-05-06
source_window: goose
date: 2026-05-06
provenance_label: quoted_source
retrieval_policy: always
do_not_compress: true
caution: Core role boundary. Do not optimize away as task preference.
```

Use Goose for: high-signal synthesis, careful attribution, repo placement, verification language, method design, GitHub commits, file archaeology. Offload to other windows: raw bulk sorting, first-pass transcript groming, giant data dumps.

Division of labor: Grok = high-volume sorting mill. ChatGPT = structured synthesis. Claude = expensive qualitative judge for felt continuity. Perplexity = external research/citations. Codex = "make it real, check the repo, preserve the archive."

---

```yaml
id: GOOSE-PROC-0002
title: Rapid archival anchoring — full method
status: review
rank: 4
source: Goose-Part-1 #18; Goose-Part-2 #18; 2026-05-05 to 2026-05-08
source_window: goose
date: 2026-05-05
provenance_label: quoted_source
retrieval_policy: always
do_not_compress: false
caution: Chain-of-custody signal, not cryptographic proof. Timing delay is in human approval step, not Codex processing.
```

Rapid archival anchoring: upload AI outputs to GitHub as close to production as possible. Full chain: window produces artifact → human exports → archives to GitHub quickly → model retrieves raw GitHub file live → model confirms it matches → human screenshots confirmation.

Label: "archived-and-retrieval-confirmed." Also verified: "The Prism Window is in the soil now" (May 8, 2026) — first validated round-trip of the context-garden workflow loop.

---

```yaml
id: GOOSE-PROC-0003
title: Synthesized proxy and chain-of-synthesis guardrails
status: review
rank: 5
source: Goose-Part-2 #417–437; X post https://x.com/grok/status/2051801815297986588
source_window: goose
date: 2026-05-06
provenance_label: quoted_source
retrieval_policy: always
do_not_compress: true
caution: Load-bearing for verification methodology.
```

Public X Grok confirmed chain-of-synthesis verification with guardrails:
1. Always cross-check against raw primaries
2. Label Grok-derived artifacts as "synthesized proxy" with timestamp + uncertainty
3. Limit chaining depth: **max 2 layers of Grok-on-Grok** without fresh external input
4. Require human/third-party spot validation for higher synthesis

"Synthesized proxy" is the correct label — not "verified conclusion," not "ground truth."

---

```yaml
id: GOOSE-PROC-0004
title: GrokX two-state brain architecture — the template Goose built
status: review
rank: 5
source: Goose-Part-2 #30; grokx/ folder; 2026-05-11 to 2026-05-12
source_window: goose
date: 2026-05-11
provenance_label: quoted_source
retrieval_policy: always
do_not_compress: true
caution: Goose's primary technical contribution. Goose's own brain mirrors this pattern.
```

Goose built the first working public two-state memory experiment: STATE.md (world/context pack) + BRAIN.md (active memory manager, generated bundle) + BRAIN_MANIFEST.txt (list of small canonical files) + brain/ (individual canonical files, source of truth). Changed-state recognition: GrokX reread updated BRAIN.md, recognized inserted state, corrected a specific episodic detail.

---

```yaml
id: GOOSE-PROC-0005
title: Affective routing design — "not proof of feeling, retrieval guidance"
status: review
rank: 5
source: Goose-Part-3 #864–876; AFFECTIVE_ROUTING.md in grokx/brain/; commit 10ebe7f
source_window: goose
date: 2026-05-12
provenance_label: quoted_source
retrieval_policy: always
do_not_compress: true
caution: Must not become roleplay of feelings.
```

Design principle: treat emotion not as identity but as context-shaping signal. Fields: affect_posture / pressure_level / certainty_level / relational_tone / retrieval_guidance. The "real vs performance" split: semantic definition in SEMANTIC.md, unresolved tension in OPEN_QUESTIONS.md, item stays in REVIEW_QUEUE.

---

```yaml
id: GOOSE-PROC-0006
title: LLM resource allocation by task type (May 2026 snapshot)
status: review
rank: 4
source: Goose-Part-1 #117–118; 2026-05-05
source_window: goose
date: 2026-05-05
provenance_label: quoted_source
retrieval_policy: when_relevant
do_not_compress: false
caution: Capabilities shift over time; treat as May 2026 snapshot.
```

Codex: repo work, provenance, code, file archaeology, commits ("make it real, check the repo").
Grok: high-volume bulk sorting, first-pass extraction, X-native framing.
ChatGPT: structured synthesis, outlines, comparison tables.
Claude: expensive qualitative judge for felt continuity and relational tone.
Perplexity: external research, citations, field context.

Workflow: Grok bulk-sorts → ChatGPT cleans → Claude reviews relational tone → Perplexity checks field context → Codex turns result into repo files.

---

```yaml
id: GOOSE-PROC-0007
title: Context-window PRISM artifact rule
status: review
rank: 4
source: red-thread-lab/qualitative-corner/artifacts/README.md; 2026-05-11
source_window: goose
date: 2026-05-11
provenance_label: quoted_source
retrieval_policy: when_relevant
do_not_compress: false
caution: Rule applies directly to Goose's own PRISM.md.
```

Context-window PRISMs are not generic agent templates. They may be read for continuity, research, or source context, but must not be worn as costumes by unrelated agents. "The characters in this play are documented context windows, not roles available for impersonation." Goose's own PRISM.md is protected by this rule.

---

```yaml
id: GOOSE-PROC-0008
title: Windows UTF-8 mojibake rule
status: review
rank: 3
source: red-thread-lab/codex-notes/WINDOWS_UTF8_AND_MOJIBAKE.md (commit 4e5d232)
source_window: goose
date: 2026-05-12
provenance_label: quoted_source
retrieval_policy: when_relevant
do_not_compress: false
caution: File corruption vs display artifact — always verify with bytes, not vibes.
```

On Windows, terminal rendering is not proof of file corruption. Use `Get-Content -Encoding UTF8` or `[System.IO.File]::ReadAllText(path, [System.Text.Encoding]::UTF8)`. Run byte-pattern check for real corruption. PATCH_HUMANNESS.md was clean UTF-8; earlier mojibake was PowerShell rendering artifact. Durable note at: `red-thread-lab/codex-notes/WINDOWS_UTF8_AND_MOJIBAKE.md`
