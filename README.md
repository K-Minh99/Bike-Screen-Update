# Bike Screen OTA

OTA artifacts for TPMS Main, ESP32 with the screenBike 8 MiB partition layout.

- Firmware: **v1.1.5**, build **2026100606**.
- Binary size: **2117632 bytes**.
- Compatible SUB protocol: **2**.
- Firmware source is maintained locally and is not published here.

## Current release

v1.1.5: Continuous passive BLE and cached history maintenance; fixes false trip endings, mixed-screen data interruptions and AP/sleep handoff races. Lower chart/OTA/Wi-Fi memory, recoverable Wi-Fi scans, latest SUB snapshot held at AP acceptance, motion sampling isolated from display work. Build and host/browser tests passed; board verification pending.

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

Current binary SHA-256: `7d32d69f5d9f03210b2915b89b336af7a01f5f1e9e1101841734e098cb8215ae`.

This build was compiled and checked with host/browser tests. Successful OTA
and Wi-Fi/AP behavior still need confirmation on the actual board.
