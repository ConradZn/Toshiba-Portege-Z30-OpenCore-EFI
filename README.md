# OpenCore 1.0.6 EFI for Toshiba Portege 
# Z30/T Series (Z30-A / B / C) Series

<img width="6912" height="3456" alt="Banner" src="https://github.com/user-attachments/assets/6ba4b5c9-27f9-4262-b03c-1891bbe7fdd1" />

This repository provides highly optimized OpenCore EFI configurations for the entire Toshiba Portege Z30 series. To ensure "out-of-the-box" functionality (including Wi-Fi), **please download the branch corresponding to your target macOS version.**

## 💻 Supported Models & Hardware

The Z30 series spans three CPU generations. Choose your SMBIOS based on your specific model:

| Model | CPU Generation | Architecture | Integrated GPU | SMBIOS |
| --- | --- | --- | --- | --- |
| **Z30-A / Z30T-A** | 4th Gen | Haswell | Intel HD 4400 | `MacBookAir6,2` |
| **Z30-B / Z30T-B** | 5th Gen | Broadwell | Intel HD 5500 | `MacBookPro12,1` |
| **Z30-C / Z30T-C** | 6th Gen | Skylake | Intel HD 520 | `MacBookPro13,1` |

---

## 📂 Stable Branches (Pre-configured)

Each branch is a standalone EFI. **The correct version of `AirportItlwm.kext` for Intel Wi-Fi is already included for that specific OS.**

* **`stable-catalina`** – Native support for Haswell/Broadwell.
* **`stable-big-sur`** – Final native support for Z30-A (Haswell)
* **`stable-monterey`** – High stability for Z30-B (Broadwell) and Z30-C (Skylake)
* **`stable-ventura`** – Requires OCLP for Graphics Acceleration
* **`stable-sonoma`** – Requires OCLP and specific AMFI boot-args (Coming Soon)

---

## ⚙️ BIOS Settings

* **Secure Boot:** Disabled
* **VT-d:** Disabled (or use `DisableIoMapper` in config)
* **CSM:** Disabled (Set to **UEFI Only**)
---

## 🚀 Installation & Post-Install

### 1. Prepare your EFI

* Download the branch matching your macOS version
* Use **GenSMBIOS** to generate a unique Serial, Board Serial, and UUID, **you need to put your own ROM from your ethernet**
* Add them to `config.plist` under `PlatformInfo -> Generic`

### 2. Graphics Acceleration (Ventura & Newer)

Apple dropped native support for these GPUs in newer versions. Hardware acceleration requires **OpenCore Legacy Patcher (OCLP)**:

1. Install macOS and reach the desktop
2. Download [OCLP](https://github.com/dortania/OpenCore-Legacy-Patcher/releases)
3. Run **"Post-Install Root Patch"**
4. Reboot

### 3. What works / What doesn't

## ✅ What Works

* **Graphics:** Full acceleration (Native up to Monterey, OCLP for Ventura+)
* **Audio:** Internal speakers, microphone, and 3.5mm combo jack (with ComboJack)
* **Wi-Fi & Bluetooth:** Intel AC-7260/7265 (Pre-configured in each branch)
* **Keyboard:** Full support including volume and brightness shortcuts
* **Trackpad/Touchscreen:** Multi-touch gestures
* **Battery:** Accurate percentage and status
* **USB Ports:** All ports mapped and working at USB 3.0 speeds
* **Ethernet:** Intel Gigabit LAN
* **Sleep/Wake:** Working (Proper lid wake support)
* **HDMI:** Video and Audio out
* **SD Card Reader:** May be unstable or slow (Realtek PCI reader limitation)

## ❌ What Doesn't / Known Issues

* **VGA Port:** Not supported (macOS does not support analog VGA output on Intel IGPU)
* **AirDrop/Handoff:** One-way only (Intel Wi-Fi limitation; for 100% support, a Broadcom card swap is needed)
* **Fingerprint Sensor:** Not supported (No drivers for macOS)

---

## 🛠 Recommended Utilities

| Utility | Description | Download |
| --- | --- | --- |
| **Discrete Scroll** | Fixes external mouse wheel scrolling (removes acceleration) without affecting trackpad | [GitHub Link](https://github.com/emreyolcu/discrete-scroll) |
| **ComboJack** | Enables proper headset detection for the 3.5mm combo jack | [GitHub Link](https://github.com/hoaug-tran/ComboJack) |
| **Stats** | Menu bar monitor for CPU/GPU temps and battery | [GitHub Link](https://github.com/exelban/stats) |
| **Rectangle** | Window snapping and management for the 13.3" display | [GitHub Link](https://github.com/rxhanson/Rectangle) |
| **ProperTree** | The best plist editor for managing your `config.plist` | [GitHub Link](https://github.com/corpnewt/ProperTree) |

---

## 🙌 Credits

* [Acidanthera](https://github.com/acidanthera) for OpenCore
* [OpenIntelWireless](https://github.com/OpenIntelWireless) for Wi-Fi/BT drivers
* [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for the guides
