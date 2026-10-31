# Nutflix TV 0.6.1 — Backup remote controls

Backup uses a separate embedded video player. Older Nutflix versions sent remote commands to FramexTV’s outer player, whose controls are removed when Backup is selected. This update routes commands into the actual Backup player, including full-screen nested frames.

- OK plays/pauses the Backup video; left/right seek ten seconds during playback.
- Down reaches its timeline/controls. Arrows and OK choose the subtitle and quality choices exposed by that source.
- Back closes its menu, then hides controls, then returns Home.
- Controls hide after five idle seconds while playing; paused video and open menus keep them visible. Captions are not hidden with the control bar.
- Progress and decoded-frame status return to Nutflix for resume and startup detection.

A recent Android System WebView is required for embedded-frame navigation. If that feature is missing, the app explains how to update System WebView; native keyboard fallback is retained. Availability and layout of subtitle/quality options depend on the provider.

Version 0.6.1, Android version code 9, package tv.nutflix. The signing key is unchanged. Install over the current app, or use Settings → Check for updates from version 0.6. My list and progress remain on the TV.

Validation: eleven core/contract checks and thirty-five browser tests passed, including cross-origin and nested Backup frames, actual remote command routing, subtitle/quality selection, idle behavior, progress, and unrelated-message rejection. Native address/resolver/updater checks, APK build and signatures passed. Official AndroidX artifacts are checksum-pinned and Apache 2.0 notices are packaged. Remote frames have no Android interface.

The current public FramexTV code confirms the separate Backup iframe. Its live video page returned HTTP 403 in the cloud, so actual Backup playback/menus and WebView support still require a check on the TV. Fixture results do not establish provider compatibility. No certificate trust or source-access restrictions were bypassed.
