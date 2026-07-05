# Pi HUD

A [pi coding agent](https://pi.dev/) extension that adds a heads-up display (HUD) status bar inspired by [claude-hud](https://github.com/jarrodwatts/claude-hud).

## Features

- **3-line HUD** — model, project, git branch, context usage, elapsed time, skills, extensions, tokens, cost, tool stats, running agents
- **Real-time TPS** — tokens-per-second with sliding window, color-coded speed tiers
- **TTFT** — time-to-first-token measurement (brief or always-on mode)
- **Configurable** — toggle each element on/off, customize colors and thresholds
- **Plugin system** — extend with custom HUD items via `pi-hud-plugins/`

## Install

```bash
pi install git:github.com/Mr-Koala/pi-hud
```

Or copy `pi-hud.ts` to `~/.pi/agent/extensions/` and `/reload`.

## Configuration

Edit `.pi/pi-hud.json` (project) or `~/.pi/agent/pi-hud.json` (global):

```json
{
  "tpsDisplay": "ttft",
  "tpsWindow": 1000,
  "tpsEndBehavior": "average",
  "ttftDisplay": "brief",
  "tpsThresholds": { "slow": 0, "medium": 50, "fast": 100, "blazing": 200 },
  "tpsColors": { "slow": "#ff4444", "medium": "#ffaa00", "fast": "#00ff88", "blazing": "#44ddff" }
}
```

### Options

| Option | Default | Description |
|--------|---------|-------------|
| `tpsDisplay` | `"tps"` | Display mode: `tps`, `ttft`, `stats`, `full` |
| `tpsWindow` | `1000` | Sliding window in ms |
| `tpsEndBehavior` | `"average"` | End-of-stream TPS: `average` or `last` |
| `ttftDisplay` | `"brief"` | TTFT visibility: `always` or `brief` (hide after 3s) |
| `tpsThresholds` | `{slow:0, medium:15, fast:30, blazing:45}` | Speed tier boundaries |
| `tpsColors` | hex colors | Speed tier colors |

### Commands

- `/tps` — Cycle TPS display mode (tps → ttft → stats → full)

## License

MIT
