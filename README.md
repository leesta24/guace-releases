# Guace — Releases

> An intelligent personal knowledge base with powerful managed agents, for macOS.

This repository hosts public, downloadable builds of [Guace](https://github.com/leesta24/guace). The source code itself lives in a private repository.

## Latest

| Platform | Download | Notes |
| --- | --- | --- |
| **macOS (Apple Silicon)** | [`Guace-0.0.1-arm64.dmg`](../../releases/latest) | Requires macOS 10.12+ |
| **macOS (Apple Silicon, zip)** | [`Guace-0.0.1-arm64-mac.zip`](../../releases/latest) | Same payload, no installer |

Intel (`x64`) builds are not produced yet — open an issue if you need one.

## Install

1. Download the `.dmg` from the [latest release](../../releases/latest).
2. Open the `.dmg`, drag **Guace** to **Applications**.
3. Launch from Launchpad / Spotlight.

### "App is from an unidentified developer"

Guace isn't (yet) signed with an Apple Developer ID, so macOS Gatekeeper will block the first launch. Two ways around it:

**Right-click route (recommended):**
1. In **Applications**, right-click **Guace** → **Open**.
2. Click **Open** in the dialog. macOS remembers your choice forever.

**Terminal route (if Gatekeeper won't budge):**
```bash
xattr -dr com.apple.quarantine /Applications/Guace.app
```

Then double-click as normal.

## What you need to bring

Guace is a chat front-end + orchestrator on top of your own keys / tools. First-time setup:

1. **An LLM provider key** — Vercel AI Gateway, DeepSeek, etc. Add it via *Settings → Models & Providers*. Keys are stored in macOS Keychain only — never on disk, never uploaded.
2. **(Optional) A managed agent CLI** — install [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code) or [OpenAI Codex CLI](https://github.com/openai/codex) on your PATH. Add it under *Agents*; Guace will dispatch heavy tasks to it.

## Where data lives

| What | Path |
| --- | --- |
| Sessions, tasks, settings (SQLite) | `~/Library/Application Support/Guace/guace.db` |
| Prompts (`agent.md`, `user.md`) | `~/Library/Application Support/Guace/prompts/` |
| Your vault (markdown notes) | `~/Documents/Guace/vault/` |
| Task workspaces | `~/Documents/Guace/workspaces/` |
| Provider API keys | macOS Keychain — service `ai.guace.daemon` |

Uninstall = drag Guace from Applications + delete those directories (the keychain entries are reusable across reinstalls; remove them via Keychain Access if you want a clean slate).

## Status

Pre-1.0. Expect rough edges. This isn't notarised yet, the schemas are still moving, and you're trusting an unverified .dmg to run a shell tool on your machine. Don't dispatch anything you wouldn't run by hand.

## Reporting bugs

Open an issue here with:
- The Guace version (shown in *Settings*)
- What you did
- What you expected vs. what happened
- Screenshots / log snippets where useful

For private / security-sensitive reports, email the maintainer directly.

## License

Binary releases are distributed under the terms shown in the private source repository. Reverse engineering / repackaging without permission isn't welcome; using the app on your own machine is.
