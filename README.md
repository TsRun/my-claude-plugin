# my-claude-plugin

Custom skills plugin for Claude Code.

## Skills

| Skill | Description |
|-------|-------------|
| `/my-workflow:commit` | Commit & push with `[TYPE] message` format (ADD, UPDATE, FIX, REMOVE) |
| `/my-workflow:rename` | Rename/tag the current session (overrides built-in) |
| `/my-workflow:delete` | Delete sessions: `noname`, `all`, or `name <name>` |
| `/my-workflow:sessions` | List all named sessions |
| `/my-workflow:doc` | Generate or update project documentation |
| `/my-workflow:fix-types` | Auto-fix all type checking errors (pyright/mypy) |

## Installation

```bash
/plugin marketplace add TsRun/my-claude-plugin
/plugin install my-workflow@my-claude-plugin
```

After installation, skills are available as `/my-workflow:commit`, `/my-workflow:rename`, etc.
