# 📲 Xiaomi Pad 6 (pipa) - Installation Guide

---

### 📂 Pre-installation
Before you start, make sure you have the following files in one folder (recommended: `platform-tools`):
* 📥 **ROM Package** (`rom.zip`)
* 🖼️ **Boot Images** (`boot.img`, `dtbo.img`, `vendor_boot.img`) - *Check ROM post/zip for these*
* 🧱 **Firmware** (Flash latest if not already included)
* 🌐 **GApps** (Optional, referred to as `gapps.zip`)
* 🛠️ **Custom Recovery** (TWRP/OrangeFox - Optional)
* 🔓 **Unlocked Bootloader** is mandatory.

---

### ⚡ First Time Installation (Clean Flash)

**Step 1: Reboot to Bootloader**
* Open terminal in your folder and run:
    ```bash
    adb reboot bootloader
    ```
    *(Or hold `Power + Volume Down` while device is off)*

**Step 2: Flash Required Images**
* Run these commands strictly in order:
    ```bash
    fastboot flash boot boot.img
    fastboot flash dtbo dtbo.img
    fastboot flash vendor_boot vendor_boot.img
    ```

**Step 3: Reboot to Recovery**
* Boot into recovery mode:
    ```bash
    fastboot reboot recovery
    ```

**Step 4: Format Data**
* In recovery menu, select **Format Data**.
* *(⚠️ Required for first-time clean install. Optional if flashing over the same ROM).*

**Step 5: Reboot Recovery**
* From recovery menu → select **Advanced** → **Reboot to recovery**.

**Step 6: Flash Firmware**
* Select **Apply update** → **Apply from ADB**.
* Sideload the firmware zip:
    ```bash
    adb sideload firmware.zip
    ```
    *(Replace `firmware.zip` with actual filename)*

**Step 7: Flash ROM**
* (Optional) Reboot recovery again.
* Select **Apply update** → **Apply from ADB**.
* Sideload the ROM package:
    ```bash
    adb sideload rom.zip
    ```
    *(Replace `rom.zip` with actual filename)*

**Step 8: Flash GApps (For Vanilla Builds)**
* *Only if using a Vanilla build.*
* Reboot recovery after ROM install ends (usually stops at ~47% on PC).
* Select **Apply update** → **Apply from ADB**:
    ```bash
    adb sideload gapps.zip
    ```

**Step 9: Reboot**
* Reboot system and Enjoy! 🚀

---

### 🔄 Update Installation
*If you are updating to a newer version of the same ROM:*

1.  **Via OTA:**
    * Go to **Settings > System > Update** and use the built-in Updater.
2.  **Via Recovery:**
    * Follow **Step 2** (Flash Images) from above.
    * Flash the new ROM zip.
    * **Do NOT** Factory Reset/Format Data.
    * Reboot System.

---

### 🚑 Troubleshooting
> **⚠️ Issue:** Play Store crashing after flashing ROM?
> **✅ Fix:** Just re-flash the `gapps.zip` file via recovery.
> 
