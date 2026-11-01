# Nutflix TV 0.7.3 — Backup subtitle Back button

Back now reaches subtitle menus that listen for Escape on their page or focused option. Previously, Nutflix sent Escape directly to the window, skipping those listeners and leaving the submenu open. It also recognizes icon-only Back/Close actions through their title and detects subtitle panels linked by ARIA even without a menu role.

If Escape leaves the same popup open, a short, guarded fallback uses its associated expanded trigger. A submenu’s own Back action takes priority, so nested settings can return one level at a time. Closed Plyr menu wrappers no longer trap Back. Focus returns to the opening control; later Back presses hide controls and return to browsing. Delayed provider updates cannot make the fallback reopen an already closed menu.

Version 0.7.3, Android version code 14, package tv.nutflix. Update through Settings → Check for updates or install over the current app. The retained signing key preserves My list and viewing progress. All holiday themes and browsing-only Christmas snow remain included.

Validation: four new regressions failed before the fix; six new menu tests cover document Escape, trigger-only closure, nested/icon Back, ARIA panels, delayed closure and Plyr wrapper exit. Full browser/calendar, native build and Java policy checks run before publishing, followed by APK signature/download verification. Live Backup pages return HTTP 403 in the cloud, so provider-specific behavior on the physical TV remains unverified.
