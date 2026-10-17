# UI navigation

## Primary dashboard (exactly three)
- **Recon**: Wi-Fi, Bluetooth/BLE, GNSS, NFC/RFID, infrared receive, radio interfaces. Wi-Fi (access-point scan) and Bluetooth/BLE (device scan) are live, refreshing on-screen roughly every half-second from a background radio scan; the remaining tools show honest unavailable states until implemented.
- **Analyze**: observations, captured sessions, comparisons, saved logs, statistics, analysis tools. Empty states until data exists.
- **Expand**: module discovery, uninitialized modules, installed modules, manual module registration, setup wizard, and a live **Diagnostics** self-test. Module auto-discovery is bus dependent and still shows an honest unavailable state; **Diagnostics is live** — it runs a read-only hardware sanity pass on open (SoC/memory, an I2C bus scan, IMU, RTC, power monitor, SD card, display/touch, Wi-Fi and BLE radios) and reports a colour-coded OK / FAIL / NOT PRESENT / SKIPPED per component, with a Re-run button. It never fabricates results.

Utility: **Settings** icon in toolbar (not fourth main tile): Display, Privacy, Storage, Device, Developer, About.

## Behavior
- Every screen has back and home navigation.
- All UI switches/sliders/buttons in the browser prototype respond; settings persist locally in browser storage, not on ESP32.
- A banner identifies demonstration data.
- Unimplemented operations show a clear status rather than fabricated results.
- Privacy mask length is 1–15, with a preview using synthetic identifiers.
