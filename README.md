# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.2.8**, build **2026100710**.
- Binary size: **2504080 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

History point readout: tapping the chart immediately shows the recorded voltage/temperature and RTC timestamp in an on-chart floating box. Daily charts show the nearest selected channel mean and date. Missing intervals and unknown RTC are labelled explicitly; touch zoom/pan and detailed cards are retained.

AP Display settings let you choose any of 34 live screens: Compact/Trend plus
15 new pairs, including calendar, clocks, instruments and voltage dashboards.
Mix screens across styles, then choose timed cycling or single-tap navigation.
Timed mode uses per-screen durations (Compact 5/5 seconds; all other pairs 5/10 seconds). Tap mode
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

Current binary SHA-256: `979d0a208c2967157f6cad1f41af84ae084806daedcf4bc221c56246d2ffd5eb`.

This build was compiled and checked with host/browser tests. Successful OTA
and Wi-Fi/AP behavior still need confirmation on the actual board.
