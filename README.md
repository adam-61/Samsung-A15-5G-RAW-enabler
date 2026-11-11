# MTK RAW Enabler: Samsung Galaxy A15 5G (Rebuilt)

A Magisk module that replaces two MediaTek camera HAL libraries with patched versions so that RAW (DNG) capture can be exposed through the Camera2 API on the **Samsung Galaxy A15 5G**.

Use it with apps such as **GCam mods (BSG, Arnova)**, **LMC 8.4**, and other camera apps that support RAW/DNG.


## Credits

## What it does

The module overlays these files onto `/vendor/lib64/` (systemlessly, via KSU):

| File | Role |
|------|------|
| `libmtkcam_metastore.so` | Builds the camera's static metadata (RAW capability, RAW16 sizes, hardware level), which apps read to decide whether RAW is available |
| `libmtkcam_3rdparty_customer.so` | Request-side camera code, including DNG / opaque RAW request handling |

No files on the real vendor partition are modified. Disabling or removing the module restores the stock libraries.

## Requirements

- Samsung Galaxy A15 5G (MediaTek)
- **Magisk v20.4/KSU(temp root) or newer**


## Installation

1. Download the module zip 
2. Open **KSU**, go to **Modules**, then **Install from storage**, and select the zip.
3. The installer checks that your phone is arm64 and MediaTek, and that your stock libs match the expected file sizes. If the sizes differ, **it aborts on purpose** to protect your camera.
4. Reboot.
5. Open **Camera2 Probe**, **Manual Camera Compatibility Test**, or **LMC 8.4** and check whether RAW16 / DNG is listed.
6. Enable RAW capture in your camera app's settings.

---

## Uninstall / recovery

If the camera misbehaves after flashing:

- Open KSU, go to **Modules**, and disable or remove this module, then reboot.


## Disclaimer

- This module modifies camera libraries. **Flash at your own risk.** Back up your data and know how to disable the module before installing.
- It is provided as-is, with no warranty, and may not work on every firmware version or region.

