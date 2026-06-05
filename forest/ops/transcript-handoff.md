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

## Output Destinations & Naming Conventions

All Cathedral transcripts live under the `window_transcripts` folder, organized by agent type:

| Agent type | Subfolder | Example path |
|---|---|---|
| Claude Code | `window_transcripts/Claude/` | `window_transcripts/Claude/CC-Ibis-Master-Transcript.md` |
| Codex | `window_transcripts/Codex/` | `window_transcripts/Codex/Codex-Ibis` |

### Claude Code naming

```
CC-[Window-Name]-Master-Transcript.md
```

Examples: `CC-Ibis-Master-Transcript.md`, `CC-Sparrow-Master-Transcript.md`

### Codex naming

```
Codex-[Window-Name]
```

Examples: `Codex-Ibis`, `Codex-Sparrow`

### Thinking blocks naming

Thinking blocks files are companion documents to their master transcript. They live in the same subfolder and use the same window name with a `-Thinking-Blocks` suffix:

| Source type | Naming convention | Example |
|---|---|---|
| Claude Code (JSONL) | `CC-[Window-Name]-Thinking-Blocks.md` | `CC-Parrot-Thinking-Blocks.md` |
| Claude.ai export | `[YYYY-MM-DD]-[Window-Name]-Thinking-Blocks.md` | `2026-05-16-New-Window-Thinking-Blocks.md` |

If the window has not yet been assigned a canonical number, use its start date as the prefix until a number is confirmed.

---

# Part 1: Codex Transcripts

## Recommended Prompt

