# Known limitations — TaktSignal Community Alpha

Also published at https://taktsignal.cloud/docs/community-alpha-limitations (the website version is the current one).

This page lists what has **not** been proven yet, so you can decide how to evaluate TaktSignal. It is updated with
each Community Alpha release.

## What "Community Alpha" means

TaktSignal has been through substantial automated, synthetic and internal validation: hundreds of automated tests,
synthetic factory labs with predefined expected results, adversarial data tests, and a lab running against real
ERPNext 15 and 16 sites with synthetic data. It has **not** yet been validated across enough real factories,
ERPNext configurations and desktop environments. Community Alpha is how that evidence is gathered — with your help.

It is **not** production-proven software. Alerts can be wrong or missing.

## You should

- Start with an **ERPNext staging site, an isolated copy of your ERPNext, or a lab/test site**.
- Compare what TaktSignal shows with ERPNext and with what is really happening on the floor.
- Report discrepancies — wrong alerts, missing alerts, confusing confidence, incorrect data trust.
- Keep backups (Control Center → Backups).

## You should not

- Use TaktSignal Community Alpha as the **only** basis for critical production, purchasing or delivery decisions.
- Connect Administrator, System Manager or any account that can write. Setup refuses write-capable accounts.
- Post raw factory information, API keys, passwords, database dumps or ERPNext backups when reporting a problem.

## Platforms

| Computer                                     | Status                       | What that means                                                                                                                                                    |
| -------------------------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| macOS, Apple Silicon (macOS 12+)             | Tested Community Alpha       | Installed and taken through setup, restart, reboot, backup/restore and reinstall on a real Apple Silicon Mac running macOS 26. macOS 12–25 not run yet.            |
| Linux x64 (Ubuntu 22.04+ / Debian 12+, .deb) | Tested Community Alpha       | Automated clean-machine lifecycle on Ubuntu 24.04 (install to uninstall, including crashes, update and rollback). Ubuntu 22.04 / Debian 12 not install-tested yet. |
| Windows 10/11 x64                            | Experimental Community Alpha | The installer has been built but has not completed the same install validation on a real Windows PC. Offered only when a build is published.                       |
| macOS, Intel                                 | Pending                      | Not built or tested; no download.                                                                                                                                  |

## Known limitations

- **Code signing.** The macOS app is signed with TaktSignal's Apple Developer ID and notarized by Apple (from 0.1.0).
  The Linux `.deb` is not in a signed apt repository; its integrity comes from the SHA-256 and the signed release
  metadata. The experimental Windows installer is not published and not code-signed. You can
  [verify every download](https://taktsignal.cloud/docs/verify-download) with its SHA-256.
- **Install into Applications.** Open TaktSignal from Applications, not from the disk image or Downloads. The
  disk image shows an Applications folder to drag it onto, and since 0.1.2 the app offers “Move to Applications” when
  opened from the disk image. Since 0.1.1 it replaces an older copy still running in the background. Data is kept.
- **One computer, one person.** The desktop installation runs for the OS user who installed it and is reachable only
  from that computer. Sharing with a team requires a server installation (not covered by these guides).
- **ERPNext versions.** Exercised with ERPNext 15 (v15.121.4) and 16 (v16.36.0). Older versions connect with a
  warning and are not validated. Heavily customised sites, custom statuses and unusual stock set-ups may be read
  incompletely — [Data Trust](https://taktsignal.cloud/docs/understanding-data-trust) is designed to show where.
- **Estimates, not measurements.** "Factory time at stake" and delay hours are rule-based estimates with a written
  basis, not measured downtime. [Confidence](https://taktsignal.cloud/docs/understanding-confidence) is a rule-based label, not a statistical
  probability.
- **Calendars.** Work centers without configured shifts use an assumed default calendar; alerts that depend on it say
  so and have lower confidence.
- **Browsers.** The Control Center and the app were exercised in Chrome/Chromium. Safari, Firefox and Edge have not
  been tested yet.
- **Start at login.** On macOS, starting automatically at login before you click the icon has not been verified yet.
- **Updates.** In-app updates are tested on Linux (including automatic rollback). They are only offered for builds
  whose release metadata carries a valid signature.
- **No automatic backups** other than the ones taken before an update or a restore. Back up before experiments.

## What feedback matters most

Installation, ERPNext compatibility, synchronization, incorrect or missing alerts, confidence that feels wrong,
Data Trust problems, usability, performance and whether the workflow fits how your factory works. See
[Diagnostics and support](https://taktsignal.cloud/docs/diagnostics) for how to report safely.
