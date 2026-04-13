# Weighbridge Client

Windows, macOS, and Linux desktop application for reading weighbridge (timbangan) data via serial port and forwarding it to WB Console.

---

## Download

Go to the [Releases](../../releases) page and download the installer for your platform:

| Platform | File |
|---|---|
| Windows | `weighbridge_client_setup_vX.X.X.exe` |
| macOS | `weighbridge_client_vX.X.X.dmg` |
| Linux | `weighbridge_client_vX.X.X.AppImage` |

The app also checks for updates automatically on startup and can download the installer directly from within the app.

---

## Installation

### Windows
1. Run the downloaded `.exe` installer
2. Follow the setup wizard
3. Launch **Weighbridge Client** from the Start Menu or Desktop shortcut

> **If you see a "VCRUNTIME140.dll not found" or similar error**, install the Visual C++ Redistributable:
> Download [VC_redist.x64.exe](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170) and run it, then relaunch the app.

### macOS
1. Open the downloaded `.dmg` file
2. Drag **Weighbridge Client** to the Applications folder
3. On first launch, right-click the app → **Open** to bypass Gatekeeper (required for unsigned apps)

> **If you see a "damaged" or "cannot be opened" error**, run the following command in Terminal then relaunch:
> ```bash
> xattr -cr /Applications/Weighbridge\ Client.app
> ```

### Linux
1. Make the AppImage executable:
   ```bash
   chmod +x weighbridge_client_vX.X.X.AppImage
   ```
2. Run it directly:
   ```bash
   ./weighbridge_client_vX.X.X.AppImage
   ```
3. (Optional) Move it to `~/.local/bin/` or `/usr/local/bin/` for system-wide access

> **Note for Linux:** Your user must be in the `dialout` group to access serial ports.
> ```bash
> sudo usermod -aG dialout $USER
> ```
> Log out and back in for the change to take effect.

---

## First-Time Setup

On first launch, the configuration window will open automatically. Fill in:

| Field | Description |
|---|---|
| **Serial Port** | COM port of the weighbridge (e.g. `COM3` on Windows, `/dev/ttyUSB0` on Linux/macOS) |
| **Baud Rate** | Match the weighbridge setting (e.g. `9600`) |
| **Data Bits / Parity / Stop Bits** | Match the weighbridge setting |
| **Offset / Length** | Trim the raw serial string to extract only the weight value |
| **Exclude Characters** | Strip unwanted characters from the serial output |
| **Scale Name** | Label shown in the app and used as the MQTT topic |

Once saved, the app will remember the configuration and auto-connect on every subsequent launch.

---

## Usage

- The app window sits in the bottom-right corner of the screen and displays the latest weight reading
- Serial port connects automatically on startup if configured
- The status indicator shows whether the serial port and MQTT broker are connected
- Click the **gear icon** to open configuration
- Click the **connection button** to manually disconnect or reconnect the serial port

---

## File Locations

### Configuration (`config.json`)

| Platform | Path |
|---|---|
| **Windows** | Next to the executable (e.g. `C:\Program Files\Weighbridge Client\config.json`) |
| **macOS** | `~/Library/Application Support/co.id.witech.weighbridge_client/config.json` |
| **Linux** | `~/.local/share/co.id.witech.weighbridge_client/config.json` |

### Log (`app.log`)

| Platform | Path |
|---|---|
| **Windows** | Next to the executable (e.g. `C:\Program Files\Weighbridge Client\app.log`) |
| **macOS** | `~/Library/Application Support/co.id.witech.weighbridge_client/app.log` |
| **Linux** | `~/.local/share/co.id.witech.weighbridge_client/app.log` |

### Downloaded Update Installer

When the app downloads an update automatically, the installer is saved to the system temp folder:

| Platform | Path |
|---|---|
| **Windows** | `C:\Users\<username>\AppData\Local\Temp\weighbridge_client_vX.X.X.exe` |
| **macOS** | `/tmp/weighbridge_client_vX.X.X.dmg` |
| **Linux** | `/tmp/weighbridge_client_vX.X.X.AppImage` |

Old installer files are cleaned up automatically before each new download.

---

## System Requirements

| Platform | Requirement |
|---|---|
| **Windows** | Windows 10 / 11 (64-bit) |
| **macOS** | macOS 12 (Monterey) or later |
| **Linux** | Ubuntu 20.04+ or any GTK3-compatible distribution (64-bit) |

Serial port (physical COM port or USB-to-serial adapter) required on all platforms.

---

## License

Copyright © 2026 PT Witech Inovasi Indonesia. All rights reserved.
