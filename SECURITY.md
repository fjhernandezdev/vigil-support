---
layout: default
title: Enterprise Security, InfoSec Audit & NDA
permalink: /security
---

# Enterprise Security, InfoSec Verification & Corporate NDA

**Application:** Vigil for macOS (`dev.fjhernandez.vigil`)  
**Distribution:** Apple Mac App Store (Apple Business Manager / VPP & MDM Compatible)  
**Security Architecture:** 100% Air-Gapped / Kernel-Enforced Zero Network Access

---

## 1. Executive Summary for CISOs, InfoSec & Corporate IT

Unlike cloud-connected utilities or Electron apps that bundle third-party telemetry SDKs, **Vigil is cryptographically incapable of transmitting data off a corporate Mac.**

You do not need to take our word for it—or rely solely on a legal contract. Because Vigil is distributed as a strictly sandboxed macOS binary (`com.apple.security.app-sandbox = true`) **without** the `com.apple.security.network.client` or `com.apple.security.network.server` entitlements, the **macOS XNU kernel blocks the Vigil process from opening any network socket (TCP, UDP, HTTP, or DNS) at the operating-system level.**

---

## 2. 10-Second Cryptographic Verification (Zero-Trust Audit)

Corporate InfoSec and Endpoint Security teams can independently verify Vigil's sandbox isolation and dependency tree on any Mac using Apple's built-in command-line tools:

### A. Verify Kernel Sandbox & Absence of Network / File Entitlements
```bash
codesign -d --entitlements :- /Applications/Vigil.app
```
**Expected Output (Mac App Store Build):**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>com.apple.application-identifier</key>
    <string>23365MV9QU.dev.fjhernandez.vigil</string>
    <key>com.apple.developer.team-identifier</key>
    <string>23365MV9QU</string>
    <key>com.apple.security.app-sandbox</key>
    <true/>
</dict>
</plist>
```
* **No `com.apple.security.network.client`**: Outbound internet/LAN connections are blocked by the macOS kernel (`EPERM`).
* **No `com.apple.security.network.server`**: Inbound listening sockets are blocked by the macOS kernel.
* **No `com.apple.security.files.*`**: Vigil cannot read or write any corporate files, source code, documents, or browser data outside its isolated preferences container.
* **No TCC Permissions**: Vigil never requests Accessibility, Input Monitoring, Screen Recording, Camera, Microphone, or Full Disk Access.

### B. Verify Zero Third-Party SDKs or Supply-Chain Dependencies
```bash
otool -L /Applications/Vigil.app/Contents/MacOS/Vigil
```
Every linked library resides exclusively inside Apple's SIP-protected `/System/Library/Frameworks/` and `/usr/lib/swift/`. Vigil contains **zero** third-party frameworks, **zero** open-source or commercial analytics libraries, and **zero** crash-reporting SDKs.

---

## 3. Pre-Filled Vendor Security & Risk Assessment Matrix (CAIQ / VRM)

For Corporate Procurement, Legal, and Vendor Risk Management (VRM) teams:

| Security Control / Domain | Vigil Implementation & Posture |
| :--- | :--- |
| **Data Collection & Telemetry** | **None.** Zero PII, zero corporate data, zero telemetry, zero crash reports. |
| **Network Connectivity** | **None (Air-Gapped).** Kernel-disabled via macOS App Sandbox (0 network entitlements). |
| **Data Storage (At Rest)** | **Local Preferences Only.** Stores boolean/integer UI toggles in `~/Library/Containers/dev.fjhernandez.vigil/`. |
| **Subprocessors / Third Parties** | **None.** In-App Purchases and Volume Licenses are processed exclusively by **Apple Inc.** (`StoreKit 2`). |
| **Authentication / Credentials** | **None.** No user accounts, passwords, API keys, or SSO tokens are requested or stored. |
| **Privileged Access / Root** | **None.** Runs as a standard unprivileged user-space menu bar agent (`LSUIElement`). |
| **MDM & Fleet Deployment** | **Supported.** Deployable via **Apple Business Manager (ABM)** + Jamf, Kandji, Mosyle, or Microsoft Intune. |
| **Regulatory Alignment** | Compliant by design with **GDPR**, **CCPA/CPRA**, **HIPAA** (zero PHI access), and **Mexico LFPDPPP**. |

---

## 4. Corporate NDA & Signed Zero-Data Security Attestation

We understand that regulated enterprises (financial institutions, fintech, healthcare, defense, legal, and AI/R&D organizations) often require formal legal assurances in addition to technical verification.

Upon request, we provide corporate legal, compliance, and procurement teams with:
1. **Counter-Signed Mutual Non-Disclosure Agreement (MNDA):** We are happy to review and execute your organization's standard Mutual NDA or provide our standard Enterprise MNDA.
2. **Signed Zero-Data & Air-Gapped Architecture Attestation:** A formally executed legal attestation certifying that Vigil contains no network entitlements, collects zero data, and has zero access to customer or corporate information.
3. **Custom Vendor Security Questionnaires:** Completion of your organization's InfoSec / VRM questionnaire (HECVAT, CAIQ, SIG Lite, or custom InfoSec forms).

### How to Request an Enterprise NDA or Security Attestation
Open an Enterprise Security request at **[github.com/fjhernandezdev/vigil-support/issues](https://github.com/fjhernandezdev/vigil-support/issues)** with the title `Enterprise NDA / InfoSec Request — [Company Name]` (no confidential information needs to be posted in the issue; we will coordinate directly with your Legal or InfoSec contact via email).
