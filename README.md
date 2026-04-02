# claudeplugins

A collection of Claude Code plugins by [Irth Solutions](https://github.com/irthai).

## Plugins

### irth-dev

A gated development pipeline that builds features from work items with human approval at every stage.

**What it does:** Takes a story/ticket ID from any work item tracker and walks through a structured 4-gate workflow:

| Gate | Stage | What Happens |
|------|-------|--------------|
| 1 | Clarifying Questions | Agent asks ambiguities with default assumptions, human confirms |
| 2 | Implementation Plan | Agent presents plan, human approves before any code is written |
| 3 | Code Review | Separate review agent presents findings by severity, human accepts/rejects |
| 4 | PR Creation | Code is ready for pull request after all gates pass |

**Key features:**
- **Two specialized agents** — a dev agent that builds and a review agent that only reviews (never writes code)
- **Tracker-agnostic** — works with Azure DevOps, JIRA, or any tracker with MCP tools
- **Learning system** — captures human decisions at every gate and builds project-wide conventions over time in `dev-knowledge.md`
- **Atomic commits** — code and unit tests committed together, never `git add .`
- **Deviation rules** — auto-fixes bugs and blocking issues, stops and asks for architectural changes

**Usage:**

```
/irth:dev <story-id>
```

The plugin auto-checks for updates before each run.

## Repository Structure

This repo is organized to host multiple plugins. Each plugin lives in its own folder under `plugins/`:

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
└── README.md
```

### Adding a New Plugin

1. Create a new folder under `plugins/` (e.g., `plugins/my-plugin/`)
2. Add a `plugin.json` with name, version, description, and author
3. Add commands under `commands/` and agents under `agents/`
4. Register the plugin in `.claude-plugin/marketplace.json` by adding an entry to the `plugins` array

## Requirements

- [Claude Code](https://claude.ai/code)
- MCP tools for your work item tracker (optional — the agent will ask which tracker to use)

## Contributors

- **Shobana Sathyamurthy** — Primary contributor
- **Prady Roy**

## License

This source code is made available for viewing purposes only. See [LICENSE](LICENSE) for details.
