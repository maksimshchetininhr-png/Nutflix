# Nutflix TV 0.9.0 — Next episode and watch history

Episodes now offer an optional Next episode prompt near the credits. Up selects the card and OK starts the next confirmed, released episode, including across seasons. Not now dismisses it; playback is never skipped automatically. Finales, unaired episodes and unavailable guides do not generate invented episode numbers. The native card uses main/Backup playback telemetry and stays out of source menus.

Continue watching shows one card per TV/anime series. It resumes the most recently watched unfinished episode; after the credits window, it suggests the next available episode instead. Older unfinished episodes are retained in history without appearing as duplicate cards. Completed saved movies stay in My list under a separate Finished heading, with Watch again starting from zero. Seeking back or replaying can make a viewing unfinished again.

The current metadata does not provide reliable per-title credits markers. Episodes use a fallback of the last two minutes, capped at 10% of runtime; movies use the last five minutes, capped at 5%. These timings estimate completion and may differ from the actual credits. Existing progress remains local and completed old records are recognized where possible. Saved titles are not deleted.

Version 0.9.0, Android version code 16, package tv.nutflix. Update through Settings → Check for updates or install over the current version using the retained signing key. Holiday themes, browsing-only snow, high-quality playback preference, Search keyboard and Backup Back handling remain included.

Validation covers grouped history/restart, credits boundaries/short videos, completed movies/replay, future episodes/finales, season transitions, missing guides, optional remote prompts and guarded next-episode handoff. Production Java tests cover credits parity and forward episode identity. Full app checks/build/signatures and published download bytes are verified before release. Physical-TV remote behaviour and live source compatibility remain device checks; automated fixtures do not establish provider playback.
