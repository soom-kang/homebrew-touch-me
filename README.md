![touch me for ZEUSLAP](docs/assets/touch-me-title.png)

[English](README.md) · [한국어](README.ko.md) · [Source](https://github.com/soom-kang/touch-me)

# Touch Me Homebrew Tap

Touch Me is a menu bar app that helps you use ZEUSLAP touchscreen input properly on a Mac. This repository is a personal Homebrew Tap for installing and updating the Touch Me beta, maintaining the release version, download URL and file verification information.

The current beta targets Apple Silicon Macs running macOS 26 (Tahoe) or later and requires the USB/HID profile verified on the P16KT. Compatibility with other ZEUSLAP models has not been verified. The app starts in English, with Korean available in settings.

## Beta.10 publication — 2026-10-14

The [beta.10 prerelease](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.10) is **PUBLISHED** at 2026-10-14 01:14:28 KST / 2026-10-13 16:14:28 UTC. Source `main` and tag `v0.8.0-beta.10` resolve to `8aaebe4530ece3e0b6309c3be0df3c2d57e4d07f`; the annotated tag object is `51db567d54bd80987d5375a91e55cd80ba7f0f50`.

One native app build and one DMG packaging run produced the fixed-certificate-signed `0.8.0-beta.10` release, build 28. Native app verification is **NATIVE_APP_PASS**: strict signature, exact certificate and bidirectional designated requirements match beta.9, while the code hash differs.

Anonymous public downloads of the DMG and checksum sidecar matched the frozen candidate in complete bytes, size and digest: **PUBLIC_DOWNLOAD_PASS**. The combined public-byte and source/tag verification record is **PUBLIC_BYTE_AND_TAG_PASS**. This Cask contains the verified public DMG checksum. Beta.10 installation remains **NOT_RUN**.

| Public beta.10 release | Verified value |
| --- | --- |
| Version / build | `0.8.0-beta.10` / 28 |
| DMG | `touch-me-0.8.0-beta.10-arm64.dmg`, 525,357 bytes |
| DMG SHA-256 | `106e1738dd514f5f1ee32c912b07dea721f84cf37a8965f5474f511492d2121b` |
| Signing certificate SHA-1 | `e7491a0b49d0784093d48b2bb30b298df3a924f9` |
| Signing certificate SHA-256 | `f58a3ca4f6dcfda8f04192c5170288b3a5ffb286acbcae147ead120892002819` |

The ad hoc beta.8 → certificate-signed beta.9 transition is complete. The installed beta.9 A baseline has both **Input Monitoring: Allowed** and **Accessibility: Allowed** in the app's own GUI, confirmed by the user (**USER_REPORTED**). After normal Quit, a native process check found no Touch Me process. This establishes the A baseline; the public beta.9 A → beta.10 B Homebrew upgrade and permission-retention test remain **NOT_RUN**. Beta.10 GUI/device behavior, Gatekeeper and use on a Mac without the signing identity or added certificate trust are also **NOT_RUN**.

Beta.10 Cask Ruby syntax passed. Equivalent Homebrew style rules passed with one file and no offenses using installed compatible `spoom 1.8.9` through a process-only `-I` load path, without additional cop exclusions, gem installation or configuration/trust writes. The known bundle mismatch with missing `spoom 1.8.10` remains; this does not establish the exact locked toolchain.

This experimental personal Tap does not provide Developer ID signing or Apple notarization. The Cask has no permission-grant, certificate-trust or quarantine-removal hook. Keep its selected-Cask trust scope unchanged. The ordinary online audit remains **BLOCKED** under the existing deferral.

## Historical beta.9 publication — 2026-10-14

The [beta.9 prerelease](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.9) was **PUBLISHED** at 2026-10-14 00:17:31 KST / 2026-10-13 15:17:31 UTC. At that checkpoint, source `main` and tag `v0.8.0-beta.9` resolved to `0414617c860451e0c7b2200294b0eeca651f9ad9`.

One native app build and one DMG packaging run produced build 27 with the fixed maintainer certificate. Native artifact verification passed. Anonymous public downloads of the DMG and checksum sidecar matched the frozen candidate in complete bytes, size and digest: **PUBLIC_DOWNLOAD_PASS**. The beta.9 Cask contained the verified DMG checksum. Earlier releases, assets and tag references retained their recorded identities.

| Public beta.9 release | Verified value |
| --- | --- |
| Version / build | `0.8.0-beta.9` / 27 |
| DMG | `touch-me-0.8.0-beta.9-arm64.dmg`, 525,433 bytes |
| DMG SHA-256 | `1ef60494e4191437493f3941dba096fcc514d916b28f8380c6a71e1a579b27db` |
| Signing certificate SHA-1 | `e7491a0b49d0784093d48b2bb30b298df3a924f9` |
| Signing certificate SHA-256 | `f58a3ca4f6dcfda8f04192c5170288b3a5ffb286acbcae147ead120892002819` |

The agreed acceptance route is public signed beta.9 A → beta.10 B through normal Homebrew upgrades with the same certificate and app target. The first transition from ad hoc beta.8 may require manual privacy reapproval. At publication, beta.9 installation, Homebrew upgrade, GUI/device behavior, Gatekeeper, use on a Mac without the signing identity or added certificate trust, and the signed A → B permission-retention test were **NOT_RUN**. The later user-confirmed A baseline is recorded above. Public artifact verification does not establish those acceptance results. This experimental personal Tap does not provide Developer ID signing or Apple notarization.

Actual beta.9 Cask syntax passed. Equivalent Homebrew style rules passed with one file and no offenses using installed compatible `spoom 1.8.9` through a process-only `-I` load path, without additional cop exclusions, gem installation or configuration/trust writes. The first attempt stopped with exit 2 because the bundle expected missing `spoom 1.8.10`; the mismatch and both attempts remain in the run logs. This does not establish the exact locked toolchain.

The Cask has no permission-grant, certificate-trust or quarantine-removal hook. Keep its selected-Cask trust scope unchanged. The ordinary online audit remains **BLOCKED** under the existing deferral; do not enable developer mode or change gem/trust infrastructure to run it.

## Historical beta.8 publication — 2026-10-12

This section preserves the beta.8 publication checkpoint. Its artifact and acceptance results do not apply to the beta.9 release.

Beta.8/build 26 includes two QA fixes:

- **TMQA-006:** Retry and Start confirm directory sync even when the active recovery record is absent. A sync error or a newly appeared record blocks Start; the record format and device feature I/O stay unchanged.
- **TMQA-007:** Prepare the DMG and checksum together before replacing final files. Archive the previous valid pair with its original filenames and roll back ordinary file-move failures. A prior pair with one missing file or a checksum mismatch is preserved and rejected; both files absent permits first-time packaging; a rollback failure stops further moves and reports recovery paths. Separate renames do not guarantee crash, power-loss or concurrent-run atomicity.

The guarded USB-C reconnection introduced in beta.7 remains. During the same app run, mapping can resume on a fresh `(0,0)` connection at the saved USB location and display after permissions and device/display safety checks. A connection already in `(2,0)` requires informed manual **Start mapping** and keeps that mode after **Stop mapping**.

The old record can be archived only when both recorded HID/USB services are proven ended in the same boot and ownership is verified. Archiving does not confirm restoration or authorize writing the old mode to a new connection. Uncertain records remain blocked; keep them for **Retry restore**.

At that checkpoint, this Tap distributed the verified [beta.8 prerelease](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.8), build 26. The source/tag identity and anonymous public DMG/checksum sidecar bytes, size and digest matched the frozen candidate. Actual Cask Ruby syntax and equivalent Homebrew style-rule checks passed; the Tap-directory style run inspected one file with no offenses. The actual Cask matched the source draft body, excluding its two draft-header comments.

| Public release identity | Verified value |
| --- | --- |
| Publication | 2026-10-12 10:41:21 KST / 01:41:21 UTC |
| Source / tag commit | `e97d1720e2e994761614935cb04303f05fd1c691` / `v0.8.0-beta.8` |
| Annotated tag object | `054ca99a7936c1d6f27e6f788f303b34f0a343ca` |
| Version / build / DMG | `0.8.0-beta.8` / 26; `touch-me-0.8.0-beta.8-arm64.dmg`, 525,223 bytes |
| DMG SHA-256 | `d5b2b99085893a781928fbb7f8793e6c88505d05c32394c75c2ad57a9c7d8fb1` |

The unchanged runtime/test sources reuse the 38 Swift and 22 packaging test PASS results. One new app build and one DMG passed native artifact checks, including strict ad hoc signature, metadata/license/icon, arm64, image integrity/sidecar, read-only inner-app bytes and normal detach. Build 26 GUI, physical-device behavior, installation, upgrade and downloaded first-launch Gatekeeper checks remain `NOT_RUN`.

The ordinary online audit remains `BLOCKED` by the approved deferral. At the 2026-10-12 preflight, the selected Cask was trusted and the whole Tap was untrusted; both states are preserved. Style validation uses the installed vendored RuboCop wrapper with equivalent Homebrew rules and a task cache. The `brew style` front-end, gem installation/cleanup and trust-changing commands are not part of this validation.

All seven earlier releases, fourteen assets and fourteen annotated/peeled tag references retained their recorded identities. The [beta.7 publication](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.7) and its trust-related audit deferral stay historical. One development build 24 reconnection cycle was user-reported, without direct device-mode readback; it is not build 26 acceptance. The [beta.5/build 23 native acceptance](https://github.com/soom-kang/touch-me/blob/main/docs/qa/beta5-native-acceptance.md) and [beta.6 release record](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.6) also retain their original scope.

A second finger arriving before dragging starts cancels the pending click. One-finger taps click on lift, and moving more than 8 screen-coordinate units starts a drag. An active drag follows the first finger; lift all fingers before switching gestures or starting again after scrolling. See the [release notes](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.8) for changes and validation limits.

## Install

This Cask targets the verified public beta.10 prerelease. Before installing or upgrading, confirm that your local Cask uses version `0.8.0-beta.10`, its versioned release URL and the SHA-256 shown above. Public artifact verification does not establish local installation or upgrade success.

If you already installed `/Applications/Touch Me.app` manually, turn off **Launch at login**, select **Stop mapping**, complete any pending restoration or record handling, then **Quit** normally. Preserve the old app outside Applications before continuing. Keep its saved preferences and recovery records; do not force an overwrite.

```bash
brew install --cask soom-kang/touch-me/touch-me
```

The beta.10 release uses the same fixed maintainer certificate as beta.9, without Developer ID or Apple notarization. Before first launch, verify the source and checksum of the exact published version. macOS may block the app. When available, follow [Apple's manual approval procedure](https://support.apple.com/en-us/102445) in **System Settings → Privacy & Security → Open Anyway**. A damage/malware alert or managed policy may require investigation; approval and execution are not guaranteed.

Allow **Input Monitoring** and **Accessibility** in System Settings, then refresh the app. The first migration from ad hoc signing may require manual reapproval; keep permissions that remain allowed. Check both before mapping. Retention across signed beta.9 → beta.10 is still `NOT_RUN`; the Cask does not grant permissions or change certificate trust.

## Update or remove

Before either operation, select **Stop mapping**, complete pending restoration or record handling, then **Quit** normally. If either fails, stop the operation and use **Retry restore**. Keep recovery records; do not delete them to complete an upgrade or removal. Reconnecting to the same USB port does not authorize writing the old mode to a new connection.

For an upgrade, check **App Management** for the application that will run `brew`. Homebrew can preserve the outer app folder when it has that access; deleting and reinstalling the folder can lose permission metadata. Use a normal named upgrade. The agreed beta.9 → beta.10 test will check the newly running app without another privacy reapproval. [Homebrew FAQ](https://docs.brew.sh/FAQ#why-do-my-cask-apps-lose-their-dock-position--launchpad-position--permission-settings-when-i-run-brew-upgrade)

```bash
brew update
brew upgrade --cask soom-kang/touch-me/touch-me
```

To remove the app, turn off **Launch at login** first, complete the same Stop/Quit sequence, then run:

```bash
brew uninstall --cask soom-kang/touch-me/touch-me
```

Removal preserves saved preferences and recovery records. There are no launch hooks, process-kill hooks, permission changes or `zap` routine.

## Maintain this Tap

Beta versions are updated manually. Keep the Cask version, versioned release URL and SHA-256 together. Update `audit_exceptions/github_prerelease_allowlist.json` to the exact intended beta version; it permits that prerelease without disabling other ordinary audit checks.

Follow the [release runbook](https://github.com/soom-kang/touch-me/blob/main/docs/Homebrew.md) for publication and audit. Audit results do not establish installation, Gatekeeper approval, GUI behavior, physical-device mapping or login launch. See the [app guide](https://github.com/soom-kang/touch-me#readme) for use and support limits.

[MIT License](LICENSE), copyright 2026 Soom Kang.
