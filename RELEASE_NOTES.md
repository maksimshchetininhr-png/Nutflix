# Nutflix TV 0.6.0 — updates directly from the TV

Settings now includes Check for updates as the first focused option. It checks GitHub for the latest published version and offers Download update when a newer build exists. The APK downloads on the TV with progress and Cancel, is verified, and opens Android’s installer. No computer or USB stick is needed for subsequent updates.

The first in-app update may require Allow from this source for Nutflix. Android still asks you to confirm installation. Normal updates keep My list and playback progress. Install this 0.6 build once to add the update button; future builds can use it.

The updater accepts only immutable APK links in this repository, verifies expected size and SHA-256, and checks the installed package/signing certificate and a newer version code. A read-only private content provider grants Android’s installer temporary access to the verified APK. No general storage permission is needed.

The published update manifest is refreshed atomically with each download release. It points to an immutable APK commit, so publishing another update cannot change the file being downloaded.

Version 0.6.0, Android version code 8, package tv.nutflix. The signing certificate matches the previously published builds. Install over the existing app without uninstalling.

Validation covers remote access to the button, browser fallback messaging, update URL/version/file/identity checks, the full catalogue/player regression suite, and signed Android builds. The real public manifest and its APK are downloaded and verified after publishing. Native installer and permission behavior still need a physical TV check. Existing source-stream and anime-metadata limitations remain unchanged.
