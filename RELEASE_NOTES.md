# Nutflix TV 0.4.0 — Matilda edition

The home title is now “nutflix. Matilda edition”.

Playback uses the source website’s actual player interface, without a duplicate Nutflix seek/options bar:

- Left/right on the remote seek backward/forward ten seconds; there are no separate +10s or −10s buttons.
- Down opens and focuses the player timeline. Down again moves into the player button row.
- Arrows and OK operate the source’s quality, subtitle, speed, volume, and server menus when available for the current stream. Subtitle choices use the source’s named tracks.
- Playing video hides title/timeline overlays after five seconds without remote input. Paused playback and open menus keep controls visible. Captions remain visible.
- Back closes a menu, then hides playback controls, then returns Home.

## Install/update

Version 0.4.0, Android version code 4, package tv.nutflix. Signing matches the published 0.1, 0.2, and 0.3 builds. Install over your current version without uninstalling. My list and local playback progress remain on the device. See INSTALL.md.

## Validation and limitations

Eleven unit/contract checks and twenty-two browser tests pass. New player tests cover single remote commands, timeline focus, quality/subtitle selection, scrolling long menus, Back behavior, five-second hiding, paused playback, and open menus. Native Android builds and APK signature verification pass.

The real provider’s published control labels were inspected over verified HTTPS. The player-navigation tests use independent fixtures; physical TV playback and controls still need a check on the TV. Available quality/subtitle/server choices depend on the current stream, and a provider interface redesign may require an adapter update. Live catalogue browsing is retained from version 0.3. Anime search/guide access still depends on AniList availability.

This is a sideloadable development build. No private signing key or service credentials are included.
