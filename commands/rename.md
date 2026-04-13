---
name: rename
description: Rename the current conversation session. Overrides the built-in /rename command. Use when the user wants to rename or re-tag the current session.
argument-hint: new-name [--color color]
---

Rename the current conversation session. Arguments: $ARGUMENTS

## Steps

1. Read `~/.claude/projects/<project-slug>/sessions-index.json` (create if missing).
2. Find the current session ID by checking which JSONL file in the project dir is most recently modified.
3. **If no name is provided in arguments**: auto-generate one by reading the first few user messages from the session JSONL file and summarizing the topic in 2-3 lowercase words joined by hyphens (e.g., `kube-deploy-fix`, `auth-refactor`). Keep it short and descriptive.
4. Upsert an entry: `{ "sessionId": "<id>", "name": "<new-name>", "color": "<color>", "namedAt": "<ISO timestamp>" }`
5. Write back the index.
6. **Persist in Claude Code's native format** by appending these JSON lines to the session's JSONL file (`~/.claude/projects/<project-slug>/<sessionId>.jsonl`):
   ```
   {"type":"custom-title","customTitle":"<new-name>","sessionId":"<sessionId>"}
   {"type":"agent-name","agentName":"<new-name>","sessionId":"<sessionId>"}
   {"type":"tag","tag":"<color>","sessionId":"<sessionId>"}
   {"type":"agent-color","agentColor":"<color>","sessionId":"<sessionId>"}
   ```
   Use: `printf '%s\n' '<line1>' '<line2>' '<line3>' '<line4>' >> <file>`
7. **Color selection**:
   - Available colors: `red`, `blue`, `green`, `yellow`, `purple`, `orange`, `pink`, `cyan`
   - If `--color <color>` is provided, use that color.
   - If the session already has a color in the index, keep it.
   - Otherwise, auto-pick a color that no other named session in the index is using. If all colors are taken, cycle from the beginning.

## Rules
- The sessions index file path is: `~/.claude/projects/<project-slug>/sessions-index.json` where `<project-slug>` matches the current project directory name (e.g., `-home-mathisserrier-Project-e-learning`).
- The index is a JSON array of objects.
- Color order for auto-pick: red, blue, green, yellow, purple, orange, pink, cyan.
