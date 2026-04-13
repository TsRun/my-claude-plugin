---
name: delete
description: Delete conversation sessions. Supports deleting unnamed sessions, all sessions, or a specific named session. Use when the user wants to clean up or remove sessions.
argument-hint: [noname|all|name session-name]
---

Delete conversation sessions. Parse the arguments to determine the sub-action: $ARGUMENTS

## Sub-actions

### `noname` (or no arguments)
Delete all UNNAMED conversations (keep named ones + current):
1. Read `~/.claude/projects/<project-slug>/sessions-index.json` to get the set of named session IDs.
2. List all `*.jsonl` files in the project directory.
3. Delete any JSONL + matching directory that is NOT in the named set AND is NOT the current session.
4. Report how many were deleted.

### `all`
Delete ALL conversations except the current one:
1. List all `*.jsonl` files in the project directory.
2. Delete every JSONL + matching directory that is NOT the current session.
3. Clear `sessions-index.json` (keep only the current session's entry if it is named).
4. Report how many were deleted.

### `name <session-name>`
Delete a specific named session:
1. Find the session by name in `sessions-index.json`.
2. Delete the JSONL file and matching directory.
3. Remove the entry from the index and write it back.
4. Confirm deletion.

## Rules
- The sessions index file path is: `~/.claude/projects/<project-slug>/sessions-index.json` where `<project-slug>` matches the current project directory name (e.g., `-home-mathisserrier-Project-e-learning`).
- **Always preserve the current session** — never delete it, even with `delete all`.
- Find the current session ID by checking which JSONL file in the project dir is most recently modified.
- The index is a JSON array of objects.
- If no arguments provided, default to `noname`.
