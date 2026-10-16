<div align="center">
  <a href="https://natrium.sh">
    <img src="./assets/banner-v6.svg" alt="Natrium Technologies Inc." width="100%" />
  </a>
  <br />
  <br />
  <p>
    <a href="https://natrium.sh"><img src="https://img.shields.io/badge/WEBSITE-NATRIUM.SH-000000?style=for-the-badge&labelColor=09090b&color=ffffff" alt="natrium.sh" /></a>
    <a href="https://natrium.sh/downloads"><img src="https://img.shields.io/badge/DOWNLOADS-APPS_%26_CLI-000000?style=for-the-badge&labelColor=09090b&color=ffffff" alt="Downloads" /></a>
    <a href="https://github.com/sponsors/NatriumTechnologies"><img src="https://img.shields.io/badge/SPONSOR-GITHUB_SPONSORS-ea4aaa?style=for-the-badge&logo=githubsponsors&logoColor=white" alt="Sponsor" /></a>
    <a href="https://natrium.sh/security"><img src="https://img.shields.io/badge/SECURITY-ENCRYPTED_EMAIL-000000?style=for-the-badge&labelColor=09090b&color=a1a1aa" alt="Security" /></a>
  </p>
  <p>
    <img src="https://img.shields.io/badge/Node.js-09090b?style=flat-square&logo=nodedotjs&logoColor=ffffff" alt="Node.js" />
    <img src="https://img.shields.io/badge/Next.js-09090b?style=flat-square&logo=nextdotjs&logoColor=ffffff" alt="Next.js" />
    <img src="https://img.shields.io/badge/React-09090b?style=flat-square&logo=react&logoColor=ffffff" alt="React" />
    <img src="https://img.shields.io/badge/SQLite-09090b?style=flat-square&logo=sqlite&logoColor=ffffff" alt="SQLite" />
    <img src="https://img.shields.io/badge/Linux-09090b?style=flat-square&logo=linux&logoColor=ffffff" alt="Linux" />
    <img src="https://img.shields.io/badge/Cloudflare-09090b?style=flat-square&logo=cloudflare&logoColor=ffffff" alt="Cloudflare" />
  </p>
</div>

---

### Overview

**Natrium Technologies Inc.** builds fast, private communication software designed from the ground up to protect user privacy. Our flagship product, [**natrium.sh**](https://natrium.sh), is a sovereign encrypted email platform engineered entirely in-house.

- **Custom Outbound & Inbound MTA**: Built our own mail delivery engine from scratch, sending, receiving, and cryptographically verifying emails directly without relying on external email providers.
- **Zero-Knowledge Architecture**: Every message and file attachment is encrypted with AES-256-GCM before storage. Users sign in with hardware Passkeys (WebAuthn) or TOTP 2FA, with zero ads and zero data tracking.
- **Autonomous Local AI**: Scans attachments for threats before download, mitigates phishing in real time, and includes a private, locally hosted AI assistant for drafting and contextual summaries.

---

### Downloads & Installation

Natrium Email is available as standalone desktop applications, mobile packages, and terminal one-liners. All native binaries default directly to the login interface with zero external runtime dependencies.

#### 🪟 Windows

| Edition | Architecture / Format | Download Link |
| :--- | :--- | :--- |
| **64-bit Native App** | `.exe` (x64) | [Download Installer](https://natrium.sh/api/downloads?platform=windows) |
| **Portable** | `.zip` (x64) | [Download Portable](https://natrium.sh/api/downloads?platform=windows_zip) |
| **ARM64** | `.exe` (arm64) | [Download ARM64](https://natrium.sh/api/downloads?platform=windows_arm64) |
| **32-bit Legacy** | `.exe` (ia32) | [Download 32-bit](https://natrium.sh/api/downloads?platform=windows_32) |

**Install via PowerShell** (unblocks the binary automatically):
```powershell
irm https://natrium.sh/install.ps1 | iex
```

---

#### 🐧 Linux

| Package | Format / Distro | Download Link |
| :--- | :--- | :--- |
| **64-bit AppImage** | Universal `.AppImage` (x86_64) | [Download AppImage](https://natrium.sh/api/downloads?platform=linux) |
| **Debian / Ubuntu** | `.deb` (amd64) | [Download .deb](https://natrium.sh/api/downloads?platform=deb) |
| **Fedora / RHEL** | `.rpm` (x86_64) | [Download .rpm](https://natrium.sh/api/downloads?platform=rpm) |
| **ARM64 AppImage** | `.AppImage` (aarch64) | [Download ARM64](https://natrium.sh/api/downloads?platform=linux_arm64) |

**Install via Terminal**:
```bash
curl -fsSL https://natrium.sh/install.sh | bash
```

---

#### 🍎 macOS

| Architecture | Package Format | Download Link |
| :--- | :--- | :--- |
| **Apple Silicon (M1/M2/M3/M4)** | `.dmg` (arm64) | [Download Apple Silicon](https://natrium.sh/api/downloads?platform=mac_arm64) |
| **Intel** | `.dmg` (x64) | [Download Intel DMG](https://natrium.sh/api/downloads?platform=mac_x64) |

Open the `.dmg` and drag **Natrium Email** into your `Applications` folder.

---

#### 📱 Mobile (Android & iOS)

- **Android Universal APK**: [Download Universal APK](https://natrium.sh/api/downloads?platform=android)
- **Android ARM64-v8a APK**: [Download ARM64 APK](https://natrium.sh/api/downloads?platform=android_arm64)
- **iOS (iPhone & iPad PWA)**: Open Safari, navigate to [`https://natrium.sh/?view=login&app=1`](https://natrium.sh/?view=login&app=1), tap the **Share** button, and select **Add to Home Screen**.

> 💡 Full cryptographic SHA-256 checksums and verification instructions are available on the [**Natrium Downloads Portal**](https://natrium.sh/downloads).

---

### Sponsor & Support

Natrium is engineered by an independent solo developer without venture capital, tracking pixels, or corporate data brokering. Because we will **never** sell user data or run advertisements, community sponsorship directly funds our monthly server bills, clean IP reputation fees, Anycast edge routing, and ongoing cryptographic research.

- ❤️ **GitHub Sponsors**: [**github.com/sponsors/NatriumTechnologies**](https://github.com/sponsors/NatriumTechnologies)
- 🌐 **Sponsors & Backers Portal**: [**natrium.sh/sponsors**](https://natrium.sh/sponsors)
- 📄 **Raw Sponsorship Specification**: [**natrium.sh/sponsors.md**](https://natrium.sh/sponsors.md)

---

### Built With

```text
FRONTEND & APP      React · Next.js · Electron · JavaScript · HTML & CSS
BACKEND & DATA      Node.js · SQLite · REST APIs · Custom Inbound/Outbound MTA
SECURITY & AI       AES-256-GCM · WebAuthn Passkeys · TOTP 2FA · Malware Sandbox · Local AI
INFRASTRUCTURE      Linux · Cloudflare Anycast · Automated Audits · Zero-Downtime PM2
```

---

### Contact & Links

- **Webmail**: [https://natrium.sh](https://natrium.sh)
- **Downloads Portal**: [https://natrium.sh/downloads](https://natrium.sh/downloads)
- **Sponsor Page**: [https://natrium.sh/sponsors](https://natrium.sh/sponsors)
- **Security & Transparency**: [https://natrium.sh/security](https://natrium.sh/security)
- **General Inquiries**: [`admin@natrium.sh`](mailto:admin@natrium.sh)
- **Legal & Compliance**: [`compliance@natrium.sh`](mailto:compliance@natrium.sh)
