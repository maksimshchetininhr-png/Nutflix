# Install Nutflix on Philips Android TV / Google TV

Use `dist/Nutflix-TV.apk` (version **0.2.0**, Android version code **2**). This is a sideloadable development build for Android TV / Google TV, Android 6.0 or later. Install it over version 0.1: the package name and signing key are unchanged, so you do not need to uninstall or clear app data.

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

1. Open **Nutflix**. It goes directly to the FramexTV catalogue.
2. Use the **arrow keys** to move the green highlight between title cards, navigation buttons, and menus. Long title rows scroll as you move.
3. Press **OK** on a title to open its details, then choose its watch/play button. For a series, select its season and episode using the same controls.
4. For search, focus the source’s Search control and press OK. Use the TV keyboard to enter the title name.
5. Press **Back** to close a menu or return to the previous screen.

You do not need to enter title IDs or paste links to browse the catalogue. FramexTV supplies the current catalogue, search results, seasons, and playback through its own public interface; Nutflix adds the TV controls to that interface. Its separate pointer mode has been removed.

## Remote controls

| Screen | Controls |
| --- | --- |
| Catalogue, details, and episodes | Arrows move the focus highlight; OK selects; Back closes a menu or returns |
| Search | OK on the search field opens the TV keyboard |
| Catalogue playback | OK sends play/pause; left/right seek 10 seconds; up/down switch to the player’s buttons |
| App options | Menu opens the toolbar; select Catalogue, Saved links, Back, Reload, or Player controls |
| Optional embedded player | OK plays/pauses; left/right seek; up/down cycle controls |
| Personal video | OK plays/pauses; left/right seek; Back saves progress and returns |

**Menu → Player controls** switches between navigating the player’s buttons and direct play/pause/seeking commands. Select a visible provider/subtitle/settings control with arrows and OK when available. The TV’s volume buttons control TV audio normally.

**Menu → Saved links** opens your optional local collection from version 0.1, including its playback test and manual-link features. The source’s own watchlist and history stay available in its catalogue.

## Troubleshooting

- **App does not install:** verify that the TV uses Android TV / Google TV and Android 6 or newer, that the transfer completed, and that the file-manager app has installation permission. Titan OS and Saphi require different app formats.
- **An update reports a signature conflict:** use the same development keystore for subsequent builds. Removing the old app permits a differently signed build but deletes that app's local library; preserve any links you need before doing so.
- **Blank page or a missing control:** update Android System WebView and Chrome from the Play Store, then reopen Nutflix.
- **FramexTV does not load or playback never starts:** check the TV’s Internet connection and access to the service. Press Menu → Reload. The current cloud proxy blocks live catalogue inspection; the new controls were tested against representative page fixtures and still need a check on the TV.
- **A control loses its highlight:** wait for the page to finish loading, press an arrow key, or use Menu → Reload. The adapter watches dynamic page changes, but a future site redesign can require an app update.
- **A website login needs third-party cookies or a popup:** those capabilities are restricted in this build. A supported authentication integration would need separate implementation.
- **A direct link fails:** it must be an HTTPS media address playable by the TV, with any access the source requires. A normal website page is not a direct video link. The browser development player and Android player support different formats.

Keep the built APK and its `.sha256` file together if sharing a build for installation. The development keystore is not included in the repository. This APK has not been submitted to the Play Store.
