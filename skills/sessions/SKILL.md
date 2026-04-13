---
name: sessions
description: List all named conversation sessions. Use when the user wants to see their saved/named sessions.
---

List all named sessions for the current project.

## Steps

1. Read `~/.claude/projects/<project-slug>/sessions-index.json`.
2. If the file doesn't exist or is empty, say "No named sessions found."
3. For each entry, check if the JSONL file still exists. Remove stale entries and write back the index.
4. Print a table: `name | color | sessionId (short) | date named`
5. If no named sessions remain after cleanup, say so.

## Rules
- The sessions index file path is: `~/.claude/projects/<project-slug>/sessions-index.json` where `<project-slug>` matches the current project directory name (e.g., `-home-mathisserrier-Project-e-learning`).
- The index is a JSON array of objects.
