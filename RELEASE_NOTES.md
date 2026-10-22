# Nutflix TV 0.4.2 — player domain migration and startup recovery

Verified on 22 October 2026: framextv.xyz now redirects with HTTP 301 to framextv.cc. The new home/embed pages return HTTP 200. Earlier Nutflix versions restricted the player to the old host and blocked the new address. The metadata API remains reachable at api.framextv.tech. No reason for the operator’s domain change has been verified.

## Changes

- Opens the documented player directly at framextv.cc. The old exact domain remains an explicit redirect alias; unrelated redirects are blocked.
- Updated browser iframe policy, exact-origin messaging/telemetry, saved-link parsing, and optional source-website navigation for the new address.
- Shows an opening message while video loads. If no decoded frame or advancing progress appears within 25 seconds, Retry/Back controls replace an indefinite blank screen.
- Installs remote controls at first visible page commit as well as completion, so slow secondary resources do not delay video startup detection. Stale results from earlier loads are ignored.
- Retains Matilda edition branding, five-second playback chrome hiding, remote quality/subtitle menus, and the search fixes.

## Install/update

Version 0.4.2, Android version code 6, package tv.nutflix. The signing certificate matches the published 0.4.1 and earlier builds. Install over your current version without uninstalling; My list and playback progress remain on the device. See INSTALL.md.

## Validation and limits

Eleven unit/contract checks and twenty-seven browser tests passed. The production Java address policy also passed checks for current/legacy embeds, the verified provider redirect, and unsafe-address rejection. Browser tests use a bundled test video to distinguish a decoded frame from an empty player. APK version, signatures, and upgrade certificate compatibility were verified.

The real redirect and current player control labels were checked over verified HTTPS. Actual source streaming, native timeout dialogs, and physical TV playback still need a device check. A successful HTML response does not guarantee an available video stream. No cloud trust-store or network-policy changes were made.

This is a sideloadable development build. No private signing key or service credentials are included.
