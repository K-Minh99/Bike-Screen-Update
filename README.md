# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.2.33**, build **2026112602**.
- Binary size: **2544848 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

TPMS display refresh fix: every decoded pressure or temperature change now reaches the screen, including gradual 0.01 bar steps. Pressure decoding and the 10-minute no-signal timeout are unchanged.

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
During a trip or its ten-second summary, AP can be opened without external
power. When parked outside that window, connect the charger before the gesture.
The AP pressure setting switches between bar and PSI; stored alarm limits remain
in bar so changing the display unit preserves existing thresholds.

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

Current binary SHA-256: `da1c59cd40797bfc69e525e46cf4a48e221577640780c35be4717649dac83159`.

This build was compiled for Main. Successful OTA and Wi-Fi/AP behavior still
need confirmation on the actual board.
