# LibreTV mobile deployment

LibreTV 2.16.12, based on [LibreSpark/LibreTV](https://github.com/LibreSpark/LibreTV), with local fixes for source-free playback links and an optional native mobile player. Licensed under AGPL-3.0-or-later; see LICENSE.

`app-source.tar.gz` contains the complete editable application source, including the original dependency lockfile, public assets, license and cloud deployment notes. It excludes local passwords, signing keys, watching history, Windows binaries, installed dependencies and build outputs. Extract with `tar -xzf app-source.tar.gz` to inspect or edit.

The Dockerfile extracts this archive with Docker ADD, installs locked dependencies and builds the Next.js standalone server. This preserves the source directory structure when uploading through GitHub's web interface.

Deploy on Render using the root render.yaml, or create a Docker Web Service with the Free compute plan. PASSWORD must be set in Render; PROXY_SECRET should be generated there. The Blueprint config also presets the source URL and a 30-second upstream timeout.

Render Free services sleep after 15 minutes of inactivity and have monthly usage limits. Video proxying consumes bandwidth. This repository does not promise continuous or unlimited free hosting.
