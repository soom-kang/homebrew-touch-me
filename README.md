![touch me for ZEUSLAP](docs/assets/touch-me-title.png)

[English](README.md) · [한국어](README.ko.md) · [Source](https://github.com/soom-kang/touch-me)

# Touch Me Homebrew Tap

Touch Me is a menu bar app that helps you use ZEUSLAP touchscreen input properly on a Mac. This repository is a personal Homebrew Tap for installing and updating the Touch Me beta, maintaining the release version, download URL and file verification information.

The current beta targets Apple Silicon Macs running macOS 26 (Tahoe) or later and requires the USB/HID profile verified on the P16KT. Compatibility with other ZEUSLAP models has not been verified. The app starts in English, with Korean available in settings.

Beta.8/build 26 includes two QA fixes:

- **TMQA-006:** Retry and Start confirm directory sync even when the active recovery record is absent. A sync error or a newly appeared record blocks Start; the record format and device feature I/O stay unchanged.
- **TMQA-007:** Prepare the DMG and checksum together before replacing final files. Archive the previous valid pair with its original filenames and roll back ordinary file-move failures. A prior pair with one missing file or a checksum mismatch is preserved and rejected; both files absent permits first-time packaging; a rollback failure stops further moves and reports recovery paths. Separate renames do not guarantee crash, power-loss or concurrent-run atomicity.

The guarded USB-C reconnection introduced in beta.7 remains. During the same app run, mapping can resume on a fresh `(0,0)` connection at the saved USB location and display after permissions and device/display safety checks. A connection already in `(2,0)` requires informed manual **Start mapping** and keeps that mode after **Stop mapping**.

The old record can be archived only when both recorded HID/USB services are proven ended in the same boot and ownership is verified. Archiving does not confirm restoration or authorize writing the old mode to a new connection. Uncertain records remain blocked; keep them for **Retry restore**.

This Tap distributes the verified [beta.8 prerelease](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.8), build 26. The source/tag identity and anonymous public DMG/checksum sidecar bytes, size and digest match the frozen candidate. Actual Cask Ruby syntax and equivalent Homebrew style-rule checks passed; the Tap-directory style run inspected one file with no offenses. The actual Cask matches the source draft body, excluding its two draft-header comments.

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

If you already installed `/Applications/Touch Me.app` manually, turn off **Launch at login**, select **Stop mapping**, complete any pending restoration or record handling, then **Quit** normally. Preserve the old app outside Applications before continuing. Keep its saved preferences and recovery records; do not force an overwrite.

```bash
brew install --cask soom-kang/touch-me/touch-me
```

Release `0.8.0-beta.8` uses ad hoc signing without a Developer ID signature or Apple notarization. Verify the [release source and checksum](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.8) before first launch. macOS may block the app. When available, follow [Apple's manual approval procedure](https://support.apple.com/en-us/102445) in **System Settings → Privacy & Security → Open Anyway**. A damage/malware alert or managed policy may require investigation; approval and execution are not guaranteed.

Allow **Input Monitoring** and **Accessibility** in System Settings, then refresh the app. Updates may require renewed approval; check both permissions before mapping. The Cask does not grant permissions or remove quarantine.

## Update or remove

Before either operation, select **Stop mapping**, complete pending restoration or record handling, then **Quit** normally. If either fails, stop the operation and use **Retry restore**. Keep recovery records; do not delete them to complete an upgrade or removal. Reconnecting to the same USB port does not authorize writing the old mode to a new connection.

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
