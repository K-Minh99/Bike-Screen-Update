# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.1.4**, build **2026100604**.
- Binary size: **2112128 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

Fix ignored TAP_SRC SINGLE flags 0x21/0x29/0x2A. Pair distinct native single taps 120-450 ms apart to open AP, retain hardware double taps and vibration gating, and coalesce held flags/poll-IRQ duplicates.

AP Display settings let you choose any of the four existing Compact/Trend
screens, then choose timed cycling or single-tap navigation exclusively.
Timed mode uses per-screen durations (defaults 5/5/5/10 seconds). Tap mode
holds the current screen until a valid single tap while the bike is stable.
Double tap still opens AP. Existing settings are preserved during migration.

## Update

Open AP settings on Main, choose Device, scan/connect to a 2.4 GHz Wi-Fi
network, then select Check for updates and Update when a newer build exists.
Wi-Fi Internet is enabled only on request while in AP and switches off after
60 seconds of inactivity. Normal operation keeps Wi-Fi off.

To install this interface for the first time, flash via USB or use the existing
manual firmware upload in AP. Manual upload remains under the expandable
advanced section in the new interface. Keep Main powered during installation.

## Artifacts

`manifest.json` identifies the version, build, target, SUB protocol, byte count
and SHA-256. Its firmware URL is pinned to an immutable commit so a newer
publication cannot change a download already being installed. Main verifies
HTTPS, size and SHA-256 before selecting the new application partition.

Current binary SHA-256: `95e4f4e50f128a61fa38e93ee6e0d6e229909faf553f38da0f7dddd6116b2723`.

This build was compiled and checked with host/browser tests. Successful OTA
and Wi-Fi/AP behavior still need confirmation on the actual board.
