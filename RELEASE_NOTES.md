# Nutflix TV 0.7.2 — Snow only while browsing

Christmas snowfall now stops immediately when you select Play, before opening a movie, episode, personal video or test clip. It stays off during loading, playback and app resume while the player remains open. It returns only when you go back to browsing, including Back after a playback startup error.

The earlier version kept snow out of the player but could leave its animations running in the catalogue behind the native player. This update explicitly hides and stops those animations for the entire playback session. All seven holiday themes, automatic yearly dates, the reduced-motion preference and the seasonal off switch remain available.

Version 0.7.2, Android version code 13, package tv.nutflix. Use Settings → Check for updates or install the APK over the current version. The retained signing key allows an ordinary update with My list/progress preserved.

Validation covers snowfall stopped before all four playback handoffs, staying stopped through calendar/wake refresh, resuming on catalogue return, and remaining off after Christmas ends. Full browser/calendar checks, production Java policy checks, native compilation and signature/download verification run before publishing. Physical-TV lifecycle/installer behavior remains a device check.
