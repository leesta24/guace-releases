<p align="center">
  <img src="./guace-wordmark.png?v=2" alt="Guace" width="900" />
</p>

<h3 align="center">An AI-native personal knowledge base for your local files.</h3>
<p align="center"><em>macOS and Windows · local-first · your keys, your files.</em></p>

<p align="center">
  <img src="./guace-screenshot.png" alt="An earlier Guace dashboard and chat interface" width="900" />
</p>

This repository hosts public downloadable builds. The source lives in a private
repository. The screenshot shows an earlier interface and will be refreshed.

## What is Guace?

Guace combines ordinary local files with one built-in main agent. Browse your
Vault, ask questions with file context, inspect the sources, organize notes and
save useful results back to files you own. Graph helps explore local links and
connections. Managed agents, task delegation, task workspaces and external
tool-provider/MCP integrations have been removed. No external coding-agent CLI
is required.

> Connect files → ask in context → check sources → organize and save → recall.

Files remain on your disk. Provider credentials use the operating system
credential store (macOS Keychain / Windows Credential Vault). Model requests,
including relevant file context, go to the provider you configure. Local-first
indexing does not mean chat never sends document content to a remote model.

## Highlights

- **Chat with your Vault**: find, summarize and organize knowledge with one main agent.
- **File previews and editing**: Markdown, wiki-links, PDF, HTML, images, code and text.
- **Local Graph**: explore explicit links and optional on-device similarity indexes.
- **Search with evidence**: find mixed Chinese/English and short-keyword matches,
  search within a Vault directory and inspect relevant excerpts.
- **Local Mermaid diagrams**: view diagrams in Vault documents and chat.
- **Your model provider**: configure provider credentials in Settings → Models & Providers.
- **Experimental GitHub Copilot sign-in**: discover supported models available
  to your account; this does not add managed agents.
- **Shell approvals**: review operations that require approval before execution.
- **Usage and checklist**: inspect model usage and keep a persistent personal checklist.
- **Optional Telegram channel**: share the main agent and sessions with your phone.

Pre-1.0: the agent can execute tools and modify local files. Review operations as
carefully as commands you would run yourself; maintain backups of important files.

## Published builds

| Platform | Download | Notes |
| --- | --- | --- |
| macOS Apple Silicon | [0.3.4 DMG](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/Guace-0.3.4-arm64.dmg) | Developer ID signed and Apple notarized |
| macOS Intel | [0.3.4 DMG](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/Guace-0.3.4-x64.dmg) | Developer ID signed and Apple notarized |
| Windows x64 | [0.3.4 installer](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/Guace-0.3.4-windows-x64-setup.exe) | Unsigned NSIS; manual installation |

All three downloads are published in [v0.3.4](https://github.com/leesta24/guace-releases/releases/tag/v0.3.4),
currently GitHub's global latest release (checked 2026-11-10).
That release also provides Mac ZIPs, update feeds and
[SHA-256 checksums](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/SHA256SUMS.txt).
The repository-root `latest.json` and `SHA256SUMS.txt` still describe historical
0.1.4 artifacts; use the files attached to the release you are downloading.

Windows 0.3.3 does not auto-update: install 0.3.4 manually. Windows 0.3.4
includes updater code and a published update feed, but signed Windows upgrades
and an installed-version A-to-B automatic update have not been verified.
Do not treat the presence of a feed as proof that automatic upgrades work.

## Install and setup

1. Download your platform's build from [guace.app](https://guace.app/).
2. Quit Guace before upgrading. macOS: open the DMG and drag Guace to Applications,
   replacing the older app. Windows: run the setup EXE; the unsigned beta
   installer may trigger SmartScreen. Review security warnings before proceeding.
3. Open Guace, configure a provider in Settings → Models & Providers, and choose
   your Vault under Settings → Paths.
4. Start a session and ask the main agent to read or organize a note. Telegram is
   optional; no agent registration or task workspace setup is needed.

## Data and background operation

| Data | macOS | Windows |
| --- | --- | --- |
| Sessions, settings and derived indexes | ~/Library/Application Support/Guace/ | %APPDATA%/Guace/ |
| Vault default | ~/Documents/Guace/vault/ | Documents/Guace/vault/ (system Documents location) |
| Provider credentials | macOS Keychain | Windows Credential Vault |

Vault location is user-configurable; Windows Documents may be redirected by the
OS. Uninstalling the App does not imply deleting your Vault or credentials.

In 0.3.4 on both platforms, the backend normally stops when you Quit the App.
It may continue after Quit only when Telegram is enabled and has a stored token.
Saving a token alone does not enable background operation; disabling Telegram or
clearing its token removes that permission. Closing a window is not the same as
Quit; Windows can remain in the tray.

This does not add login startup or an OS service. After a reboot, or if the
background backend stops while the App is closed, open Guace again to resume
Telegram. Existing Vault files, sessions and settings are retained on upgrade;
0.3.4 does not require a search index rebuild.

<details>
<summary>Release evidence and verification limits</summary>

The [0.3.4 release notes](https://github.com/leesta24/guace-releases/releases/tag/v0.3.4)
are the current public record. The release includes the search, Graph, Mermaid,
experimental Copilot and conditional-background changes above, rather than only
source implementations awaiting their first public package.

- Mac download metadata:
  [latest.json](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/latest.json)
  and [latest-mac.yml](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/latest-mac.yml).
- Windows download metadata:
  [latest-windows.json](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/latest-windows.json)
  and [latest.yml](https://github.com/leesta24/guace-releases/releases/download/v0.3.4/latest.yml).
- The release reports packaged SQLite, Keychain, ONNX inference and clean-exit
  checks for both Mac builds. Intel execution was checked through Rosetta on
  Apple Silicon; a physical Intel Mac and macOS 13 were not separately exercised.
- Windows remains unsigned. Signed Windows A-to-B automatic-update acceptance
  remains incomplete despite the published update metadata.

These are release-record and download-metadata checks, not a fresh installation
or an end-to-end update test. Earlier dated documentation records historical
publication stages and may describe the initial Windows-only release.

</details>

## Reporting bugs

Open an issue with the Guace version, platform, steps, expected/actual behavior
and relevant screenshots or redacted logs. Never include API keys or bot tokens.
For private/security-sensitive reports, contact the maintainer directly.

## License

Guace is proprietary software. Official binary releases may be downloaded and
used for free under the [Guace Freeware License](./LICENSE). Source code is not
licensed for public use. Redistribution, repackaging, modification, reverse
engineering and resale are not permitted except where required by applicable
law or with prior written permission.
