![touch me for ZEUSLAP](docs/assets/touch-me-title.png)

[English](README.md) · [한국어](README.ko.md) · [Source](https://github.com/soom-kang/touch-me)

# Touch Me Homebrew Tap

Touch Me is a menu bar app that helps you use ZEUSLAP touchscreen input properly on a Mac. This repository is a personal Homebrew Tap for installing and updating the Touch Me beta, maintaining the release version, download URL and file verification information.

The current beta targets Apple Silicon Macs running macOS 26 (Tahoe) or later and requires the USB/HID profile verified on the P16KT. Compatibility with other ZEUSLAP models has not been verified. The app starts in English, with Korean available in settings.

Beta.7 adds guarded USB-C reconnection during the same app run. Mapping can resume on a fresh `(0,0)` connection at the saved USB location and display after permissions and device/display safety checks. A connection already in `(2,0)` requires informed manual **Start mapping** and keeps that mode after **Stop mapping**.

The old record can be archived only when both recorded HID/USB services are proven ended in the same boot and ownership is verified. Archiving does not confirm restoration or authorize writing the old mode to a new connection. Uncertain records remain blocked; keep them for **Retry restore**.

This Tap distributes the verified beta.7 release, build 25. Its public DMG and checksum sidecar match the frozen artifacts; Cask Ruby syntax and Homebrew style passed. The ordinary online audit is `BLOCKED` because selected-Cask trust is absent and the user chose to keep trust unchanged. No audit checks were bypassed.

The local reconnection candidate passed one user-reported cycle. Final beta.7 installation, Gatekeeper, GUI, physical-device use and Homebrew upgrade checks are `NOT_RUN`. Earlier beta.5/build 23 native acceptance and beta.6 release records remain historical evidence.

A second finger arriving before dragging starts cancels the pending click. One-finger taps click on lift, and moving more than 8 screen-coordinate units starts a drag. An active drag follows the first finger; lift all fingers before switching gestures or starting again after scrolling. See the [release notes](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.7) for changes and validation limits.

## Install

If you already installed `/Applications/Touch Me.app` manually, turn off **Launch at login**, select **Stop mapping**, complete any pending restoration or record handling, then **Quit** normally. Preserve the old app outside Applications before continuing. Keep its saved preferences and recovery records; do not force an overwrite.

```bash
brew install --cask soom-kang/touch-me/touch-me
```

Release `0.8.0-beta.7` uses ad hoc signing without a Developer ID signature or Apple notarization. Verify the [release source and checksum](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.7) before first launch. macOS may block the app. When available, follow [Apple's manual approval procedure](https://support.apple.com/en-us/102445) in **System Settings → Privacy & Security → Open Anyway**. A damage/malware alert or managed policy may require investigation; approval and execution are not guaranteed.

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
