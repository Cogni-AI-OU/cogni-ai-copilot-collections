---
name: agent-browser
description: >-
  Use the host-side `agent-browser` CLI for local browser smoke tests, screenshots, snapshots, and simple UI validation against forwarded localhost URLs.
  USE FOR: when interacting with `agent-browser` CLI.
---

# agent-browser

Use this skill when verification needs a real browser after the app is booted from the sandbox.

This project uses `agent-browser` on the host, not inside Shuru. The usual flow is:

1. Start the app with sandboxed bash.
2. Expose it through a forwarded localhost port.
3. Use `agent-browser` against that localhost URL.

## When Not to Use

- For CLI-only verification (no browser needed) — use standard bash verification instead.
- For visual regression diffing or cross-browser matrix testing — this skill only covers basic smoke tests.
- Headless HTML parsing or DOM scraping without visual output.

## Requirements

- The `agent-browser` CLI must be installed and available on `PATH`.
- Use a named browser session when there is any chance of concurrent runs.

## Core flow

```bash
agent-browser --session verify open <url>
agent-browser --session verify wait --load networkidle
agent-browser --session verify snapshot -i
```

After any click or navigation, re-snapshot before using old refs again.

## Common commands

```bash
# Open and wait for readiness
agent-browser --session verify open <url>
agent-browser --session verify wait --load networkidle

# Inspect the page
agent-browser --session verify snapshot -i
agent-browser --session verify get title
agent-browser --session verify get url

# Interact with elements from snapshot refs
agent-browser --session verify click @e1
agent-browser --session verify fill @e2 "text"
agent-browser --session verify press Enter

# Record the smoke test as video
agent-browser record start <output-path>

# Capture screenshot proof
mkdir -p <artifact-dir>
agent-browser --screenshot-dir <artifact-dir> screenshot
agent-browser --screenshot-dir <artifact-dir> screenshot --full

# Stop recording and clean up
agent-browser record stop
agent-browser close
```

## Guidance

- Keep browser checks narrow: page load, one or two critical controls, and optional screenshot evidence.
- Save screenshots to stable workspace-relative paths for reporting.
- Prefer `wait --load networkidle` after `open`.
- If the page is dynamic, use `snapshot -i` again after each meaningful DOM change.
- If the target URL is ambiguous because multiple forwarded ports exist, stop and report the ambiguity.
- If `agent-browser` is unavailable, fall back to bash-only verification.

## Troubleshooting

- **Session not found**: Verify the `--session` flag matches across all commands in the same flow.
- **Snapshot empty**: The page may still be loading — use `wait --load networkidle` before snapshotting.
- **Element refs stale**: After navigation or DOM mutation, re-run `snapshot -i` to refresh refs.
- **Port conflicts**: Use distinct session names for concurrent runs to avoid cross-talk.

## References

- [agent-browser's SKILL](https://raw.githubusercontent.com/superagent-ai/grok-cli/refs/heads/main/.agents/skills/agent-browser/SKILL.md)
