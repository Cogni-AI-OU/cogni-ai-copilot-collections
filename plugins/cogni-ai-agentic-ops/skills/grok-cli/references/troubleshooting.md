# Troubleshooting

Common issues and solutions:

### Installation issues

**Install script fails on macOS**

Make sure you have a modern shell and `curl` available:

```bash
# Verify curl is installed
which curl

# If using an outdated shell, try with bash explicitly
bash -c "$(curl -fsSL https://raw.githubusercontent.com/superagent-ai/grok-cli/main/install.sh)"
```

**Bun not found**

The install script bundles Bun, but if you want to use your own:

```bash
curl -fsSL https://bun.sh/install | bash
bun add -g grok-dev
```

### API key issues

**"Missing GROK_API_KEY" error**

Set your API key using one of these methods:

```bash
# Environment variable
export GROK_API_KEY=your_key_here

# Or save to user settings
grok -k your_key_here
```

Get your API key from [x.ai](https://x.ai).

### Terminal UI issues

**UI doesn't render correctly**

Try a different terminal emulator. Recommended:

- WezTerm (cross-platform)
- Alacritty (cross-platform)
- Ghostty (macOS/Linux)
- Kitty (macOS/Linux)

**Screen flickering or artifacts**

Ensure your terminal supports true color and Unicode. Update your terminal emulator to the latest version.

### Telegram remote control

**Bot doesn't respond**

1. Verify `TELEGRAM_BOT_TOKEN` is set correctly
2. Ensure the CLI process is still running (long polling lives in the process)
3. Check that you've completed the `/pair` flow and been approved

**Voice messages not transcribing**

- Verify `GROK_API_KEY` is set (transcription uses the same key)
- Check `~/.grok/user-settings.json` has `telegram.audioInput.enabled: true`

### Sandbox mode

**Sandbox only works on macOS 14+ with Apple Silicon**

If you're on Intel Mac or Linux, sandbox mode is not available. Use standard mode without `--sandbox`.

### Performance issues

**Slow response times**

- Check your network connection to x.ai API
- Try `grok-4.20-non-reasoning` for non-reasoning workloads
- Reduce `--max-tool-rounds` for headless runs

**High memory usage**

- Long-running sessions accumulate context; start a fresh session periodically
- Use `/compact` in TUI to compress conversation history

### Getting help

- Check existing [issues](https://github.com/superagent-ai/grok-cli/issues)
- Open a new issue with:
  - OS and terminal emulator version
  - Grok CLI version (`grok version`)
  - Steps to reproduce
  - Error messages or logs
