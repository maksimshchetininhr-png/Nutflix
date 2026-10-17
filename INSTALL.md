# Install Nutflix on Philips Android TV / Google TV

Use `dist/Nutflix-TV.apk`. This is a sideloadable development build for Android TV / Google TV, Android 6.0 or later.

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

## First watch

1. Open **Settings and remote controls** in Nutflix and select **Test video playback**. A six-second test pattern should play. Back returns home.
2. Select **Add a title** and choose **FramexTV embed**.
3. Enter the ID or embed link supplied by FramexTV, and a title name. For example, the embed format supplied during development was `https://framextv.xyz/embed/550?autoplay=1&muted=0`; use an ID for a title you have permission to watch.
4. Save, open the title from **My library**, and select **Play**.

To browse the service instead, select **Explore FramexTV**. Use the pointer to operate its public website. The player integrated into the library is the one with dedicated remote commands and progress saving.

## Remote controls

| Screen | Controls |
| --- | --- |
| Home and library | Arrows move focus; OK selects; Back closes a window or returns home |
| FramexTV embed | OK plays/pauses; left/right seek 10 seconds; up/down cycle controls; Back returns home |
| Embedded player options | Up/down move fields; left/right change a selected list; OK activates buttons |
| Personal video | OK plays/pauses; left/right seek 10 seconds; Back saves progress and returns home |
| Public website | Arrows move pointer; OK clicks; Menu toggles toolbar; Channel +/− scroll |

FramexTV's player options expose the provider and numeric subtitle-index commands from its supplied documentation. Availability depends on the selected source. The TV's volume buttons continue to control TV audio normally.

## Troubleshooting

- **App does not install:** verify that the TV uses Android TV / Google TV and Android 6 or newer, that the transfer completed, and that the file-manager app has installation permission. Titan OS and Saphi require different app formats.
- **An update reports a signature conflict:** use the same development keystore for subsequent builds. Removing the old app permits a differently signed build but deletes that app's local library; preserve any links you need before doing so.
- **Blank page or a missing control:** update Android System WebView and Chrome from the Play Store, then reopen Nutflix.
- **FramexTV does not load or playback never starts:** check the TV's Internet connection, access to the site, and the title ID. Try Play again or a provider exposed by the player's options. Live service behavior has not been verified from the cloud environment.
- **A website login needs third-party cookies or a popup:** those capabilities are restricted in this build. A supported authentication integration would need separate implementation.
- **A direct link fails:** it must be an HTTPS media address playable by the TV, with any access the source requires. A normal website page is not a direct video link. The browser development player and Android player support different formats.

Keep the built APK and its `.sha256` file together if sharing a build for installation. The development keystore is not included in the repository. This APK has not been submitted to the Play Store.
