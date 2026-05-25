---
name: gemini-cli-docs
description: 'USE FOR: Reading, searching, or referencing Gemini CLI documentation (docs directory, CLI reference, tutorials, hooks, extensions, tools, configuration, MCP, and IDE integration guides). DO NOT USE FOR: Operating the Gemini CLI itself, writing Gemini CLI plugins or extensions, or setting up Gemini authentication and credentials. You MUST load this skill when asked to read, search, or retrieve Gemini CLI documentation.'
license: MIT
---

# Gemini CLI Docs

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- **Documentation Lookup**: Finding specific Gemini CLI doc pages for features, CLI commands, or configuration.
- **Tutorial Reference**: Fetching how-to guides on automation, MCP setup, skills, shell commands, and memory management.
- **Architecture Reference**: Looking up hooks/extensions specs, tool definitions, IDE companion spec, or policy engine docs.

## When Not to Use

- **Running Gemini CLI Commands**: Interacting with a live `gemini` CLI session — use direct CLI execution instead.
- **Writing Extensions/Skills**: Authoring new Gemini CLI plugins, hooks, or agent skills — use the appropriate development skill.

## Core Process

1. **Identify the Topic**: Determine the docs area (CLI reference, hooks, extensions, tools, tutorials, get-started, admin, reference, or core).
2. **Fetch Doc Content**: Build the URL path using the pattern:
   ```text
   https://raw.githubusercontent.com/google-gemini/gemini-cli/main/docs/<area>/<filename>
   ```
3. **Process Content**: Extract relevant information to answer the query.

Use `webfetch` or equivalent to retrieve raw markdown files.

## Docs Path Reference

`docs/<area>/` — sub-directories and typical files:

| Area | Key Files |
| --- | --- |
| `(root)` | CONTRIBUTING.md, index.md, local-development.md, npm.md, releases.md |
| `admin/` | enterprise-controls.md |
| `cli/` | CLI reference, skills, model-routing, sandbox, session-management, plan-mode, generation-settings, themes, system-prompt, token-caching, trusted-folders, and more |
| `cli/tutorials/` | automation.md, mcp-setup.md, shell-commands.md, skills-getting-started.md, memory-management.md, task-planning.md, web-tools.md |
| `core/` | gemma-setup.md, local-model-routing.md, remote-agents.md, subagents.md |
| `extensions/` | best-practices.md, reference.md, releasing.md, writing-extensions.md |
| `get-started/` | authentication.mdx, installation.mdx, gemini-3.md |
| `hooks/` | best-practices.md, reference.md, writing-hooks.md |
| `ide-integration/` | ide-companion-spec.md |
| `reference/` | commands.md, configuration.md, tools.md, keyboard-shortcuts.md, policy-engine.md |
| `resources/` | faq.md, troubleshooting.md, quota-and-pricing.md, uninstall.md |
| `tools/` | activate-skill.md, file-system.md, mcp-server.md, memory.md, shell.md, web-fetch.md, planning.md, and more |

## References

- [Gemini CLI Repository](https://github.com/google-gemini/gemini-cli)
