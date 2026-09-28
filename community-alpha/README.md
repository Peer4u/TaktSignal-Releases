# community-alpha/

`manifest.json` in this folder is the **signed release manifest** of the Community Alpha channel. It is served by
GitHub Pages at

    https://peer4u.github.io/TaktSignal-Releases/community-alpha/manifest.json

(a direct HTTPS URL: the installed app refuses redirects when it fetches the manifest). The website's download page
and the app's "Check for updates" read it, verify its Ed25519 signature and then link to the files in this
repository's Releases.

It is written by the TaktSignal release process and committed **last**, after every file of the release is uploaded
and checked. It is never edited by hand. Rolling back = restoring the previous commit of this file.
