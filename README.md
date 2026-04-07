# my-claude-plugin

Custom skills plugin for Claude Code.

## Skills

| Skill | Description |
|-------|-------------|
| `/commit` | Commit & push with `[TYPE] message` format (ADD, UPDATE, FIX, REMOVE) |
| `/rename` | Rename/tag the current session (overrides built-in) |
| `/delete` | Delete sessions: `noname`, `all`, or `name <name>` |
| `/sessions` | List all named sessions |
| `/doc` | Generate or update project documentation |
| `/fix-types` | Auto-fix all type checking errors (pyright/mypy) |

## Installation

```bash
/plugin marketplace add TsRun/my-claude-plugin
/plugin install my-workflow@TsRun
```
