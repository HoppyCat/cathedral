# Raw GitHub Retrieval Error Log

This document tracks failures when an AI window attempts to retrieve a raw GitHub file and the retrieval layer returns an error, blank result, stale result, or otherwise unusable response.

The purpose is not to assume GitHub is at fault. These notes are for comparing retrieval behavior across assistants, tools, models, networks, and fallback paths so the Cathedral memory system can become easier to debug over time.

## When to Add an Entry

Add an entry when:

- a raw GitHub URL cannot be retrieved;
- the returned content is blank, truncated, stale, malformed, or unexpectedly encoded;
- the assistant reports a cache, fetch, authorization, DNS, timeout, rate-limit, or internal tool error;
- a local fallback file has to be used instead of the raw URL.

## Prompt Format

When asking a window to retrieve a file, use both a live URL and a local fallback path when possible:

```text
First try: https://raw.githubusercontent.com/OWNER/REPO/refs/heads/BRANCH/path/to/file.ext
Fallback: [local workspace] -> path -> to -> file.ext
```

If the assistant is not already operating from the shared workspace, use:

```text
Fallback: [local path] -> Documents -> New project -> path -> to -> file.ext
```

## Entry Template

```markdown
### YYYY-MM-DD - Short Description

- Window / assistant:
- Repository:
- Raw URL attempted:
- Intended use:
- Retrieval method:
- Observed result:
- Exact error text:
- Fallback path:
- Fallback result:
- Outcome:
- Follow-up notes:
```

## Entries

### 2026-06-03 - Goldfish Bylaws Raw File Retrieval

- Window / assistant: Blackbird / Codex
- Repository: `HoppyCat/cathedral`
- Raw URL attempted: `https://raw.githubusercontent.com/HoppyCat/cathedral/refs/heads/main/red-thread-lab/workspace/goldfish-bylaws.html`
- Intended use: Read the Goldfish Society bylaws HTML and generate a clean Markdown bylaws file for the `HoppyCat/goldfish-society` repository.
- Retrieval method: Assistant raw web retrieval attempt against the GitHub raw file URL.
- Observed result: The raw URL retrieval did not return usable file content.
- Exact error text: `Failed to fetch ... Cache miss`, with an internal retrieval wrapper/error around the failed fetch.
- Fallback path: `[local workspace] -> workspace -> goldfish-bylaws.html`
- Fallback result: Local fallback file was available and readable.
- Outcome: Markdown bylaws file was generated at `goldfish-society/bylaws/goldfish-society-bylaws.md` and pushed to GitHub in commit `69fc4a3 Add Goldfish Society bylaws markdown`.
- Follow-up notes: Treat this as a retrieval-layer/cache diagnostic, not proof that the raw GitHub file was missing. Future windows should capture the most exact error string available, whether the failure happened before or after any visible content was returned, and which fallback path succeeded.
