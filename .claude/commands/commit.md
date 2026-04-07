---
name: commit
description: Commit and push all current changes. Use when the user wants to commit their work.
argument-hint: [commit context] [--no-push]
---

Commit and push all current changes. Follow these steps exactly:

1. Run `git status` and `git diff` in parallel to see all changes
2. Stage everything with `git add -A` (all modified, deleted, and untracked files — .gitignore already handles exclusions)
3. Write a commit message following this format strictly:
   - `[TYPE] short description in english`
   - TYPE is one of: ADD, UPDATE, FIX, REMOVE
   - One line only
   - Do NOT add Co-Authored-By or any footer
4. Commit using a HEREDOC for the message
5. Push to remote immediately after commit UNLESS arguments contain "--no-push"

If there are no changes, say so and stop.
If the user provided arguments, use them as context for the commit message (ignore flags like --no-push from the message): $ARGUMENTS
