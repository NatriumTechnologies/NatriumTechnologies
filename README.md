<div align="center">
  <a href="https://natrium.sh">
    <img src="./assets/banner-v6.svg" alt="Natrium Technologies Inc." width="100%" />
  </a>
  <br />
  <br />
  <p>
    <a href="https://natrium.sh"><img src="https://img.shields.io/badge/WEBSITE-NATRIUM.SH-000000?style=for-the-badge&labelColor=09090b&color=ffffff" alt="natrium.sh" /></a>
    <a href="https://natrium.sh/downloads"><img src="https://img.shields.io/badge/DOWNLOADS-APPS_%26_CLI-000000?style=for-the-badge&labelColor=09090b&color=ffffff" alt="Downloads" /></a>
    <a href="https://natrium.sh/security"><img src="https://img.shields.io/badge/SECURITY-NAT--SEC--2026.11.01-000000?style=for-the-badge&labelColor=09090b&color=10b981" alt="Security Spec" /></a>
    <a href="https://github.com/sponsors/NatriumTechnologies"><img src="https://img.shields.io/badge/SPONSOR-GITHUB_SPONSORS-ea4aaa?style=for-the-badge&logo=githubsponsors&logoColor=white" alt="Sponsor" /></a>
  </p>
  <p>
    <img src="https://img.shields.io/badge/Vault-AES--256--GCM-09090b?style=flat-square&logo=gnupg&logoColor=ffffff" alt="AES-256-GCM" />
    <img src="https://img.shields.io/badge/KDF-scrypt_(N%3D32768)-09090b?style=flat-square&logoColor=ffffff" alt="scrypt" />
    <img src="https://img.shields.io/badge/Auth-FIDO2_%2F_WebAuthn-09090b?style=flat-square&logo=yubico&logoColor=ffffff" alt="FIDO2" />
    <img src="https://img.shields.io/badge/Threat_Intel-Falcon_Sandbox_%26_VT-09090b?style=flat-square&logoColor=ffffff" alt="Threat Intel" />
    <img src="https://img.shields.io/badge/MTA-Direct--MX_%2F_TLS_1.3-09090b?style=flat-square&logoColor=ffffff" alt="Direct-MX" />
    <img src="https://img.shields.io/badge/APIs-OpenAPI_3.1_%2F_MCP-09090b?style=flat-square&logoColor=ffffff" alt="OpenAPI MCP" />
  </p>
</div>

---

### Overview

