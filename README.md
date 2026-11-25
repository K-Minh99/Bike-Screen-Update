# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.2.34**, build **2026112603**.
- Binary size: **2546880 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

TPMS parked display: keep the last pressure, temperature and sensor battery dim after a trip; parked wake-ups refresh those values without marking them live. Each tire returns to normal on a fresh packet in the current trip; NO SIG follows 10 minutes of actual BLE scanning without a packet. AP and deep sleep do not advance that timer.

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

Current binary SHA-256: `56a90b8c40da6952799022691a6a140bda9ed0add4d23e92fce0df3040904fa5`.

This build was compiled for Main. Successful OTA and Wi-Fi/AP behavior still
need confirmation on the actual board.
