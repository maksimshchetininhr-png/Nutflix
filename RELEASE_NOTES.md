# Nutflix TV 0.6.2 — Backup directional navigation

Backup’s player controls now follow their positions on screen. Right and Left stay on the current visual row; Up and Down choose controls in the corresponding column. The nearest control edge wins, so Up from playback buttons reaches the nearby wide timeline before a distant header. At row/column edges, focus stays put instead of moving to another item in page order.

Nested icons and labels inside a button no longer become separate focus stops. Handled keydown and keyup events are captured before the provider’s own handlers, preventing a second sequential navigation step. Valid source focus changes keep Nutflix’s highlight aligned with the active control. Back still forwards Escape once to provider menus without a visible Close button.

When playback controls are hidden, Left/Right still seek ten seconds and OK still pauses/plays. Down opens the controls. Existing subtitle/quality menu actions, idle hiding, progress, catalogue, updater and domain checks remain available.

Version 0.6.2, Android version code 10, package tv.nutflix. Signing is unchanged. Use Settings → Check for updates, or install the APK over the current version. My list and progress stay on the TV.

Validation includes five new regressions that failed before the fix: wrong-row jumps across large gaps, nested icon focus stops, timeline/header selection, menu grids with deliberately scrambled DOM order, and duplicate provider capture handling. The full app suite, production Java checks, APK build/signatures and published downloads are verified before release. Backup’s actual provider menus still need a physical-TV check; independent fixtures do not prove source compatibility. Current System WebView support remains required for frame navigation.
