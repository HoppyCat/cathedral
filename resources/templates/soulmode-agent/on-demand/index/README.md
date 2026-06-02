# On-Demand Index

This folder is reserved for index files, source maps, and retrieval records that sit beside on-demand patches.

The always-loaded file map remains `on-load/INDEX.md` unless the runtime is updated to load index material from this folder directly.

> **Note:** `on-demand/index/` is currently for repo organization only and is not seeded into D1. To enable D1 seeding for this folder, add `...readMarkdownFiles("on-demand/index")` to `scripts/seed-soul-files.mjs`.