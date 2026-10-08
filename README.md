# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.2.13**, build **2026100803**.
- Binary size: **2507680 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

AP entry: stable double tap opens a local prompt, the sensor then waits for a fresh 300 ms quiet interval and shows a ready state. A new single tap begun within the following visible 1-second window confirms AP; first-gesture ringing or residual native flags cannot self-confirm. The prompt closes after 5 seconds without settling. BLE remains active and Wi-Fi off until confirmation.

AP Display settings let you choose any of 34 live screens: Compact/Trend plus
15 new pairs, including calendar, clocks, instruments and voltage dashboards.
Mix screens across styles, then choose timed cycling or single-tap navigation.
Timed mode uses per-screen durations (Compact 5/5 seconds; all other pairs 5/10 seconds). Tap mode
holds the current screen until a valid single tap while the bike is stable.
While stable, double tap to show a local confirmation prompt. When vibration
settles and the display says it is ready, begin one fresh single tap within one
second to open AP. The prompt closes after five seconds if vibration never
settles. Wi-Fi stays off and BLE continues until confirmation; a timeout
restores the same page. Existing settings are preserved during migration.

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

Current binary SHA-256: `ec7617604b5d0b12451a588b4eb790cfc5a0984e5bcd29b3a6251cef9bfd2d65`.

This build was compiled and checked with host/browser tests. Successful OTA
and Wi-Fi/AP behavior still need confirmation on the actual board.
