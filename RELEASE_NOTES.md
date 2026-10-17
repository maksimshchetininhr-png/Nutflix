# Nutflix TV 0.3.0 — in-app catalogue

Nutflix now starts in its own TV interface, populated automatically from FramexTV's public metadata service. Use the remote to browse poster rows, search, open title details, choose seasons and episodes, and maintain My list. No pasted links or mouse are needed for normal browsing. The source website is available as an optional Settings fallback.

Movies, series, and anime have separate paginated browsing screens. Continue watching stores progress on the device. Playback uses the provider's documented embed interface and remote player controls.

## Update installation

- Version 0.3.0, Android version code 3, package tv.nutflix.
- Signing certificate matches the published 0.1 and 0.2 APKs. Install over your current version without uninstalling.
- Existing saved links are retained. New bookmarks and playback progress are stored locally.
- Android TV / Google TV, Android 6.0 or later. See INSTALL.md for USB or ADB installation.

## Validation and limits

- Eleven core/catalogue checks and eighteen browser tests passed.
- Live metadata checks loaded 187 title cards with real posters, searched for Big Buck Bunny, and retrieved ten episodes for Game of Thrones season 2, with no JavaScript errors.
- APK signatures, package version, and update-signing compatibility were verified.
- Physical TV installation, remote behavior on the TV, and actual provider video playback still require a device check. A title listing does not guarantee an available stream.
- The public AniList service rejected cloud requests with HTTP 403. Anime browsing works through the catalogue service; anime-specific search and detailed episode guides depend on AniList access from the TV. The app shows a clear guide fallback with episode-number selection when needed.

This is a sideloadable development build. No streaming credentials, API keys, or private signing key are included.