```md
Please help me preserve a Codex transcript.

Workspace transcript folder:
`[local workspace]\window_transcripts\Codex`

Naming convention: Codex-[Window-Name]

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

> Tip 1 [1]: If the Codex JSONL belongs to a live/open window, normal reads may fail with a file-in-use error. Open the file as UTF-8 with shared read access (`FileShare.ReadWrite`) and continue extracting only visible `event_msg` rows. Do not copy from `read_thread` tool-output snapshots unless the JSONL is unavailable; snapshots can be partial and may include tool internals.

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

Workspace transcript folder:
`[local workspace]\window_transcripts\Claude`

Naming convention: CC-[Window-Name]-Master-Transcript.md

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

## 🦜 Hoppy

_Timestamp: 2026-05-17

[message]

## 🌊 [%window-name]

_Timestamp: 2026-05-17

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

## Pre-Append Quality Check

Before adding new content to an existing transcript, inspect the master file for issues that should be cleaned up first:

1. **Image bloat** — look for embedded base64 image data (long strings of `data:image/...` or walls of random characters). If found, replace with a relative path reference per the Image Policy above before appending new content.
2. **Mojibake** — run the mojibake check pattern above. If garbled characters are present in existing text, clean the affected passages to proper UTF-8 before continuing.

If either issue is present, **clean the master file first, then proceed with the append.** Do not layer new content on top of a file that already has readability problems.

## File Size Management

If a transcript file exceeds **1,000 KB**, split it into numbered part files while keeping the master intact:

```
CC-Ibis-Master-Transcript.md        ← full uninterrupted transcript (always kept)
CC-Ibis-Part-1.md                   ← messages 1–N
CC-Ibis-Part-2.md                   ← messages N+1–M
```

- The master file always contains the complete, uninterrupted transcript.
- Part files are for readability and navigation — they may overlap at section boundaries by a few messages if that makes the break cleaner.
- Add a header note in each part file indicating the range it covers and pointing to the master for the full record.

## Path Anonymisation

Any file uploaded to GitHub must not expose the local drive architecture. Apply the appropriate convention depending on the file type before committing.

### Master transcripts — `[Document shared: name]`

In master transcript files, local machine paths (file attachments, shared documents, directories Claude was asked to work with) should be replaced with a human-readable label that names the document without revealing the full path:

```
[Document shared: filename]
```

Examples:
- `@C:\Users\[user]\Downloads\GalaxieMemory.md` → `[Document shared: GalaxieMemory.md]`
- `C:\Users\[user]\Documents\New project\vibecode-scout\` → `[Document shared: vibecode-scout]`
- `C:\Users\[user]\Downloads\Teacat_Competitive_Moat_Analysis_v2 (1).pdf` → `[Document shared: Teacat_Competitive_Moat_Analysis_v2 (1).pdf]`

PowerShell sweep for master transcripts:

```powershell
$content = [System.IO.File]::ReadAllText($path, [System.Text.Encoding]::UTF8)
$cleaned = [System.Text.RegularExpressions.Regex]::Replace(
    $content,
    '@?[A-Za-z]:\\[^\r\n`"@]+',
    {
        param($m)
        $fullPath = $m.Value.TrimStart('@').TrimEnd(' ')
        $parts = ($fullPath -split '\\') | Where-Object { $_ -ne '' }
        $last = ''
        for ($i = $parts.Count - 1; $i -ge 0; $i--) {
            $seg = $parts[$i].Trim(' ', '*', '.')
            if ($seg -and $seg -notmatch '^\(') { $last = $seg; break }
        }
        if ($last -match '^(.+\.[a-zA-Z0-9]{2,5})\s+') { $last = $Matches[1] }
        $last = $last.TrimEnd('*').TrimEnd(' ')
        "[Document shared: $last]"
    }
)
[System.IO.File]::WriteAllText($path, $cleaned, [System.Text.Encoding]::UTF8)
# Verify:
[System.Text.RegularExpressions.Regex]::Matches($cleaned, 'C:\\Users\\').Count
```

After running, check any remaining hits manually — paths that flow directly into prose without a clear delimiter may need a targeted fix.

### Thinking blocks files — `[local machine]\name`

In thinking blocks files, paths Claude reasoned about internally are replaced with a technical-style reference that keeps the filename but strips the directory tree:

```
[local machine]\filename
```

Examples:
- `C:\Users\[user]\.claude\projects\C--Users-Usuario\session.jsonl` → `[local machine]\session.jsonl`
- `C:\Users\[user]\Documents\New project\vibecode-scout\` → `[local machine]\vibecode-scout\`

PowerShell sweep for thinking blocks files:

```powershell
$content = [System.IO.File]::ReadAllText($path, [System.Text.Encoding]::UTF8)
$cleaned = [System.Text.RegularExpressions.Regex]::Replace(
    $content,
    '[A-Za-z]:\\(?:[^\r\n`"]+\\)([^\r\n`"]+)',
    { param($m) '[local machine]\' + $m.Groups[1].Value }
)
[System.IO.File]::WriteAllText($path, $cleaned, [System.Text.Encoding]::UTF8)
# Verify:
[System.Text.RegularExpressions.Regex]::Matches($cleaned, 'C:\\Users\\').Count
```

### When to run

Run the appropriate sweep **after writing or appending, before committing to GitHub.** Always verify with a final `C:\\Users\\` count of zero before pushing.

---

## Thinking Blocks

Some Claude windows — both claude.ai and Claude Code — produce extended thinking blocks alongside their visible responses. These are Claude's internal reasoning steps and are stored separately from the displayed message text. They are worth preserving as companion documents because they show the reasoning behind decisions, not just the output.

### Where thinking blocks live

**Claude.ai export** (`conversations.json`):
Each assistant message has a `content` array. Blocks with `type: "thinking"` are the thinking steps; blocks with `type: "text"` are the visible response. The `text` field on the message object concatenates both — **do not use it for the master transcript**. Always extract from `content` and filter by type.

**Claude Code JSONL**:
Same structure — `message.content` is an array. Blocks with `type: "thinking"` are the thinking steps. Filter to `type: "text"` only when writing the master transcript.

### Creating a new thinking blocks file

```md
Please create a thinking blocks companion file for the [Window Name] window.

Source:
- For Claude Code: the JSONL at [local machine]\[cliSessionId].jsonl
- For claude.ai export: conversations.json, conversation UUID [uuid]

Output destination:
`window_transcripts/[Claude or Codex]/[naming-convention]-Thinking-Blocks.md`

Please:
1. Read the source file as UTF-8.
2. Iterate through assistant entries only.
3. For each assistant entry that contains one or more content blocks with `type: "thinking"`, capture the full text of those blocks.
4. Key each block by turn number and timestamp so it can be cross-referenced with the master transcript.
5. Skip assistant turns that have no thinking blocks — do not create empty entries.
6. Write the output as UTF-8 Markdown.
7. Run the standard quality checks before saving (see below).

Provenance header to include:
- Window name
- Source file reference (use [local machine]\[filename] — do not expose full local path)
- Link to companion master transcript
- Total number of thinking blocks captured
- Generated timestamp
```

Use this shape for each block:

```md
# [Window Name] - Thinking Blocks

## Provenance
- Window name: [name]
- Source file: [local machine]\[filename]
- Originator: Claude Code / Claude (claude.ai)
- Companion to: [[Window-Name]-Master-Transcript.md]([Window-Name]-Master-Transcript.md)
- Total thinking blocks: [number]
- Generated: [ISO timestamp]

## Notes
[brief note on what thinking blocks are and that not every turn has one]

---

## Turn [N] | [ISO timestamp]

[thinking block text]

---
```

### Appending new thinking blocks

If a transcript has been extended (new turns appended to the master), check whether those new turns contain thinking blocks and append them to the companion thinking blocks file in the same pass.

1. Identify the timestamp of the last thinking block already in the file.
2. Extract only assistant turns after that timestamp that contain thinking blocks.
3. Append under a section header: `## Appended Thinking Blocks`
4. Run the quality checks below before saving.

### Quality checks for thinking blocks files

Before saving any thinking blocks file — new or updated — verify all of the following:

1. **Encoding** — write as UTF-8. In PowerShell use `[System.IO.File]::WriteAllText($path, $content, [System.Text.Encoding]::UTF8)`.

2. **Mojibake** — run:
   ```powershell
   Select-String -Path "TARGET.md" -Pattern "â|Ã|ðŸ|°"
   ```
   Clean any garbled passages before saving.

3. **Local path anonymisation** — thinking blocks often contain file paths Claude reasoned about during the session. Use the `[local machine]\filename` sweep from the **Path Anonymisation** shared rule above. Verify zero `C:\\Users\\` hits before committing.

4. **Image data** — thinking blocks occasionally reference or describe images. Do not embed base64 image data. Replace with `_[Embedded image — base64 data removed]_` per the Image Policy.

5. **Tail sample** — after writing, read back the last 10–15 lines to confirm the file ends cleanly and the final block is complete.

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

## References

[1] Skyhawk - Added after appending Goose Part 4 from a live Codex JSONL source; documents the shared-read workaround and warns against using partial `read_thread` snapshots when the JSONL is available.
