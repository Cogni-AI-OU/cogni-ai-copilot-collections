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

An open-source coding agent for the Grok API.

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

**Environment (good for CI):**

```bash
export GROK_API_KEY=your_key_here
```

`**.env**` in the project (see `.env.example` if present):

```bash
GROK_API_KEY=your_key_here
```

**CLI once:**

```bash
grok -k your_key_here
```

**Saved in user settings** — `~/.grok/user-settings.json`:

```json
{ "apiKey": "your_key_here" }
```

Optional `**subAgents**` — custom foreground sub-agents. Each entry needs `**name**`, `**model**`, and `**instruction**`:

```json
{
  "subAgents": [
    {
      "name": "security-review",
      "model": "grok-4.3",
      "instruction": "Prioritize security implications and suggest concrete fixes."
    }
  ]
}
```

Names cannot be `general`, `explore`, `vision`, `verify`, or `computer` because those are reserved for the built-in sub-agents.

Optional: `**GROK_BASE_URL**` (default `https://api.x.ai/v1`), `**GROK_MODEL**`, `**GROK_MAX_TOKENS**`.

## Core Process

### Installation

1. Install via the official shell script:
   ```bash
   curl -fsSL https://x.ai/cli/install.sh | bash
   ```
   *Alternative*: `bun add -g grok-dev`
   *Alternative from GitHub*: `curl -fsSL https://raw.githubusercontent.com/superagent-ai/grok-cli/main/install.sh | bash`

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
- `grok worktree` - Manage Git worktrees
## Run it

**Interactive (default)** — launches the OpenTUI coding agent:

```bash
grok
```

### Supported terminals

For the most reliable interactive OpenTUI experience, use a modern terminal emulator. We currently document and recommend:

- **WezTerm** (cross-platform)
- **Alacritty** (cross-platform)
- **Ghostty** (macOS and Linux)
- **Kitty** (macOS and Linux)

Other modern terminals may work, but these are the terminal apps we currently recommend and document for interactive use.

**Pick a project directory:**

```bash
grok -d /path/to/your/repo
```

**Headless** — one prompt, then exit (scripts, CI, automation):

```bash
grok --prompt "run the test suite and summarize failures"
grok -p "show me package.json" --directory /path/to/project
grok --prompt "refactor X" --max-tool-rounds 30
grok --prompt "summarize the repo state" --format json
grok --prompt "review the repo overnight" --batch-api
grok --verify
```

`--batch-api` uses xAI's Batch API for lower-cost unattended runs. It is a good
fit for scripts, CI, schedules, and other non-interactive workflows where a
delayed result is fine.

**Continue a saved session:**

```bash
grok --session latest
grok -s <session-id>
```

Works in interactive mode too—same flag.

**Structured headless output:**

```bash
grok --prompt "summarize the repo state" --format json
```

`--format json` emits a newline-delimited JSON event stream instead of the
default human-readable text output. Events are semantic, step-level records such
as `step_start`, `text`, `tool_use`, `step_finish`, and `error`.

### Computer sub-agent

Grok ships a built-in `**computer**` sub-agent backed by `[agent-desktop](https://github.com/lahfir/agent-desktop)` for host desktop automation on macOS.

Ask for it in natural language, for example:

```bash
grok "Use the computer sub-agent to take a screenshot of my host desktop and tell me what is open."
grok "Use the computer sub-agent to launch Google Chrome, snapshot the UI, and tell me which refs correspond to the address bar and tabs."
```

Notes:

- Screenshots are saved under `**.grok/computer/**` by default.
- The primary workflow is **snapshot -> refs -> action -> snapshot** using `agent-desktop` accessibility snapshots and stable refs like `@e1`.
- `computer_screenshot` is available for visual confirmation, but the preferred path is `computer_snapshot` plus ref-based actions such as `computer_click`, `computer_type`, and `computer_scroll`.
- macOS requires **System Settings → Privacy & Security → Accessibility** access for the terminal app running `grok`.
- `agent-desktop` currently targets **macOS**.
- If Bun blocks the native binary download during install, run:

