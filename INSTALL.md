# Install Nutflix on Philips Android TV / Google TV

Use `Nutflix-TV.apk` (version **0.6.1**, Android version code **9**). This is a sideloadable development build for Android TV / Google TV, Android 6.0 or later. Install it over an earlier Nutflix version: the package name and signing key are unchanged, so you do not need to uninstall or clear app data.

## Updates directly on the TV

Install version 0.6 or newer once using the APK. After that:

1. Open Nutflix’s **N / Settings** button (or press Menu).
2. Select **Check for updates**, then **Download update** if a newer build is available.
3. Wait for download and verification. Cancel is available while it downloads.
4. If Android asks, select **Open settings**, enable **Allow from this source** for Nutflix, then return to the app. This permission belongs to Nutflix separately from your file manager.
5. Confirm **Install / Update** in Android’s installer. Reopen Nutflix if Android closes it after installation.

A normal update preserves My list and playback progress. The updater never uninstalls the app. If already current, it shows your installed version. Failed or incomplete downloads can be retried using Check for updates. Permission menus vary by Philips model.

Updates come only from the public Nutflix GitHub download branch. The app checks the APK’s file hash, package, newer version code, and matching signing certificate before opening the installer. Android performs its own final installation checks.

## Using a USB stick

1. Copy `Nutflix-TV.apk` onto a USB stick and connect it to the TV.
2. Open the APK using a TV file-manager app. If needed, install a file manager from the TV's Play Store first.
3. When Android asks, allow that file-manager app to **install unknown apps**, then return to the APK and select **Install**. The setting is usually under **Settings → Apps → Special app access → Install unknown apps**; Philips menu names vary.
4. Open **Nutflix** from the TV's apps list. You can revoke the file manager's installation permission afterward.

You can also transfer the APK with a file-transfer app you already use, then open it in the TV's file manager.

## Using ADB from your computer

Enable the TV's developer options and supported network/wireless debugging mode. The menus and available modes depend on the Philips model.

On models with Wireless debugging, first pair using the pairing address/port shown by the TV:

```sh
adb pair TV_IP:PAIRING_PORT
adb connect TV_IP:DEBUG_PORT
adb install -r Nutflix-TV.apk
adb shell am start -n tv.nutflix/.MainActivity
```

Enter the pairing code directly into the local ADB prompt. The pairing port and debugging port are different. Older models with network ADB enabled commonly use `adb connect TV_IP:5555`; use the connection information supported by your TV.

The cloud machine cannot directly connect to your home television. Run these commands on a computer on the same network as the TV.

## Browse and watch

1. Open **Nutflix**. The featured title and real poster rows load automatically.
2. Use arrows to move between posters and buttons. Press **OK** for a title’s details or its Play button.
3. Use **Movies**, **Series**, or **Anime** for paginated catalogue browsing.
4. Select **Search** to open the TV keyboard immediately. Enter a title, then move down to the **Search** button and press OK. To change media type, focus **Everything** (or the selected type) and press OK; use up/down to choose and OK to confirm. Left/right on the closed selector moves to the text field or Search button.
5. In a series’ details, choose a season and an episode. Future episodes are labelled and disabled.
6. Select **Add to my list** to keep a title. Played titles with saved progress appear in **Continue watching**.

The normal catalogue is Nutflix’s own interface populated from FramexTV’s public metadata service. No website browsing, manual title IDs, or pasted links are needed. The optional **Open source website** button is in Settings.

## Remote controls

| Screen | Controls |
| --- | --- |
| Home, catalogue, title details | Arrows move focus; OK selects; Back closes a window or returns Home |
| Search | Entering Search opens the TV keyboard; OK on the field reopens it; Down leaves the field for results or Search |
| Search media type | OK opens the picker; up/down choose; OK confirms; left/right on the closed picker move between controls |
| Season/episode guide | Arrows select a season or episode; OK opens it |
| Video playing | OK plays/pauses; left/right seek 10 seconds; Down opens the timeline |
| Player timeline and menus | Left/right scrub the timeline or move between buttons; Down enters the button row; arrows + OK choose settings |
| Player Back | Closes a menu, then hides controls, then returns Home |
| App settings | Select the N profile button, or press Menu |

Backup now receives remote commands inside its own player: OK pauses/plays, left/right seek, and Down opens its timeline or controls. Arrows and OK choose the subtitle/quality options supplied by that source. Back closes menus, then controls, then returns Home.

If Backup shows an **update Android System WebView** message, update System WebView (and Chrome, if available) from the TV’s Play Store and reopen Nutflix. Embedded-frame navigation requires that browser feature.

The player uses FramexTV’s real menus: select **Player Settings** for quality and other available options, **Subtitles / Captions** for named subtitle tracks, or the top **Server** button for available sources. Options depend on the current stream. The TV volume keys control TV audio.

The home title is **nutflix. Matilda edition**. While video plays, title and timeline overlays fade after **five seconds** without remote input. Paused playback and open menus keep controls visible. No separate +10s/−10s buttons are shown.

Anime-specific search and detailed episode guides depend on the public AniList service. If that service rejects the connection, use Everything search or browse the Anime categories. The guide fallback is clearly labelled and lets you choose an episode number; it does not claim a known total count.

## Troubleshooting

- **App does not install:** verify that the TV uses Android TV / Google TV and Android 6 or newer, that the transfer completed, and that the file-manager app has installation permission. Titan OS and Saphi require different app formats.
- **An update reports a signature conflict:** use the same development keystore for subsequent builds. Removing the old app permits a differently signed build but deletes that app's local library; preserve any links you need before doing so.
- **Blank page or a missing control:** update Android System WebView and Chrome from the Play Store, then reopen Nutflix.
- **Catalogue does not load:** check the TV’s Internet connection and select **Retry catalogue**. Catalogue requests use `api.framextv.tech`; playback starts at `framextv.cc` or the last working address discovered on this TV.
- **The source changes domain:** version 0.5 checks its current address before playback and on Retry. It follows ordinary HTTPS redirects for the same movie/episode, then remembers the new address after video starts. No link entry or settings change is needed.
- **Black screen on an older build:** install version 0.5.0. Earlier builds may block a new source domain.
- **Playback never starts:** a brief address check runs first, then a loading message appears while the player opens. If no video starts within 25 seconds, choose **Retry** or **Back**. You can also try another source from the player’s Server menu when it is available. A catalogue listing does not guarantee an available stream.
- **A control loses focus:** press an arrow or Back. Keep Android System WebView up to date. The normal catalogue uses packaged controls, so website layout changes do not affect its navigation.
- **A website login needs third-party cookies or a popup:** those capabilities are restricted in this build. A supported authentication integration would need separate implementation.
- **A direct link fails:** it must be an HTTPS media address playable by the TV, with any access the source requires. A normal website page is not a direct video link. The browser development player and Android player support different formats.

Keep the built APK and its `.sha256` file together if sharing a build for installation. The development keystore is not included in the repository. This APK has not been submitted to the Play Store. Automatic domain redirects cannot repair a service outage or a changed player/catalogue API.
