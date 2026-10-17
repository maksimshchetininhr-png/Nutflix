# Nutflix TV 0.4.1 — search keyboard and remote focus fixes

Selecting Search now explicitly requests the TV keyboard on the first visit, without requiring navigation away and back. Android waits for the focused editor and retries briefly if its input connection is not ready. A delayed request is ignored after focus moves away.

Left/right on the closed media-type selector now moves to the neighbouring search field or Search button. Press OK to open the native type picker, use up/down to choose Everything, Movies, Series, or Anime, and OK to confirm. Search results refresh without stealing focus from the controls.

The Matilda edition title, real catalogue, remote player menus, and five-second playback overlay timeout remain available.

## Install/update

Version 0.4.1, Android version code 5, package tv.nutflix. The signing certificate matches the published 0.4.0 and earlier builds. Install over your current version without uninstalling; My list and viewing progress stay on the device. See INSTALL.md.

## Validation

Eleven unit/contract checks and twenty-five browser tests pass. Three new regressions reproduced the original failures before the fixes and then passed: first-visit keyboard handoff, left/right exits for every search type, and result refresh without focus theft. Android build, package version, APK signatures, and update certificate compatibility were verified.

Browser checks verify the keyboard-request handoff; actual on-screen keyboard display and native picker behavior still require a check on the TV. Available streams, quality/subtitle choices, and anime metadata remain dependent on the source services.

This is a sideloadable development build. No private signing key or service credentials are included.
