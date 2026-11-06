# Nutflix TV 0.8.0 — Search keyboard, smoother Home and HD preference

Selecting Search now directly requests the TV keyboard, including on the first click. Android activates the focused WebView editor and retries briefly even when an earlier IME request was accepted but not displayed. Moving away from the editor cancels stale requests.

Home scrolling follows poster rows and neighbors instead of measuring the entire catalogue per arrow. One animation follows changing targets during repeated or reversed navigation. Cards keep a stable size on focus and posters decode asynchronously. View changes reset immediately; reduced-motion preferences are respected.

Playback now prefers the highest selectable quality, including 1080p and higher when offered. The same helper runs in the main player, Backup and nested player frames, using public APIs or existing menus. It cleans up its startup menus and respects later manual changes. It cannot create HD for a lower-only/fixed-resolution stream or control a player that exposes no usable quality interface; those retain available playback. No source API keys, stream extraction or TLS changes are involved.

Version 0.8.0, Android version code 15, package tv.nutflix. Update through Settings → Check for updates or install over the current version. The retained signing key preserves My list/progress. Holiday themes, browsing-only snow and Backup submenu Back handling remain included.

Validation covers first-click native keyboard requests from a scrolled Home screen, rapid row navigation and reversal, default 1080p/4K selection through APIs/menus/selects, lower-only fallback, manual override, input cancellation and main/Backup/nested integration. The full browser/calendar suite, Java policy checks and signed APK build run before publication, followed by download verification. Native TV keyboard/animation performance and actual provider compatibility remain device checks; fixture tests do not establish live source behavior.
