# How to Fix Intel Management Engine on MSI Z87-G45 GAMING

## Overview

The MSI Z87-G45 GAMING motherboard is known to occasionally encounter a bug where the Intel Management Engine (ME) becomes non-functional after extended use. When this issue occurs, the system shuts down abruptly every 30 minutes without warning.

This guide provides a step-by-step tutorial to resolve the issue by re-flashing the BIOS and the Intel ME firmware. It is designed to save time and help anyone facing the same problem.

---

## Prerequisites

### Hardware and Tools
1. **MSI Z87-G45 GAMING Motherboard**.
2. **Ubuntu Live USB** (or any Linux-based bootable USB).
3. **A USB flash drive** (minimum 4 GB, formatted to FAT32).
4. **A reliable power source** to prevent interruptions during the flashing process.

---

## Step 1: Prepare the Ubuntu Live USB

1. **Download Ubuntu ISO**:
   - Visit the [Ubuntu Downloads Page](https://ubuntu.com/download/desktop) and download the latest version of Ubuntu.

2. **Create a Bootable USB**:
   - Use a tool like [Rufus](https://rufus.ie/) on Windows or `dd` on Linux to write the Ubuntu ISO to your USB flash drive:
     - On Windows:
       1. Open Rufus.
       2. Select your USB drive.
       3. Choose the Ubuntu ISO and start the process.
     - On Linux:
       ```bash
       sudo dd if=/path/to/ubuntu.iso of=/dev/sdX bs=4M
       sync
       ```
       Replace `/path/to/ubuntu.iso` with the path to the ISO file and `/dev/sdX` with the target USB drive.

3. **Boot into Ubuntu**:
   - Insert the Ubuntu Live USB into your system.
   - Restart your PC and access the boot menu (usually by pressing `F11` or `Del` during startup).
   - Select the USB drive to boot into Ubuntu.

---

## Step 2: Download the BIOS for MSI Z87-G45 GAMING

1. **Visit MSI's Official Website**:
   - Navigate to the [MSI Support Page](https://www.msi.com/support).

2. **Locate the Z87-G45 GAMING BIOS**:
   - Search for the MSI Z87-G45 GAMING motherboard in the product section.
   - Go to the BIOS downloads section.
   - Download the latest BIOS version (e.g., a `.180` or `.zip` file).

3. **Extract the BIOS File**:
   - If the BIOS file is a `.zip`, extract its contents. Ensure the extracted file has an appropriate extension (e.g., `.180`).

4. **Copy the BIOS File to a USB Drive**:
   - Format a USB drive to FAT32.
   - Place the BIOS file on the root directory of the USB drive for easy access.

---

## Step 3: Backup and Flash the BIOS with Intel ME Firmware

### Backup Current BIOS
1. Boot into the Ubuntu Live environment.
2. Open a terminal and install `flashrom`:
   ```bash
   sudo apt update
   sudo apt install flashrom
   ```
3. Backup your current BIOS:
    ```bash
      sudo flashrom -p internal -r backup.bin
    ```
This saves the current firmware to a file named backup.bin. Store it safely.

### Flash the New BIOS

1. Flash the BIOS:

  ```bash
  sudo flashrom -p internal -w firmware.180
  ```

2. Verify the flash:

  ```bash
  sudo flashrom -p internal -v firmware.180
  ```

---

## Step 4: Clear CMOS and Reboot
- Power down your system.
- Disconnect the power cable.
- Remove the CMOS battery from the motherboard.
- Wait for 5–10 minutes.
 - Reinsert the CMOS battery, reconnect power, and boot up.

---

## Final Notes
Ensure no interruptions occur during the flashing process to avoid bricking your motherboard.
If you encounter errors during the flash process (e.g., locked regions), refer to a hardware programmer like CH341A to perform a direct flash.
By following this guide, your MSI Z87-G45 GAMING motherboard should return to full functionality, resolving the Intel Management Engine issue and preventing the 30-minute shutdown problem.

Happy troubleshooting!