**Natrium Technologies Inc.** builds sovereign, zero-knowledge encrypted communications infrastructure engineered for uncompromising personal and enterprise confidentiality. Our flagship platform, [**natrium.sh**](https://natrium.sh), is a next-generation encrypted email system designed and operated entirely in-house.

Unlike ad-supported email providers that scan message bodies or legacy encrypted services reliant on closed bridges, Natrium delivers end-to-end cryptographic privacy with **Direct-MX mail delivery**, **pre-vault behavioral malware screening**, **hardware FIDO2 passkeys**, and **standardized Model Context Protocol (MCP) & OpenAPI endpoints** for developer and agent workflows.

- **Zero-Knowledge Envelope Encryption**: Message bodies, subjects, headers, drafts, notes, and attachment blobs are encrypted client-side using authenticated **AES-256-GCM** with keys derived via memory-hard **scrypt** ($N=32768, r=8, p=1$). Only minimal RFC 5322 routing headers are processed for mail transit.
- **Pre-Vault Multi-Engine Threat Screening**: Inbound attachments are vetted at the MX boundary across 70+ threat engines via VirusTotal and Falcon Sandbox behavioral reputation intelligence before being sealed into encrypted vault storage.
- **Sovereign Direct-MX Outbound MTA**: Outbound mail resolves recipient MX records directly over TLS 1.3 with Perfect Forward Secrecy, signed with 2048-bit RSA DKIM keys and verified against strict SPF (`-all`) and DMARC (`p=reject`) policies.
- **Anti-Surveillance & Tracker Neutralization**: Automated stripping of 1x1 tracking pixels, invisible web beacons, and remote marketing telemetry prior to rendering. Zero ad networks, zero tracking cookies, zero data brokerage.
- **Bot-Free, Zero-ID Onboarding**: No phone numbers, SMS verification, or personal identifiers required. Handle reservations are human-reviewed within hours to preserve clean sender IP reputation across all outbound relays.
- **Programmatic & AI Agent Access**: Native support for **OpenAPI 3.1**, **Model Context Protocol (MCP)**, and Agent-to-Agent (A2A) interfaces, enabling autonomous agent workflows without brittle desktop bridges.

---

### Architectural Benchmark: Natrium vs. Legacy Providers

| Capability / Architecture | Legacy Encrypted Providers (Proton, Tuta) | Big Tech (Gmail, Outlook) | **Natrium Secure Mail (`natrium.sh`)** |
| :--- | :--- | :--- | :--- |
| **Inbound Attachment Screening** | Basic static signature checks with limited feed updates | Automated ad scanning & indexing | **Pre-vault screening across 70+ engines & Falcon Sandbox behavioral telemetry** |
| **Outbound MTA & Deliverability** | Open signups attract botnets that degrade shared relay reputation | High deliverability tied to invasive account surveillance | **Direct-MX delivery with human-vetted handle requests protecting relay reputation** |
| **Registration Requirements** | Often demands phone SMS verification or external recovery email | Strict phone number, device tracking & KYC verification | **Zero phone numbers, SMS verification, or personal identifiers required** |
| **Developer & AI Agent Access** | Requires proprietary desktop bridges or closed web interfaces | REST APIs bound to complex OAuth & cloud data harvesting | **Documented OpenAPI 3.1, Model Context Protocol (MCP), and A2A endpoints** |
| **Data Stored on Server** | Subject lines & contact metadata often stored unencrypted | Full plaintext messages, attachments, and user search history | **AES-256-GCM encrypted bodies, subjects, and `.enc` blobs; zero plaintext storage** |
| **Key Derivation & Protection** | Legacy OpenPGP keyring management with high browser overhead | Server holds all cryptographic master keys | **Memory-hard `scrypt` ($N=32768$), AES-256-GCM DEK envelopes & FIDO2 passkeys** |
| **Privacy & Anti-Tracking** | Manual tracking toggles; promotional cross-sell banners | Ingests 1x1 pixels to profile purchases and travel habits | **Automatic 1x1 pixel stripping in a clean, distraction-free dark workspace** |

---

### Cryptographic Security Specifications (`NAT-SEC-2026.11.01`)

Natrium operates under documented formal security and operational policies:

```text
[Client Passphrase] ──► [HMAC-SHA256 Pepper] ──► [scrypt N=32768, r=8, p=1] ──► [Key Encryption Key (KEK)]
                                                                                         │
                                                    ┌────────────────────────────────────┘
                                                    ▼
[Random 256-bit DEK] ──(Encrypted by KEK)──► [Persisted DEK Envelope]
        │
        ├──► Message Bodies & Subjects ────► AES-256-GCM (Fresh 96-bit IV + 128-bit Tag)
        ├──► Disk Attachment Blobs ────────► Encrypted Binary .enc Files
        └──► Inbound External Mail ────────► Pre-Vault Screening (70+ Engines / Falcon Sandbox)
```

1. **Memory-Hard Key Derivation**: User passphrases undergo server-side HMAC-SHA256 peppering in protected volatile memory, followed by `scrypt` ($N=32768, r=8, p=1$) requiring 32 MB of contiguous RAM per evaluation to render GPU/ASIC cluster attacks infeasible.
2. **Envelope Vault Architecture**: Each tenant mailbox is isolated by a unique 256-bit Data Encryption Key (DEK) sealed under the user's Key Encryption Key (KEK). Disk attachments exist strictly as authenticated `.enc` binary blobs.
3. **Volatile In-Memory Decryption**: During outbound MTA transmission, attachment blobs are decrypted strictly into ephemeral memory buffers for MIME streaming; plaintext data is never written back to physical storage.
4. **Phishing-Resistant Authentication**: Support for WebAuthn / FIDO2 hardware keys (YubiKey, Apple Touch ID / Face ID, Windows Hello), RFC 6238 TOTP authenticators, and single-use 8-character backup codes across all tiers.
5. **Perimeter Hardening**: Cloudflare Anycast edge routing, stateful rate-limiting, Strict-Transport-Security (HSTS 2-year preload), strict CSP (`frame-ancestors 'none'`), and automated session revocation upon anomaly detection.

---

### Platform Plans & Tiers

| Feature / Resource | Free Tier ($0/mo) | Pro ($3.99/mo billed annually) | Enterprise ($11.99/mo per user) |
| :--- | :--- | :--- | :--- |
| **Encrypted Storage** | 10 GB Vault Storage | 25 GB Vault Storage | 50 GB Dedicated Storage |
| **Mail Addresses** | 3 `@natrium.sh` Addresses | 5 `@natrium.sh` Aliases | Unlimited Custom Domain Links |
| **Encrypted Attachments** | 25 MB per message | 100 MB per message | 100 MB+ High-Bandwidth Relays |
| **Multi-Identity Switching**| Up to 2 Linked Accounts | Up to 4 Linked Accounts | Unlimited Account Links & Console |
| **Threat Screening** | 70+ Antivirus & Sandbox Feeds | 70+ Antivirus & Sandbox Feeds | Advanced Behavioral Heuristics |
| **AI Capabilities** | Contextual Summarization | Autonomous AI Auto-Reply Engine | Dedicated Model Serving & Tuning |
| **Developer / Agent APIs**| OpenAPI 3.1 & MCP Endpoints | High-Rate OpenAPI 3.1 & MCP | Custom Inbound/Outbound MTA Relays |
| **Support SLA** | Community & Ticket Support | Priority Ticket Queue | 24/7 Dedicated Incident Team |

---

### Native Downloads & Installation

Natrium Email is available across all desktop, mobile, and command-line environments. Native binaries default directly to the zero-knowledge session workspace with zero external runtime dependencies.

#### 🪟 Windows

| Edition | Architecture / Format | Direct Link |
| :--- | :--- | :--- |
| **64-bit Native App** | `.exe` Installer (x64) | [Download Installer](https://natrium.sh/api/downloads?platform=windows) |
| **Portable** | `.zip` Archive (x64) | [Download Portable](https://natrium.sh/api/downloads?platform=windows_zip) |
| **ARM64** | `.exe` (arm64) | [Download ARM64](https://natrium.sh/api/downloads?platform=windows_arm64) |
| **32-bit Legacy** | `.exe` (ia32) | [Download 32-bit](https://natrium.sh/api/downloads?platform=windows_32) |

**One-Line PowerShell Install**:
```powershell
irm https://natrium.sh/install.ps1 | iex
```

---

#### 🐧 Linux

| Package | Architecture / Format | Direct Link |
| :--- | :--- | :--- |
| **Universal AppImage** | `.AppImage` (x86_64) | [Download AppImage](https://natrium.sh/api/downloads?platform=linux) |
| **Debian / Ubuntu** | `.deb` Package (amd64) | [Download .deb](https://natrium.sh/api/downloads?platform=deb) |
| **Fedora / RHEL** | `.rpm` Package (x86_64) | [Download .rpm](https://natrium.sh/api/downloads?platform=rpm) |
| **ARM64 AppImage** | `.AppImage` (aarch64) | [Download ARM64](https://natrium.sh/api/downloads?platform=linux_arm64) |

**One-Line Terminal Install**:
```bash
curl -fsSL https://natrium.sh/install.sh | bash
```

---

#### 🍎 macOS

| Architecture | Package Format | Direct Link |
| :--- | :--- | :--- |
| **Apple Silicon (M1 / M2 / M3 / M4)** | `.dmg` (arm64) | [Download Apple Silicon](https://natrium.sh/api/downloads?platform=mac_arm64) |
| **Intel Core** | `.dmg` (x86_64) | [Download Intel DMG](https://natrium.sh/api/downloads?platform=mac_x64) |

---

#### 📱 Mobile (Android & iOS)

- **Android Universal APK**: [Download Universal APK](https://natrium.sh/api/downloads?platform=android)
- **Android ARM64-v8a APK**: [Download ARM64 APK](https://natrium.sh/api/downloads?platform=android_arm64)
- **iOS (iPhone & iPad PWA)**: Open Safari, navigate to [`https://natrium.sh/?view=login&app=1`](https://natrium.sh/?view=login&app=1), tap **Share**, and select **Add to Home Screen**.

> 💡 *Full cryptographic SHA-256 checksums and verification public keys are published on the [**Natrium Downloads Portal**](https://natrium.sh/downloads).*

---

### Tech Stack

```text
CORE PRODUCT        Sovereign Encrypted Email · Zero-Knowledge Storage · Custom Outbound MTA
FRONTEND & DESKTOP  Next.js 15 · React 19 · Electron · Tailwind CSS · TypeScript
BACKEND & ENGINE    Node.js · SQLite / WAL Mode · REST APIs · Direct-MX SMTP Engine
CRYPTOGRAPHY        AES-256-GCM · scrypt (N=32768) · FIDO2 / WebAuthn · RSA-2048 DKIM
THREAT DEFENSE      VirusTotal API · Falcon Sandbox Heuristics · 1x1 Pixel Stripping
INFRASTRUCTURE      Linux Sovereign Bare-Metal · Cloudflare Anycast · Strict DNSSEC
PROGRAMMATIC        OpenAPI 3.1 Specification · Model Context Protocol (MCP) · A2A APIs
```

---

### Transparency, Legal & Contact

- **Main Platform**: [https://natrium.sh](https://natrium.sh)
- **Downloads Portal**: [https://natrium.sh/downloads](https://natrium.sh/downloads)
- **Security Architecture**: [`NAT-SEC-2026.11.01`](https://natrium.sh/security)
- **Architecture Comparison**: [`NAT-CMP-2026.11.01`](https://natrium.sh/security)
- **Terms of Service**: [`NAT-TOS-2026.11.01`](https://natrium.sh/security)
- **Privacy Policy**: [`NAT-PRIV-2026.11.01`](https://natrium.sh/security)
- **Law Enforcement & Subpoenas**: [`NAT-LE-2026.11.01`](https://natrium.sh/security)
- **GitHub Sponsors**: [github.com/sponsors/NatriumTechnologies](https://github.com/sponsors/NatriumTechnologies)
- **SecOps & Inquiries**: [`admin@natrium.sh`](mailto:admin@natrium.sh) · [`compliance@natrium.sh`](mailto:compliance@natrium.sh)
