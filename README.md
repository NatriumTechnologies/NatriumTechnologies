<div align="center">
  <a href="https://natrium.sh">
    <img src="./assets/banner-v7.svg" alt="Natrium Technologies Inc." width="100%" />
  </a>
</div>

### Institutional Mandate

**Natrium Technologies Inc.** is an independent systems and cryptographic engineering firm specializing in sovereign, zero-knowledge communication infrastructure. Our production platform, [**natrium.sh**](https://natrium.sh), delivers end-to-end encrypted email architecture engineered to eliminate single points of surveillance, centralized credential custody, and metadata harvesting.

Unlike legacy webmail services that scan message bodies or proprietary encrypted services reliant on local desktop bridges, Natrium couples client-side cryptographic envelope isolation with an autonomous **Direct-MX Mail Transfer Agent (MTA)**, **pre-vault behavioral malware screening**, **hardware FIDO2 passkeys**, and native **OpenAPI 3.1 & Model Context Protocol (MCP)** interfaces.

---

### Core Architecture & Cryptographic Primitives

Natrium operates under documented formal technical specifications ([`NAT-SEC-2026.11.01`](https://natrium.sh/security)).

```text
[Client Passphrase] ──► [Volatile HMAC-SHA256 Pepper] ──► [scrypt N=32768, r=8, p=1] ──► [Key Encryption Key]
                                                                                                 │
                                                      ┌──────────────────────────────────────────┘
                                                      ▼
[256-bit Random DEK] ──(Encrypted by KEK)──► [Persisted Envelope]
        │
        ├──► Message Bodies, Subjects & Drafts ──► Authenticated AES-256-GCM (Fresh 96-bit IV)
        ├──► Disk Attachment Blobs ─────────────► Authenticated Binary .enc Files
        └──► Inbound External Mail ─────────────► MX Boundary Pre-Vault Inspection
```

- **Zero-Knowledge Envelope Isolation**: Every mailbox maintains an isolated cryptographic key hierarchy. Passphrases undergo server-side HMAC-SHA256 peppering in protected volatile memory followed by memory-hard `scrypt` ($N=32768, r=8, p=1$) requiring 32 MB of contiguous RAM per hash evaluation. A unique 256-bit Data Encryption Key (DEK) is sealed under the user's Key Encryption Key (KEK); plaintext credentials and master keys are never stored.
- **Pre-Vault Multi-Engine Threat Screening**: Inbound external attachments are intercepted at the MX boundary over TLS and analyzed across 70+ threat engines via the VirusTotal API and Falcon Sandbox behavioral reputation heuristics before being sealed into encrypted vault storage.
- **Autonomous Direct-MX Outbound MTA**: Outbound mail resolves recipient MX records directly over TLS 1.3 with Perfect Forward Secrecy. Messages are signed with 2048-bit RSA DKIM keys and enforce strict SPF (`-all`) and DMARC (`p=reject`) alignment backed by DNSSEC. Plaintext attachments are decrypted strictly into volatile memory for MIME streaming.
- **Tracker Neutralization**: Automatic stripping of 1x1 tracking pixels, invisible web beacons, and remote marketing scripts prior to HTML rendering. Zero advertising networks, zero tracking cookies, zero behavioral profiling.
- **Bot-Free, Zero-ID Signup**: No phone numbers, SMS verification, or personal identifiers required. Account reservations are vetted within hours to protect shared outbound SMTP relay reputation.
- **Phishing-Resistant Authentication**: Hardware FIDO2 / WebAuthn passkeys (YubiKey, Apple Touch ID / Face ID, Windows Hello) and RFC 6238 TOTP authenticators supported across all accounts.

---

### Programmatic & Agent Endpoints

Natrium provides standardized programmatic interfaces for developer tooling, command-line automation, and autonomous AI agents:

- **OpenAPI 3.1 Specification**: Documented REST endpoints for message transmission, mailbox synchronization, folder management, and cryptographic vault operations.
- **Model Context Protocol (MCP)**: Native server integration allowing autonomous agents to query, synthesize, and dispatch communications within strict security parameters.
- **Agent-to-Agent (A2A)**: Authenticated, zero-knowledge communication channels for distributed multi-agent architectures.

---

### Client Distribution

Native binaries are self-contained with zero external runtime dependencies.

```bash
# Unix (Linux & macOS)
curl -fsSL https://natrium.sh/install.sh | bash

# Windows (PowerShell)
irm https://natrium.sh/install.ps1 | iex
```

Direct binary distributions for Windows (`.exe`, portable `.zip`, ARM64), Linux (`.AppImage`, `.deb`, `.rpm`), macOS (`.dmg` Apple Silicon & Intel), Android (`.apk`), and iOS (PWA) are available via the [**Natrium Downloads Portal**](https://natrium.sh/downloads).

---

### Technical Specifications & Legal Repository

Official governance documents, operational standards, and compliance frameworks are published in the Natrium Legal Repository:

- [`NAT-SEC-2026.11.01`](https://natrium.sh/security) — Security Architecture & Cryptographic Hierarchy
- [`NAT-CMP-2026.11.01`](https://natrium.sh/security) — Comparative Systems Architecture (Natrium vs. Legacy)
- [`NAT-TOS-2026.11.01`](https://natrium.sh/security) — Production Terms of Service
- [`NAT-PRIV-2026.11.01`](https://natrium.sh/security) — Zero-Knowledge Privacy Policy
- [`NAT-LE-2026.11.01`](https://natrium.sh/security) — Law Enforcement & Subpoena Compliance Standards
- [`NAT-SAF-2026.11.01`](https://natrium.sh/security) — Trust & Safety / Zero-Tolerance Anti-Abuse Policy

---

### Security Operations & Contact

- **Platform Gateway**: [https://natrium.sh](https://natrium.sh)
- **Security & Disclosure**: [https://natrium.sh/security](https://natrium.sh/security)
- **Downloads & Checksums**: [https://natrium.sh/downloads](https://natrium.sh/downloads)
- **GitHub Sponsorship**: [github.com/sponsors/NatriumTechnologies](https://github.com/sponsors/NatriumTechnologies)
- **SecOps Inquiries**: [`admin@natrium.sh`](mailto:admin@natrium.sh)
- **Legal & Compliance**: [`compliance@natrium.sh`](mailto:compliance@natrium.sh)
