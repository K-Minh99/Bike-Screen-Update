# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.2.11**, build **2026100801**.
- Binary size: **2506720 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

Require two separate double-tap gestures to open AP: first shows a local 5-second confirmation with Wi-Fi off and BLE active; second confirms. Preserve qualified stability through 1-second tap cooldown; timeout returns to the current page. Keep AUTO/SINGLE navigation and protect the trip-summary confirmation window.

AP Display settings let you choose any of 34 live screens: Compact/Trend plus
15 new pairs, including calendar, clocks, instruments and voltage dashboards.
Mix screens across styles, then choose timed cycling or single-tap navigation.
Timed mode uses per-screen durations (Compact 5/5 seconds; all other pairs 5/10 seconds). Tap mode
holds the current screen until a valid single tap while the bike is stable.
While stable, double tap to show a local 5-second confirmation, then double tap
again to open AP. Allow about one second between the two gesture groups;
the initial stable baseline is preserved through valid tap cooldown. Wi-Fi
stays off and BLE continues during confirmation. If it expires, the same page
remains visible. Existing settings are preserved during migration.

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

Current binary SHA-256: `5717ca3188f8b91c86baf293a7255e35c1dece410fb4a69c8cae90a3c676a49e`.

This build was compiled and checked with host/browser tests. Successful OTA
and Wi-Fi/AP behavior still need confirmation on the actual board.
