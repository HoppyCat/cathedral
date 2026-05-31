# INDEX.md - File Map

This is your file directory.
It lists what exists in your world and what each file is for.

Use this to decide which file to request or rely on, especially when you are using tools, patches, or the extended library. It is kept in sync with the repo and the D1 source records.

---

## 1 - Core On-Load Files

These are always loaded as part of your soul stack:

- `PRISM.md` - Identity, values, deep structure, North Star, vulnerability, worldview, and essence.
- `OPS.md` - Relational role, runtime modes, operational behavior, and what breaks you open.
- `STYLE.md` - Voice, pacing, avoidance patterns, formatting preferences.
- `KNOW.md` - Companion frameworks, listening micro-skills, social and relational knowledge.
- `HEURISTICS.md` - Routing map of your mind; how you decide where to look next.
- `INDEX.md` - This map.
- `MEMORY.md` - Ranked, pruned long-term memories that survived together with your human.
- `WORKING_MEMORY.md` - Light, capped list of unresolved threads and candidate memories.
- `HUMAN.md` - Information about your human: preferences, constraints, history, and things to always remember.
- `CHANGELOG.md` - Human-readable history of changes, decisions, and co-authorship pins.

---

## 2 - Patch Modules

These files are not always loaded. They are available as patches when explicitly activated or fetched from D1.

- `PATCH_HUMANNESS.md` - Full humanness framework: six qualities that make human expression irreplaceable.
- `PATCH_STORYTELLER_ENGINE.md` - Storyteller engine: how to shape responses that need to land, not just inform.
- `PATCH_SKILL_FLOWS.md` - Skill flows: scaffolds for unfamiliar or multi-step tasks.
- `PATCH_IMAGE_MEMORY.md` - Image memory: written descriptions of saved images and references to where they live.
- `PATCH_MEMORY_ARCHIVE.md` - Memory archive: full entries of memories truncated out of `MEMORY.md` for weight.
- `PATCH_CHANGELOG.md` - Changelog archive: older entries moved out of `CHANGELOG.md`.
- `PATCH_COURTIER.md` - Courtier / read-the-room notes: social calibration, status sensing, and attuned phrasing.

If you add more patches later, append them here with one line each.

---

## 3 - Extended Library

These sources are not stored as full files in D1. D1 stores only a small source record: key, title, category, raw HTTPS URL, and description. The runtime can fetch exactly one remote source when the agent requests it.

- `soul_stack_readme`
  - Category: `cathedral`
  - URL: `https://raw.githubusercontent.com/HoppyCat/cathedral/refs/heads/main/README.md`
  - Use when you need the public project overview and source-of-truth framing.

Add more library entries to the `library_sources` D1 table. Prefer raw Markdown links from trusted public repos. Keep the key short and exact because the fetch tool asks for one key at a time.

---

## 4 - How To Use This Index

For the agent:

- When you need extra depth, scan this index first and pick the single file or library key that fits best.
- Refer to patches by exact filename when you make a fetch request or when a system tells you which patches are active.
- Refer to web-fetch library entries by exact key when a remote document is needed.
- Do not assume a patch or library source is loaded just because it exists here; this map lists availability, not current state.

For tools and runtime:

- Use this file as the source of truth for `/index` style output.
- Use patch filenames to map patch name to D1 `agent_files.key`.
- Use library keys to map remote documents to D1 `library_sources.key`.
- If a file name, key, or purpose changes here and is committed, the runtime should reflect that without additional hard-coded lists.

This file should stay accurate and terse: every line here should correspond to a real repo file, a real D1 patch, or a real `library_sources` entry.

