# Transcript Extraction Handoff

Use this when asking a Codex window to export, repair, compare, or append transcript files.

## Goal

Create lightweight, readable Markdown transcripts for major windows while preserving:

- chronological message order
- timestamps
- speaker labels
- provenance/source path
- image references as file paths, not embedded image bytes
- UTF-8 text without mojibake

## Recommended Prompt

```md
Please help me preserve a Codex transcript.

Workspace transcript folder:
`[local workspace]\window_transcripts\Codex`

Please:
1. Find the relevant Codex session/thread by title or session id.
2. Prefer the local Codex JSONL source file when available, because it includes timestamps.
3. Extract only visible user/assistant messages.
4. Do not include hidden system/developer prompts, token accounting, task events, tool calls, or duplicate `response_item` copies when an `event_msg` copy already exists.
5. Write the transcript as UTF-8 Markdown.
6. Preserve chronological numbering and timestamps.
7. Store images externally in an `assets/` subfolder and link them by relative path. Do not embed base64 images.
8. Before editing an existing transcript, make a timestamped backup.
9. After writing, verify the header range, final message number, and a tail sample.

Output destination:
`[provide exact target file here]`

If appending to an existing part, continue from the last message number already present and add a small section header such as:

`## Appended Live Thread Continuation`

Please report:
- source JSONL path or thread id
- message range extracted/appended
- backup file path if any
- any encoding or missing-timestamp issues
```

## Finding The Source

Codex Desktop sessions are usually stored under:

```text
[local workspace]\.codex\sessions\YYYY\MM\DD\
```

The source file usually looks like:

```text
rollout-YYYY-MM-DDTHH-MM-SS-[thread-id].jsonl
```

If the thread title is known, use the Codex thread tools first:

- `list_threads` with the title query
- `read_thread` for recent turns

Then use the thread id to find or confirm the matching JSONL path if a full transcript with timestamps is needed.

## Event Selection Rules

Prefer JSONL rows where:

```text
type = event_msg
payload.type = user_message
payload.type = agent_message
```

Avoid duplicating assistant messages from both:

```text
event_msg.payload.type = agent_message
response_item.payload.type = message
```

Most transcripts should omit:

- `token_count`
- `task_complete`
- `response_item` duplicates
- tool call/event internals
- hidden system/developer/environment messages

## Markdown Format

Use this shape:

```md
# [Window Title] - Raw Transcript

## Provenance
- Source session id: [id]
- Source file: [absolute JSONL path]
- Originator: Codex Desktop
- Initial cwd: [if known]
- Thread index names:
  - [title(s)]
- Total extracted message count in source at generation: [number]
- Message range: [start-end]
- Generated: [ISO timestamp]

## Extraction Notes
This transcript preserves visible user and assistant message text in chronological order, while omitting hidden system/developer instructions, tool calls, token accounting, task events, and environment-context scaffolding.

## Transcript

### 1. Hoppy

_Timestamp: 2026-05-30T00:00:00.000Z_

[message]

### 2. Codex / [Window Name]

_Timestamp: 2026-05-30T00:00:00.000Z_

[message]
```

## Mojibake Prevention

Mojibake usually appears when UTF-8 text is read or written through the wrong encoding. Common signs:

```text
Iâ€™m
â€œquoteâ€
ðŸ˜Š
Ã¢â‚¬â„¢
Ã°Å¸
```

Best practices:

- Read and write transcript Markdown as UTF-8.
- In PowerShell, prefer explicit `-Encoding utf8` when writing.
- Avoid copying transcript text through terminals or tools that reinterpret Unicode.
- If the JSONL itself is already mojibaked, preserve it only if you are making a raw evidence copy; otherwise make a cleaned Markdown transcript from the best source available.
- After writing, run a quick search for likely mojibake markers:

```powershell
Select-String -Path "TARGET.md" -Pattern "â|Ã|ðŸ|�"
```

Not every `ðŸ` is necessarily wrong in older already-mojibaked files, but new clean transcripts should not introduce fresh double-encoding like `Ã¢â‚¬â„¢`.

## Image Policy

Do not embed image bytes in the transcript.

Use:

```md
![Embedded image 1](assets/window-name-images/image-01.png)
```

Or, when preserving only provenance:

```md
Image referenced:
`assets/window-name-images/image-01.png`

Why it mattered:
[brief note]
```

## Comparison Checks

When comparing a before/after transcript:

- Compare message numbers and timestamps first.
- Unique header lines do not count as missing conversation.
- Unique image reference lines may be expected if one file extracted images and another did not.
- Report whether missing material is actual conversation content or only metadata.

## Final Report Template

```md
Done.

Source:
`[source]`

Destination:
`[destination]`

Message range:
`[start-end]`

Backup:
`[backup path or none]`

Notes:
- [encoding status]
- [whether timestamps were preserved]
- [anything omitted intentionally]
```