```bash
node ./node_modules/agent-desktop/scripts/postinstall.js
```

### Scheduling

Schedules let Grok run a headless prompt on a recurring schedule or once. Ask
for it in natural language, for example:

```text
Create a schedule named daily-changelog-update that runs every weekday at 9am
and updates CHANGELOG.md from the latest merged commits.
```

Recurring schedules require the background daemon:

```bash
grok daemon --background
```

Use `/schedule` in the TUI to browse saved schedules. One-time schedules start
immediately in the background; recurring schedules keep running as long as the
daemon is active.

**List Grok models and pricing hints:**

```bash
grok models
```

**Pass an opening message without another prompt:**

```bash
grok fix the flaky test in src/foo.test.ts
```

**Generate images or short videos from chat:**

```bash
grok "Generate a retro-futuristic logo for my CLI called Grok Forge"
grok "Edit ./assets/hero.png into a watercolor poster"
grok "Animate ./assets/cover.jpg into a 6 second cinematic push-in"
```

Image and video generation are exposed as agent tools inside normal chat sessions.
You keep using a text model for the session, and Grok saves generated media under
`.grok/generated-media/` by default unless you ask for a specific output path.

---

## What you actually get


| Thing                             | What it means                                                                                                                                                                                                              |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Built for the Grok API**        | Defaults tuned for the xAI API; models like `grok-4.3`, `grok-4.20-non-reasoning`, `grok-4.20-multi-agent-0309`, plus current flagship and multi-agent variants—run `grok models` for the full menu.                       |
| **X + web search**                | `**search_x`** and `**search_web`** tools—live posts and docs without pretending the internet stopped in 2023.                                                                                                             |
| **Media generation**              | Built-in `**generate_image`** and `**generate_video`** tools for text-to-image, image editing, text-to-video, and image-to-video flows. Generated files are saved locally so you can reuse them after the xAI URLs expire. |
| **Sub-agents (default behavior)** | Foreground `**task`** delegation (e.g. explore, general, or computer) plus background `**delegate`** for read-only deep dives—parallelize like you mean it.                                                                |
| **Verify**                        | `**/verify`** or `**--verify`** — inspects your app, builds, tests, boots it, and runs browser smoke checks in a sandboxed environment. Screenshots and video included.                                                    |
| **Computer use**                  | Built-in `**computer`** sub-agent for host desktop automation via `**agent-desktop`**. It prefers semantic accessibility snapshots and stable refs, with screenshots saved under `**.grok/computer/**` when requested.     |
| **Custom sub-agents**             | Define named agents with `**subAgents`** in `**~/.grok/user-settings.json`** and manage them from the TUI with `**/agents**`.                                                                                              |
| **Remote control**                | Pair **Telegram** from the TUI (`/remote-control` → Telegram): DM your bot, `**/pair`**, approve the code in-terminal. Keep the CLI running while you ping it from your phone.                                             |
| **No “mystery meat” UI**          | OpenTUI React terminal UI—fast, keyboard-driven, not whatever glitchy thing you’re thinking of.                                                                                                                            |
| **Skills**                        | Agent Skills under `**.agents/skills/<name>/SKILL.md`** (project) or `**~/.agents/skills/`** (user). Use `**/skills**` in the TUI to list what’s installed.                                                                |
| **MCPs**                          | Extend with Model Context Protocol servers—configure via `**/mcps`** in the TUI or `**.grok/settings.json`** (`mcpServers`).                                                                                               |
| **Sessions**                      | Conversations persist; `**--session latest`** picks up where you left off.                                                                                                                                                 |
| **Headless**                      | `**--prompt`** / `**-p`** for non-interactive runs—pipe it, script it, bench it.                                                                                                                                           |
| **Hackable**                      | TypeScript, clear agent loop, bash-first tools—fork it, shamelessly.                                                                                                                                                       |

## Telegram (remote control) — short version

