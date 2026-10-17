# Branding

The single approved repository logo is `assets/footholed-logo.png`, supplied by the project owner. No other logo formats are included. Do not infer permission to relicense or redistribute the logo, FootHoled name, or DEF CON-exclusive art/designs from the firmware license. Standard-edition hardware files will have separately documented licenses when published.

## Boot splash

The firmware boot splash (`firmware/src/splash.cpp`) is built from the FootHoled **name and tagline** (`FOOTHOLED`, `RECON · ANALYZE · EXPAND`) styled with the brand colours, plus a plain hexagon outline. It is **not** a redrawn or alternate version of the shield/boot-print logo, so it does not count as a new logo variant under the rule above. To put the actual approved artwork on the splash, convert `assets/footholed-logo.png` to an LVGL RGB565 image and display it with `lv_image` — do not hand-draw the logo a second time.
