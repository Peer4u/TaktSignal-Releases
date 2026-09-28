# TaktSignal — Community Alpha releases

**Manufacturing Operational Intelligence for ERPNext.** TaktSignal reads your ERPNext data (read-only) on your own
computer and highlights production, material and delivery risks early — decision support that you check, not a
system that decides for you.

**Website and downloads: https://taktsignal.cloud** — start there.

This repository is the **public release channel** of TaktSignal Community Alpha. It contains only:

- the published installers, in [Releases](https://github.com/Peer4u/TaktSignal-Releases/releases) (with `SHA256SUMS`,
  an SBOM and release notes for every version);
- the signed release metadata that the website and the installed app read (`community-alpha/manifest.json`, served
  from GitHub Pages);
- the public [issue tracker](https://github.com/Peer4u/TaktSignal-Releases/issues) for Community Alpha feedback;
- the licence and notices.

**TaktSignal's source code is not published here.** TaktSignal is proprietary software, offered free of charge for
evaluation under the [TaktSignal Community Alpha Licence](LICENSE). Bundled third-party components keep their own
licences ([THIRD_PARTY_RUNTIME_NOTICES.md](THIRD_PARTY_RUNTIME_NOTICES.md); every download also contains
`THIRD_PARTY_NOTICES.txt`).

## Before you install

TaktSignal is **Community Alpha**: early software for evaluation, not proven in production. Read
[COMMUNITY_ALPHA.md](COMMUNITY_ALPHA.md) and [KNOWN_LIMITATIONS.md](KNOWN_LIMITATIONS.md). Connect a staging or test
copy of ERPNext first, with a read-only ERPNext account.

| Computer                           | Status                                                  |
| ---------------------------------- | ------------------------------------------------------- |
| macOS, Apple Silicon               | Tested Community Alpha                                  |
| Linux x64 (Ubuntu / Debian, .deb)  | Tested Community Alpha                                  |
| Windows x64                        | Experimental — validation in progress, no download yet |
| macOS, Intel                       | Pending — no download                                   |

Download from **https://taktsignal.cloud/download** — it shows each file's size and SHA-256 from the signed release
metadata. How to check a download: [DOWNLOAD_VERIFICATION.md](DOWNLOAD_VERIFICATION.md).

## Feedback and support

- **Problems and feedback:** [open an issue](https://github.com/Peer4u/TaktSignal-Releases/issues/new/choose). The
  tracker is public — **never post** passwords, API keys, database dumps, ERPNext or TaktSignal backups, raw factory
  data or confidential customer / supplier information.
- **Private questions and support:** work.manhcang@gmail.com
- **Security vulnerabilities:** report privately to work.manhcang@gmail.com — never in a public issue. See
  [SECURITY.md](SECURITY.md).

## Privacy

The installed product sends no telemetry, analytics or crash reports. Your ERPNext data stays in a database on your
own computer. Downloading from GitHub and checking for updates are served by GitHub (GitHub, Inc.), which sees your IP
address like any web host. Details: https://taktsignal.cloud/privacy

---

TaktSignal is published by Nguyen Dac Manh Cang. © 2026. All rights reserved except as granted in [LICENSE](LICENSE).
