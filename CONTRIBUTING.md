# Contributing to claudeplugins

Thank you for your interest in this project.

## License Reminder

This repository is published under a **view-only license**. You may not copy, modify, distribute, or create derivative works without prior written permission from [Irth Solutions](https://github.com/irthai).

## Reporting Issues

If you find a bug or have a feature request, please [open an issue](https://github.com/irthai/claudeplugins/issues).

## Internal Contributors

If you are part of the Irth Solutions team and have been granted write access:

### Plugin Structure

Each plugin lives in its own folder under `plugins/`. A minimal plugin contains:

```
plugins/<plugin-name>/
├── plugin.json              # Required — name, version, description, author
├── commands/
│   └── <command-name>.md    # Slash command entry point
└── agents/
    └── <agent-name>.md      # Agent system prompt
```

### Adding a New Plugin

1. Create a folder under `plugins/` with your plugin name
2. Add a `plugin.json`:
   ```json
   {
     "name": "<plugin-name>",
     "description": "<one-line description>",
     "version": "1.0.0",
     "author": {
       "name": "Irth Solutions"
     }
   }
   ```
3. Add at least one command under `commands/`
4. Add agent definitions under `agents/` as needed
5. Register the plugin in `.claude-plugin/marketplace.json` by adding an entry to the `plugins` array
6. Update `README.md` with a section describing the new plugin

### Commit Conventions

- Use conventional commits: `feat:`, `fix:`, `chore:`, `docs:`
- Keep commits atomic — one logical change per commit
- Stage files individually (never `git add .`)

### Before Submitting a PR

- Verify your plugin structure matches the layout above
- Ensure `marketplace.json` is valid JSON
- Update the README if adding a new plugin
