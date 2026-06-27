# codex-statusline

A compact Codex TUI status line preset for WSL2 users.

It shows the model, context usage, 5-hour limit, weekly limit, and context window in one footer line:

```text
gpt-5.5 default · Context 13% used · 5h 84% left · weekly 71% left · 258K window
```

For README screenshots, this footer is too narrow to read comfortably when captured full-width. Prefer showing the text example above, or crop the terminal footer tightly before adding a screenshot.

## Requirements

- Codex CLI with TUI status-line support
- WSL2
- A Codex config file at `~/.codex/config.toml` inside your WSL2 Linux environment

On WSL2, `~/.codex/config.toml` means the Linux path in your distro, for example:

```text
/home/<linux-user>/.codex/config.toml
```

Do not edit a Windows path such as `C:\Users\<windows-user>\.codex\config.toml` unless that is where your Codex CLI actually reads its config.

## Install

Back up your Codex config:

```bash
cp ~/.codex/config.toml ~/.codex/config.toml.bak
```

Open the config file:

```bash
nano ~/.codex/config.toml
```

Add or update this section:

```toml
[tui]
status_line = [
  "model-with-reasoning",
  "context-used",
  "five-hour-limit",
  "weekly-limit",
  "context-window-size",
]
status_line_use_colors = true
```

Restart Codex after saving the file.

## Alternative: Use `/statusline`

You can also configure the same footer from inside the Codex TUI:

1. Start Codex.
2. Run `/statusline`.
3. Select and order these items:
   - `model-with-reasoning`
   - `context-used`
   - `five-hour-limit`
   - `weekly-limit`
   - `context-window-size`
4. Save the selection.

Codex persists the result to `~/.codex/config.toml`.

## Notes

Codex status lines are configured with built-in item IDs. This preset does not install an external renderer or shell script.

If your Codex version does not recognize one of the item IDs above, update Codex or run `/statusline` and choose the closest available item from the menu.

## License

MIT
