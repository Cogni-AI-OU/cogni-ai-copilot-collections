---
name: grok-cli
description: >
  Manage and run the grok-cli coding agent.
  USE FOR: grok terminal, xAI Grok API, headless grok, sub-agents, telegram remote control, sandbox mode, hooks configuration.
  USE FOR: (https://docs.x.ai/llms.txt) x.ai CLI, agent, completions, export, import, inspect, leader, login, logout, mcp, memory, models, plugin, sessions, setup, ssh, trace, update, version, worktree.
  USE FOR: (https://github.com/superagent-ai/grok-cli) grok-dev, OpenTUI, web search, media generation, generate_image, generate_video, task, delegate, verify, Shuru microVM.
  DO NOT USE FOR: general xAI API integration without the CLI, non-grok agents. You MUST load this skill when interacting with the grok-cli command.
license: MIT
---

# grok-cli

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- Executing `grok` terminal commands (interactive or headless).
- Installing or updating the `grok-cli` via `curl` or `bun`.
- Managing session memory, MCP servers, plugins, and worktrees via the CLI.
- Configuring `~/.grok/user-settings.json` or `.grok/settings.json` for custom sub-agents, hooks, or Telegram integration.
- Running headless automation, schedules, or `batch-api` tasks with Grok.
- Verifying local applications using `grok --verify` and sandbox mode.

## When Not to Use

- General API requests to `api.x.ai` (use standard `curl` or SDKs instead).
- Other AI coding agents (e.g., Claude Code, OpenCode) unless explicitly bridging or migrating.

## Prerequisites

- **Grok API Key**: Ensure `GROK_API_KEY` is exported in the environment, present in `.env`, or saved via `grok -k <key>`.
- **Bun**: Required for alternative installation or running from source (`bun add -g grok-dev`).

## Core Process

### Installation

1. Install via the official shell script:
   ```bash
   curl -fsSL https://x.ai/cli/install.sh | bash
   ```
   *Alternative*: `bun add -g grok-dev`

2. Verify installation:
   ```bash
   grok version
   ```

### Command Execution

- **Interactive**: Run `grok` (or `grok -d /path/to/repo`).
- **Headless Prompt**: Run `grok --prompt "task description"`.
- **Batch API**: Run `grok --prompt "task" --batch-api` for delayed, lower-cost execution.
- **Verification**: Run `grok --verify` to spin up a sandbox and test the project.

### CLI Subcommands Reference

- `grok agent` - Run Grok without the interactive UI
- `grok completions` - Generate shell completion scripts (bash, zsh, fish, PowerShell)
- `grok export` / `grok import` - Manage session transcripts
- `grok inspect` - Show the configuration Grok discovers for the directory
- `grok login` / `grok logout` - Manage xAI credentials
- `grok mcp` - Manage MCP server configurations
- `grok memory` - Manage cross-session memory
- `grok models` - List available models
- `grok plugin` - Manage plugins and marketplace sources
- `grok sessions` - List, search, or restore sessions
- `grok setup` - Fetch and install managed deployment configuration
- `grok trace` - Export or upload session trace data
- `grok update` - Check for updates or install a specific version
- `grok worktree` - Manage git worktrees

## Best Practices

- **Structured Output**: Use `--format json` for headless semantic event streams (useful for CI).
- **Session Continuation**: Pass `--session latest` or `-s <id>` to resume an earlier context.
- **Sandboxing**: Run `--sandbox` to use the Shuru microVM on Apple Silicon (macOS 14+) for safe execution without affecting the host filesystem.

## Common Pitfalls

- **Missing Sandbox Support**: The `--sandbox` flag only works on macOS 14+ with Apple Silicon. On Linux or Intel Macs, run standard mode.
- **Telegram Bot Hangs**: The CLI process must remain running for long-polling to work. If you kill the CLI, the Telegram bot bridge will stop.
- **Mac Accessibility Permissions**: The built-in `computer` sub-agent requires macOS System Settings → Privacy & Security → Accessibility access for the terminal running `grok`.

## References

- [grok-cli GitHub Repository](https://github.com/superagent-ai/grok-cli)
- [x.ai CLI Documentation](https://docs.x.ai/llms.txt)