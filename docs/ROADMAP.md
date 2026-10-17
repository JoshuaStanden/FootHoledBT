# Roadmap

## UI Alpha (this archive)
- [x] Document architecture and verified-versus-unverified hardware inventory
- [x] Preserve original README ASCII header and PNG logo
- [x] Clickable offline browser prototype with Recon / Analyze / Expand, Settings, privacy preview, and simulated module setup
- [x] LVGL 9 UI source foundation
- [x] Boot splash screen (`splash.cpp`) -- FOOTHOLED wordmark + tagline + boot bar, fades into the menu (written, not yet flash-verified)
- [x] ST7796 SPI display + FT6336 capacitive touch BSP integration (`board_adapter.cpp`) -- non-B board; **display verified on hardware** (draw buffers moved to internal DMA RAM; GPIOs verified from vendor demo)
- [x] PlatformIO board target corrected (`esp32-s3-devkitc-1-n16r8v`), SPIRAM/flash flags set
- [x] Toolchain pinned to ESP-IDF 6.1.x + LVGL 9.x (`firmware/src/idf_component.yml`)
- [x] `partitions.csv` for 16 MB flash (NVS + factory 6 MB + OTA 6 MB + SPIFFS + NVS keys)
- [x] NVS settings service -- brightness, privacy masking, mask length persisted across reboots
- [x] Verified GPIO pin map documented (`docs/H0.1_Pin_Map.md`)
- [ ] Confirm PSRAM mode (octal vs quad) on physical board revision
- [ ] Verify full PlatformIO/ESP-IDF build with `espressif/esp_lcd_st7796` component

## Hardware bringup
- [ ] Display brightness control -- LEDC code written; NVS persistence wired; TODO(HW): tune on real board
- [ ] MCP23017 GPIO expander driver (I2C, received -- driver skeleton pending)
- [ ] INA228 power/current monitor driver (I2C, received -- driver skeleton pending)
- [ ] Foriot dual 18650 electrical and thermal validation
- [ ] Legacy GNSS UART bringup (GY-GPS6MV2 candidate; MAX-M10S upgrade planned)
- [ ] Real Expand module registry and safe probing
- [~] SD card mount and observation storage -- **recon CSV log implemented**
      (`recon_log.cpp`, writes `/sdcard/recon_log.csv`, every Wi-Fi/BLE sighting);
      SPIFFS partition still reserved. TODO(HW): verify SDMMC pins + FAT32 card.
- [~] Wi-Fi + BLE scanners implemented (`wifi_scan.cpp`, `ble_scan.cpp`) -- run on
      their own tasks, idle until a recon screen starts them. TODO(HW): verify on board.
- [ ] **Recon log real-time timestamps** -- rows currently carry only
      `uptime_s` (seconds since boot, resets each power cycle). The board has an
      onboard **PCF85063 RTC** (I2C 0x51, shared bus); to get real dated
      timestamps: add a PCF85063 driver, set the clock once (build time / GPS /
      UI), then read it per row and emit an ISO-8601 datetime column. This is a
      KNOWN GAP we explicitly want to close.

## Later
- [ ] NFC/RFID, IR, NRF24, Sub-GHz interfaces
- [ ] Signed firmware OTA update strategy (OTA partition reserved)
- [ ] Sandboxed SD application runtime and stable plugin API
- [ ] Standard-edition PCB and enclosure publication
- [ ] FAFO (Freq Around, Find Out) -- separate project, targeting DC35; ~100 units planned
