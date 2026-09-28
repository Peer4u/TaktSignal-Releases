# Verifying a download

Every release publishes the SHA-256 checksum of each file:

- on **https://taktsignal.cloud/download**, next to each download (read from the signed release metadata);
- in the release's `SHA256SUMS` file;
- in `community-alpha/manifest.json`, which is signed with the TaktSignal release key (Ed25519). The website and the
  installed app accept only metadata with a valid signature, and the app checks every update's size and SHA-256
  before installing it.

Calculate the checksum of the file you downloaded and compare every character:

| Computer | Command                                   |
| -------- | ----------------------------------------- |
| macOS    | `shasum -a 256 ~/Downloads/<file>`        |
| Linux    | `sha256sum ~/Downloads/<file>`            |

If it does not match, do not open the file: delete it, download it again from taktsignal.cloud/download, and if it
still differs, report it privately to work.manhcang@gmail.com.

**macOS signing.** Whether a macOS build is signed with TaktSignal's Apple Developer ID and notarized by Apple is
stated for each release on the download page and in the release notes, and recorded in the signed release metadata.
You can check a downloaded app yourself with `spctl --assess --type execute --verbose /Applications/TaktSignal.app`.

A matching checksum proves you have the published file. It is not a security audit.
