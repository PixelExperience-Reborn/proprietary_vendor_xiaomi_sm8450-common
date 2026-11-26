# PixelExperience-Reborn — Xiaomi sm8450-common proprietary vendor

Android 17 vendor files for **POCO F5 Pro / Redmi K60 (mondrian, SM8475)** only:
SoC-level Qualcomm stack (GPU, radio, media, security, GNSS, Wi-Fi/Bluetooth, sensors, closed audio).

## What is (and is not) committed here

The closed Xiaomi/Qualcomm binaries are **not committed**: the project has no
permission to redistribute them (see
`device/xiaomi/sm8450-common/docs/HARDWARE_CONTRACT.md`). They are listed with
their SHA-256 in `device/xiaomi/sm8450-common/proprietary-files.txt` and reproduced
from the official Xiaomi OTA **OS3.0.8.0.VMNCNXM** pinned in
`device/xiaomi/sm8450-common/proprietary/ota-source.json`:

```
python3 device/xiaomi/sm8450-common/tools/extract_proprietary.py
```

The tool writes `proprietary/vendor/...` and `proprietary/provenance.json`
into this directory and refuses any file whose hash differs from the list.
`proprietary/` is ignored by git.

Method, exclusions and compatibility evidence:
`device/xiaomi/sm8450-common/docs/PROPRIETARY_FILES.md`.

## Build rules

`Android.bp`, `Android.mk`, `sm8450-common-vendor.mk` and `BoardConfigVendor.mk`
are generated from the device's `proprietary-files.txt` by
`device/xiaomi/sm8450-common/setup-makefiles.py` (the organization's
`tools/extract-utils`), after `tools/extract_proprietary.py` has
reproduced the files from the OTA and applied the declared fixups (the
Android 12 `android.*-ndk_platform` library names become the Android 17
`-ndk` names). Regenerate them whenever a list changes; never edit them
by hand.
