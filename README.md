# tsrun-toolkit

Dev workflow skills and MCP integrations for Claude Code.

## Skills

| Skill | Description |
|-------|-------------|
| `/tsrun-toolkit:commit` | Commit & push with `[TYPE] message` format (ADD, UPDATE, FIX, REMOVE) |
| `/tsrun-toolkit:doc` | Generate or update project documentation |
| `/tsrun-toolkit:fix-types` | Auto-fix all type checking errors (pyright/mypy) |

## MCP Servers

| Server | Description |
|--------|-------------|
| **Obsidian** | Read/write your Obsidian vault via Local REST API |
| **Playwright** | Browser automation and E2E testing (by Microsoft) |

## Installation

```bash
/plugin marketplace add TsRun/tsrun-toolkit
/plugin install tsrun-toolkit@tsrun-toolkit
```

On install you'll be prompted for Obsidian settings (port and API key). These are optional if you don't use Obsidian.
