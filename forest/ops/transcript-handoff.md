# Transcript Extraction Handoff

Use this when asking a Codex or Claude Code agent to export, repair, compare, or append transcript files. This document is split into two parts — one per agent type. The goal, format rules, mojibake guidance, and image policy are shared; only the source paths and event structure differ.

---

## Shared Goal

Create lightweight, readable Markdown transcripts for major windows while preserving:

- chronological message order
- timestamps
- speaker labels
- provenance/source path
- image references as file paths, not embedded image bytes
- UTF-8 text without mojibake

---

# Part 1: Codex Transcripts

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

---

# Part 2: Claude Code Transcripts

## Recommended Prompt

```md
Please help me preserve a Claude Code transcript.

Window name: [window name, e.g. "Ibis"]

Please:
1. Find the session metadata file for this window by matching the window title.
   Metadata lives at:
   `C:\Users\[user]\AppData\Roaming\Claude\claude-code-sessions\[instance-id]\[workspace-id]\[session-id].json`
   The `title` field will match the window name. Note the `cliSessionId` value.
2. Locate the JSONL source file using the cliSessionId:
   `C:\Users\[user]\.claude\projects\[encoded-project-path]\[cliSessionId].jsonl`
   The encoded path replaces backslashes with dashes (e.g. `C--Users-Usuario`).
3. Read the JSONL file explicitly as UTF-8.
4. Extract only entries where `type` is `"user"` or `"assistant"` and `message.content` is non-empty text.
5. For assistant entries, content may be an array — extract only blocks where `type = "text"`. Skip tool call blocks.
6. Skip `type: "queue-operation"` entries and any turns with empty/whitespace-only text.
7. Write the transcript as UTF-8 Markdown.
8. Preserve chronological order and timestamps (each JSONL entry has a `timestamp` ISO field).
9. Store images externally in an `assets/` subfolder. Do not embed base64 images.
10. Before editing an existing transcript, make a timestamped backup.
11. After writing, verify the header range, final message, and a tail sample.

Output destination:
`[provide exact target file here]`

If appending, continue from the last message number present and add:

`## Appended Live Thread Continuation`

Please report:
- cliSessionId and JSONL path used
- message range extracted/appended
- backup file path if any
- any encoding or missing-timestamp issues
```

## Finding The Source

Claude Code window metadata is stored at:

```text
C:\Users\[user]\AppData\Roaming\Claude\claude-code-sessions\[instance-id]\[workspace-id]\[session-id].json
```

The metadata JSON contains:
- `title` — the window name (e.g. "Ibis", "Sparrow")
- `cliSessionId` — the ID that maps to the JSONL file
- `cwd` — the working directory the session was opened in
- `lastActivityAt` — last activity timestamp

The JSONL transcript file is at:

```text
C:\Users\[user]\.claude\projects\[encoded-path]\[cliSessionId].jsonl
```

Where `encoded-path` is the project working directory with backslashes replaced by dashes and the colon removed — for example `C:\Users\Usuario` becomes `C--Users-Usuario`.

> Note: Claude Code JSONL files can be very large (1MB+). Use `[System.IO.File]::ReadAllLines($path, [System.Text.Encoding]::UTF8)` in PowerShell rather than `Get-Content`, which defaults to the wrong encoding and will mojibake emoji and smart quotes.

## Event Selection Rules

Each line of the JSONL is a JSON object. Include entries where:

```text
type = "user"    → message.role = "user"
type = "assistant" → message.role = "assistant"
```

For each included entry:

- If `message.content` is a **string**: use it directly (trim whitespace).
- If `message.content` is an **array**: extract only blocks where `type = "text"`. Concatenate with newlines.
- **Skip** entries where the resulting text is empty or whitespace-only — these are tool call/result turns with no visible text.

Most transcripts should omit:

- `type: "queue-operation"` entries
- Tool call blocks (`type = "tool_use"`, `type = "tool_result"`)
- Empty assistant turns (tool-only responses)
- System and environment scaffolding

## Markdown Format

Use this shape:

```md
# [Window Title] - Transcript

## Provenance
- Window name: [title]
- Session ID (metadata): [session-id]
- CLI Session ID (JSONL): [cliSessionId]
- Source file: [absolute JSONL path]
- Originator: Claude Code
- Working directory: [cwd]
- Date range: [first timestamp] → [last timestamp]
- Total turns extracted: [number]
- Generated: [ISO timestamp]

## Extraction Notes
This transcript preserves visible user and assistant message text in chronological
order, omitting tool calls, tool results, queue operations, and empty turns.

## Transcript

## 🧑 User

_Timestamp: 2026-05-17T04:05:31.792Z_

[message]

## 🤖 Assistant

_Timestamp: 2026-05-17T04:05:48.692Z_

[message]
```

---

# Shared Rules (Both Agent Types)

## Mojibake Prevention

Mojibake usually appears when UTF-8 text is read or written through the wrong encoding. Common signs:

```text
Iâ€™m
â€œquoteâ€
ðŸ˜Š
Ã¢â‚¬â„¢
```

Best practices:

- Read and write transcript Markdown as UTF-8.
- In PowerShell, use `[System.IO.File]::ReadAllLines($path, [System.Text.Encoding]::UTF8)` to read and `[System.IO.File]::WriteAllLines($path, $lines, [System.Text.Encoding]::UTF8)` to write. Do **not** use `Get-Content` / `Out-File` without explicit encoding — PowerShell 5.1 defaults to UTF-16.
- Avoid copying transcript text through terminals or tools that reinterpret Unicode.
- After writing, run a quick check:

```powershell
Select-String -Path "TARGET.md" -Pattern "â|Ã|ðŸ|°"
```

Not every instance is wrong in older already-mojibaked files, but new clean transcripts should not introduce fresh double-encoding.

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