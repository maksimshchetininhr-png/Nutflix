# Nutflix TV 0.5.0 — automatic player address checks

Before Play and on Retry, the Android app checks its current player address for ordinary HTTPS redirects. A move to a new domain can be followed automatically while preserving the complete movie/episode URL, selected episode, title, and resume position. No manual link entry is needed.

The working origin is remembered on the TV only after decoded video or advancing playback is detected. Future plays start there and check again. Remote player menus keep using the loaded page’s own origin. Selecting the optional source website also uses the last working origin.

Discovery follows at most four HTTP redirects from a built-in or last-working embed. It rejects changed paths/queries, credentials, insecure/unusual ports, local/private destinations, loops, and non-HTML final responses. Page scripts, ads, and unrelated links cannot establish a new origin. HTTPS certificate checks remain enabled, and remote pages have no Android bridge.

Checks run off the UI thread with a finite deadline. If a probe fails, the existing trusted player can still be tried. Back cancels pending results, and late callbacks cannot reopen a closed player. The existing loading indicator and 25-second video startup Retry/Back recovery remain available.

## Install/update

Version 0.5.0, Android version code 7, package tv.nutflix. The signing certificate matches the published 0.4.2 and earlier builds. Install over your current version without uninstalling; My list and progress stay on the device. See INSTALL.md.

## Validation and limits

Eleven core/contract checks and twenty-seven browser tests passed. Production Java address and resolver tests passed, including current-to-future-domain migrations, remembered-origin isolation, all supported redirect statuses, preserved episode/resume URLs, rejected targets, loops, request limits, cancellation, and local/public addresses. The live .xyz to .cc redirect was verified over normal HTTPS with its complete query unchanged. APK version, signatures, and upgrade compatibility were checked.

Automatic discovery is an installed Android feature; browser iframe preview keeps a fixed origin policy. Service outages, removed redirects, JavaScript-only moves, changed embed formats, or redesigned catalogue/player APIs may still require an update. Physical TV playback and native UI behavior still need a device check.

No cloud trust-store or network-policy changes were made. No private signing key or service credentials are included.
