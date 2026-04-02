# CLAUDE.md — claudeplugins

## What is this repo?

A Claude Code plugin marketplace repository by [Irth Solutions](https://github.com/irthai). It hosts plugins that extend Claude Code with specialized development workflows.

## Work Item Tracker

- **Tracker:** GitHub Issues
- **Repo:** irthai/claudeplugins

## Repository Structure

```
claudeplugins/
├── .claude-plugin/
│   └── marketplace.json        # Plugin registry — lists all plugins in this repo
├── plugins/
│   └── <plugin-name>/
│       ├── plugin.json          # Plugin metadata (name, version, description)
│       ├── commands/            # Slash commands (entry points)
│       │   └── <command>.md
│       └── agents/              # Agent definitions (system prompts)
│           └── <agent>.md
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└── CLAUDE.md
```

## Current Plugins

| Plugin | Command | Description |
|--------|---------|-------------|
| irth-dev | `/irth:dev <story-id>` | 4-gate development pipeline with human approval at every stage |

## Conventions

- **Commit style:** Conventional commits — `feat:`, `fix:`, `chore:`, `docs:`
- **Commits:** Atomic — one logical change per commit. Stage files individually, never `git add .`
- **Default branch:** `main`
- **License:** View-only. No copying, modifying, or distributing without permission from Irth Solutions.

## Adding a New Plugin

1. Create a folder under `plugins/` with the plugin name
2. Add `plugin.json` with name, version, description, author
3. Add commands under `commands/` and agents under `agents/`
4. Register in `.claude-plugin/marketplace.json`
5. Update `README.md` with a section describing the new plugin
