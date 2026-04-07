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

Clone this repo into your project's `.claude/commands/` directory:

```bash
# From your project root
git clone https://github.com/TsRun/my-claude-plugin.git /tmp/my-claude-plugin
mkdir -p .claude/commands
cp /tmp/my-claude-plugin/.claude/commands/*.md .claude/commands/
rm -rf /tmp/my-claude-plugin
```

Or for global commands (available in all projects):

```bash
git clone https://github.com/TsRun/my-claude-plugin.git /tmp/my-claude-plugin
mkdir -p ~/.claude/commands
cp /tmp/my-claude-plugin/.claude/commands/*.md ~/.claude/commands/
rm -rf /tmp/my-claude-plugin
```

After installation, the commands are available as `/commit`, `/rename`, `/delete`, `/sessions`, `/doc`, and `/fix-types` in Claude Code.
