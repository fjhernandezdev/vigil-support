# Vigil for macOS — Support & Documentation

**Keep your Mac awake on your terms—without draining your battery or leaving an unlocked screen glowing all night.**

Vigil is an ultra-lightweight, native macOS menu bar utility built in Swift 6 and optimized for Mac computers with Apple silicon (M1, M2, M3, and M4).

- **[Privacy Policy](https://fjhernandezdev.github.io/vigil-support/privacy)**
- **[Enterprise Security, InfoSec Verification & Corporate NDA](https://fjhernandezdev.github.io/vigil-support/security)**
- **[Terms of Use (Standard Apple EULA)](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/)**
- **[Open a Support Ticket or Enterprise NDA Request](https://github.com/fjhernandezdev/vigil-support/issues)**

---

## Key Features

- **Dual Awake Modes**:
  - **Display & System**: Prevents both display sleep and system idle sleep (`PreventUserIdleDisplaySleep` + `PreventUserIdleSystemSleep`).
  - **System Only**: Allows your display to turn off while keeping background jobs, builds, downloads, and SSH sessions awake (`PreventUserIdleSystemSleep`).
- **One-Click Toggle & Timed Presets**:
  - **Option-click (`⌥`-click)** or **Middle-click** the menu bar icon to toggle your default mode immediately.
  - Choose **Indefinitely**, **15m**, **30m**, **1h**, **2h**, or **4h** from the menu bar popover.
- **Smart Hardware Safety Guards**:
  - **Low-Battery Auto-Stop**: Automatically stops the awake session when running on battery below your custom threshold (`10%–50%`).
  - **Lock Screen Display Downgrade**: Automatically downgrades *Display & System* to *System Only* when you lock your screen (`⌃⌘Q`), then restores *Display & System* when you unlock.
  - **Thermal Emergency Cutoff**: Releases power assertions automatically if macOS reports a critical thermal state.
- **100% Private & Sandboxed**:
  - Runs inside the macOS App Sandbox with **zero network entitlements**, **zero telemetry**, and **zero third-party SDKs**.

---

## Automation: Apple Shortcuts & CLI Usage

Vigil integrates natively with **Apple Shortcuts (`App Intents`)** (`Start Vigil Session`, `Stop Vigil Session`, `Toggle Vigil Session`, and `Get Vigil Status`) and also supports command-line control via the bundled executable:

```bash
# Optional alias for your ~/.zshrc:
alias vigil="/Applications/Vigil.app/Contents/MacOS/Vigil"

# Check status (human-readable or JSON):
vigil status
vigil status --json

# Start a 2-hour System Only session:
vigil on --duration 2h --mode system

# Toggle or stop:
vigil toggle
vigil off
```

---

## Frequently Asked Questions (FAQ)

### How do I restore my Vigil Pro purchase on another Mac?
Open Vigil from the menu bar -> click **Settings...** (`⌘,`) -> click **Restore Purchases**. Make sure you are signed in to the Mac App Store with the same Apple ID used for the original purchase.

### How do I manage or cancel an annual subscription?
Subscriptions are managed directly by Apple. Open **System Settings** -> click your **Apple ID (Name)** -> **Media & Purchases** -> **Subscriptions -> Manage**, or visit [reportaproblem.apple.com](https://reportaproblem.apple.com).

### Does Vigil prevent sleep when I close my MacBook lid (clamshell mode)?
By design, Vigil uses standard macOS user-idle power assertions (`IOKit.pwr_mgt`) rather than disabling kernel system-wide sleep (`pmset disablesleep`), ensuring your MacBook never overheats inside a closed bag or backpack. Closing the lid without an external display + power adapter attached will still allow your MacBook to sleep safely.

---

## Need Help?

Please [open an issue on our Support Tracker](https://github.com/fjhernandezdev/vigil-support/issues) and include your macOS version and Mac model.