1. Create a bot with [@BotFather](https://t.me/BotFather), copy the token.
2. Set `**TELEGRAM_BOT_TOKEN**` or add `**telegram.botToken**` in `~/.grok/user-settings.json` (the TUI `**/remote-control**` flow can save it).
3. Start `**grok**`, open `**/remote-control**` → **Telegram** if needed, then in Telegram DM your bot: `**/pair`**, enter the **6-character code** in the terminal when asked.
4. First user must be approved once; after that, it’s remembered. **Keep the CLI process running** while you use the bot (long polling lives in that process).

### Voice & audio messages

Send a voice note or audio attachment in Telegram and Grok will transcribe it with the **Grok Speech-to-Text API** (`POST https://api.x.ai/v1/stt`) before passing the text to the agent. The endpoint accepts Telegram's OGG/Opus voice notes and common audio containers (MP3, WAV, M4A, FLAC, AAC) directly — no local model download, `whisper-cli`, or `ffmpeg` required.

#### Prerequisites

- A valid `GROK_API_KEY` (the same key used for the agent). Transcription reuses the CLI's `apiKey` / `baseURL` resolution, so if the agent can reach xAI, transcription will too.

#### Configure in `~/.grok/user-settings.json`

```json
{
  "telegram": {
    "botToken": "YOUR_BOT_TOKEN",
    "audioInput": {
      "enabled": true,
      "language": "en"
    }
  }
}
```


| Setting    | Default | Description                                                                                                           |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------- |
| `enabled`  | `true`  | Set to `false` to ignore voice/audio messages entirely.                                                               |
| `language` | `en`    | Language code forwarded to `/v1/stt`. Enables Inverse Text Normalization (numbers, currencies, units → written form). |

Optional headless flow when you do not want the TUI open:

```bash
grok telegram-bridge
```

Treat the bot token like a password.

---

## Hooks

Hooks execute shell commands at key agent lifecycle events — enforce policies, run linters, trigger tests, or log activity.

Configure in `~/.grok/user-settings.json`:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "bash",
        "hooks": [
          {
            "type": "command",
            "command": "./scripts/lint-before-edit.sh",
            "timeout": 10
          }
        ]
      }
    ]
  }
}
```

Hook commands receive JSON on **stdin** (event details) and can return JSON on **stdout**. Exit code `0` = success, `2` = block the action, other = non-blocking error.

**Supported events:** `PreToolUse`, `PostToolUse`, `PostToolUseFailure`, `UserPromptSubmit`, `SessionStart`, `SessionEnd`, `Stop`, `StopFailure`, `SubagentStart`, `SubagentStop`, `TaskCreated`, `TaskCompleted`, `PreCompact`, `PostCompact`, `Notification`, `InstructionsLoaded`, `CwdChanged`.

## Sandbox

Grok CLI can run shell commands inside a [Shuru](https://github.com/superhq-ai/shuru) microVM sandbox so the agent can't touch your host filesystem or network.

**Requires macOS 14+ on Apple Silicon.**

Enable it with `--sandbox` on the CLI, or toggle it from the TUI with `/sandbox`.

On the first interactive run in a new directory, Grok asks whether to remember sandbox or host mode for that workspace and stores the choice in `~/.grok/workspace-trust.json`. Explicit `--sandbox` / `--no-sandbox` flags and non-interactive commands keep their current behavior.

When sandbox mode is active you can configure:

- **Network** — off by default; enable with `--allow-net`, restrict with `--allow-host`
- **Port forwards** — `--port 8080:80`
- **Resource limits** — CPUs, memory, disk size (via settings or `/sandbox` panel)
- **Checkpoints** — start from a saved environment snapshot
- **Secrets** — inject API keys without exposing them inside the VM

All settings are saved in `~/.grok/user-settings.json` (user) and `.grok/settings.json` (project).

### Verify

Run `**/verify`** in the TUI or `**--verify`** on the CLI to verify your app locally:

```bash
grok --verify
grok -d /path/to/your/app --verify
```

The agent inspects your project, figures out how to build and run it, spins up a sandbox, and produces a verification report with screenshots and video evidence. Works with any app type.

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
