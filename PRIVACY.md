---
layout: default
title: Privacy Policy
permalink: /privacy
---

# Privacy Policy for Vigil

**Effective Date:** October 21, 2026  
**Last Updated:** October 21, 2026  
**Application:** Vigil for macOS (Bundle ID: `dev.fjhernandez.vigil`)  
**Developer / Data Controller:** Francisco J. Hernandez ("Developer", "we", "us", or "our")

---

## 1. Summary: Zero Data Collection & Zero Network Access

**Vigil does not collect, transmit, store on external servers, sell, or share any personal data, usage telemetry, crash logs, or device identifiers.**

Vigil is distributed on the Mac App Store as a strictly sandboxed macOS application (`com.apple.security.app-sandbox = true`) compiled with **zero network entitlements** (it does not request `com.apple.security.network.client` or `com.apple.security.network.server`). At the macOS operating-system kernel level, Vigil is technically incapable of opening outbound or inbound internet connections or transmitting any information off your Mac.

---

## 2. Information Processed Locally on Your Device

To prevent system or display sleep according to your rules, Vigil reads specific macOS system states in real time. **All such processing occurs exclusively in volatile memory (RAM) on your Mac and is never logged, recorded, or transmitted anywhere:**

1. **Power Assertion State (`IOKit.pwr_mgt`):** Used solely to create and release macOS system and display sleep assertions (`PreventUserIdleSystemSleep` and `PreventUserIdleDisplaySleep`) while a session is active.
2. **Battery & Power Source Telemetry (`IOKit.ps`):** When the *Auto-stop on low battery* safety guard is enabled, Vigil reads your Mac's current power source (AC Power vs. Battery) and battery charge percentage in real time so it can automatically release sleep assertions when your battery drops below your configured threshold.
3. **System Thermal State (`ProcessInfo.thermalState`):** Vigil monitors macOS thermal state notifications (`nominal`, `fair`, `serious`, `critical`) in real time to automatically release sleep assertions if your Mac reaches a critical thermal state.
4. **Screen Lock State (`DistributedNotificationCenter`):** When the *Downgrade display sleep on Lock Screen* guard is enabled, Vigil listens for local macOS `com.apple.screenIsLocked` and `com.apple.screenIsUnlocked` notifications in memory to allow your display to sleep while keeping background tasks awake.

---

## 3. Data Stored Locally on Your Mac

Vigil stores your user preferences and current session state locally on your Mac using standard macOS `UserDefaults` inside the application's isolated App Sandbox container (`~/Library/Containers/dev.fjhernandez.vigil/Data/Library/Preferences/dev.fjhernandez.vigil.plist`):

- Default awake mode (`Display & System` vs. `System Only`)
- Low-battery auto-stop toggle (`vigil.autoStopOnLowBattery`) and threshold percentage (`vigil.batteryThreshold`, e.g., `20%`)
- Lock screen display downgrade toggle (`vigil.downgradeOnLockScreen`)
- Onboarding completion flag (`vigil.hasShownWelcomePopover`)
- Ephemeral active session state (`vigil.runtime.active`, `vigil.runtime.mode`, `vigil.runtime.endTime`, `vigil.runtime.agentPID`) used to coordinate status with Apple Shortcuts (`App Intents`) and local CLI commands.

If you enable **Launch at Login**, Vigil registers itself with macOS using Apple's native `SMAppService.mainApp` framework.

### Data Retention & How to Delete Your Local Data
Your local preferences remain on your Mac solely under your control. You can permanently delete all locally stored data at any time by:
1. Quitting Vigil from the macOS menu bar,
2. Moving `Vigil.app` from `/Applications` to the Trash, and
3. Removing the local sandbox container folder at `~/Library/Containers/dev.fjhernandez.vigil/`.

---

## 4. In-App Purchases & Subscriptions (`StoreKit 2`)

Vigil offers optional In-App Purchases (**Vigil Pro Annual** auto-renewable subscription and **Vigil Pro Lifetime** non-consumable unlock) processed exclusively by **Apple Inc.** via native macOS `StoreKit 2` (`storekitd` system daemon).

- **No Access to Payment Information:** The Developer never receives, processes, or has access to your Apple ID, name, billing address, credit card details, or payment instruments.
- **Cryptographic Verification Only:** Vigil verifies your entitlement locally on your device using Apple-signed cryptographic transaction receipts (`Transaction.currentEntitlements`) provided by macOS.
- All financial transactions are governed by [Apple's Privacy Policy](https://www.apple.com/legal/privacy/).

---

## 5. Third-Party SDKs, Analytics, and Advertising

Vigil contains:
- **Zero** third-party SDKs or external frameworks
- **Zero** analytics or telemetry trackers
- **Zero** crash-reporting libraries
- **Zero** advertising networks or cross-app tracking (`NSPrivacyTracking = false`)

---

## 6. Children's Privacy (COPPA)

Vigil is rated **4+** on the Mac App Store and does not knowingly or unknowingly collect personal information from anyone, including children under the age of 13 (or the applicable age of digital consent in your jurisdiction).

---

## 7. International Privacy Rights (GDPR, CCPA/CPRA, and Mexico LFPDPPP)

Whether you reside in the European Economic Area / United Kingdom (**GDPR**), California (**CCPA/CPRA**), Mexico (**Ley Federal de Protección de Datos Personales en Posesión de los Particulares — LFPDPPP**), or any other jurisdiction:
- Because we do not collect, store, or process any personal data (`Datos Personales`), we hold no personal records about you to access, rectify, port, restrict, or erase (**ARCO Rights / GDPR Articles 15–22**).
- We do not sell or share personal information as defined under the CCPA/CPRA.

---

## 8. Changes to This Privacy Policy

If we update this Privacy Policy, we will post the revised version at `https://fjhernandezdev.github.io/vigil-support/privacy` and update the "Last Updated" date above.

---

## 9. Contact & Support

If you have any questions about this Privacy Policy, privacy practices, or support requests for Vigil, please contact us via:
- **Public Support & Issue Tracker:** [https://github.com/fjhernandezdev/vigil-support/issues](https://github.com/fjhernandezdev/vigil-support/issues)
- **Support Website:** [https://fjhernandezdev.github.io/vigil-support/](https://fjhernandezdev.github.io/vigil-support/)
