# Nutflix TV 0.2.0 — remote catalogue navigation

The app now starts directly in FramexTV's catalogue. Use arrows to move the green focus highlight and OK to select title cards, navigation buttons, search controls, seasons, and episodes. Long title rails scroll automatically. The pointer mode and native mouse-click implementation were removed. Manual title IDs and links are no longer part of normal browsing.

Press Menu for app options and the optional saved-links collection from version 0.1. During catalogue playback, OK sends play/pause and left/right seek 10 seconds. Up/down or Menu → Player controls switches to the player's controls.

This version adapts the provider's current first-party interface for TV navigation, keeping its catalogue and search in sync without copied API credentials. It is not a separate catalogue API implementation.

Update installation
- Version 0.2.0, Android version code 2, package tv.nutflix.
- Same signing certificate as the published 0.1 APK; install over it without uninstalling.
- Existing local saved links and provider data are retained by a normal update.

Validation
- Six core checks and twelve browser checks pass across the current runs.
- Catalogue tests cover directional selection, scrolling rails, search focus, dynamic episodes, modal/back handling, SPA focus restoration, player commands, and roving-tabindex menus.
- APK build, signatures, Android version, and certificate compatibility with version 0.1 verified.
- Live catalogue navigation and physical TV playback remain unverified: the current cloud proxy blocks FramexTV with CONNECT 403. Catalogue tests use independent source-page fixtures.

See INSTALL.md for controls and installation.
