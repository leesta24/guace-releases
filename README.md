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

[Download Guace for Mac or Windows](#published-builds) · [All releases](https://github.com/leesta24/guace-releases/releases)

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

The links below follow each platform's stable release, independently of GitHub's
global `Latest` label. [Guace 0.3.8](https://github.com/leesta24/guace-releases/releases/tag/v0.3.8),
released November 25, 2026 for both platforms, adds named Vault workspaces.

| Platform | Download | Notes |
| --- | --- | --- |
| macOS Apple Silicon | [Download arm64 DMG](https://guace.app/api/download?arch=arm64) | Developer ID signed and Apple notarized |
| macOS Intel | [Download x64 DMG](https://guace.app/api/download?arch=x64) | Developer ID signed and Apple notarized |
| Windows x64 | [Download setup EXE](https://guace.app/api/download?platform=windows&arch=x64) | Unsigned beta installer; install manually |

For Mac ZIPs, version-specific installers and SHA-256 checksums, open **Assets**
on the release matching your download. Do not use the historical `latest.json`
or `SHA256SUMS.txt` in the repository root to verify a current installer.

**Upgrading from Mac 0.3.4 or Windows 0.3.4/0.3.5?** Quit Guace and install the
current build manually once. Builds from 0.3.6 onward use separate Mac and
Windows update feeds. A full automatic upgrade from the legacy builds has not
been verified on both platforms.

## Install and setup

1. Download your platform's build from the table above.
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

The backend normally stops when you Quit the App.
It may continue after Quit only when Telegram is enabled and has a stored token.
Saving a token alone does not enable background operation; disabling Telegram or
clearing its token removes that permission. Closing a window is not the same as
Quit; Windows can remain in the tray.

This does not add login startup or an OS service. After a reboot, or if the
background backend stops while the App is closed, open Guace again to resume
Telegram. On upgrade to 0.3.8, your existing Vault becomes your first workspace.
If you used semantic search, rebuild its index once; no new model download is needed.

<details>
<summary>Release evidence and verification limits</summary>

- Independent stable feeds:
  [Windows](https://github.com/leesta24/guace-releases/releases/download/windows-stable/latest.yml)
  and [Mac](https://github.com/leesta24/guace-releases/releases/download/macos-stable/latest-mac.yml).
- Mac 0.3.8 was checked on Apple Silicon and, for the Intel build, under Rosetta.
  A physical Intel Mac and macOS 13 were not separately tested.
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
