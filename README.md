# 🛡️ Email Threat Analyzer — SOC & Management Edition

> **A powerful, client-side email metadata analyzer & threat scoring engine.**
> No backend required — runs 100% in your browser with 9 validated free threat intelligence APIs.

<div align="center">

![Version](https://img.shields.io/badge/version-4.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/type-Static%20HTML-orange)
![Made in](https://img.shields.io/badge/Made%20in-Indonesia-red)
![APIs](https://img.shields.io/badge/APIs-9%20free-brightgreen)
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen)

[🚀 Live Demo](https://m-sugiarto.github.io/email-threat-analyzer/) • [📖 Documentation](#-usage) • [🐛 Report Bug](https://github.com/mozes-sugiarto/email-threat-analyzer/issues) • [✨ Request Feature](https://github.com/mozes-sugiarto/email-threat-analyzer/issues)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Quick Start](#-quick-start)
- [Usage](#-usage)
- [Debug Mode](#-debug-mode)
- [Threat Intelligence APIs](#-threat-intelligence-apis)
- [Scoring Engine](#-scoring-engine)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Privacy & Security](#-privacy--security)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

---

## 🎯 Overview

**Email Threat Analyzer** is a comprehensive static HTML tool designed for **SOC analysts (L1/L2)** and **security management** to quickly assess the threat level of suspicious emails. It combines traditional email header analysis with modern threat intelligence APIs to provide:

- 🎯 **Executive Summary (TL;DR)** — Plain-language findings for management
- 🔍 **Deep Technical Analysis** — Full metadata extraction for SOC teams
- 📊 **Weighted Threat Scoring** — 0-100 score across 8 dimensions
- 🚨 **Actionable Recommendations** — Allow / Review / Quarantine / Block
- 🐛 **Debug Mode** — Real-time visibility into all API calls

Perfect for incident response, phishing triage, spam analysis, and security awareness training.

---

## ✨ Features

### 📋 Executive Summary (TL;DR)
- **Management-friendly** plain language findings
- **Email Classification**: Legitimate / Bulk Marketing / Suspicious / Malicious
- **Recommended Action** with clear justification (Allow/Review/Quarantine/Block)
- **Top IOCs** (Indicators of Compromise) highlighted
- **Copy & Print** ready for reports

### 🔍 Deep Technical Analysis
- **Full Header Parsing** — Extract and display all email headers
- **Received Chain Visualization** — Trace email routing hops with timeline
- **Authentication Analysis** — SPF, DKIM, DMARC, ARC, CompAuth
- **SCL / Spam Detection** — Microsoft SCL, Forefront, SpamAssassin, Barracuda
- **Bulk Mail Detection** — Identify marketing ESPs (Mailchimp, SendGrid, etc.)
- **No-Reply & Reply-To Analysis** — Detect mismatches and patterns

### 🌐 IP Intelligence
- **DNSBL Reputation** — Check against 10 blocklists via Cloudflare DoH
- **GeoIP Lookup** — Country, city, ISP, ASN via ip-api.com
- **Shodan InternetDB** — Open ports, known vulnerabilities, hostnames
- **GreyNoise Community** — Distinguish scanners from targeted attacks
- **ThreatFox IOC** — Check if IP is in known malware campaigns

### 🌍 Domain Intelligence
- **Wayback Machine** — Domain age & first-seen history
- **RDAP.org** — Domain registration data
- **crt.sh** — Certificate Transparency logs & subdomain enumeration

### 🔗 URL & Attachment Analysis
- **URLhaus** — Check URLs against known malicious database
- **Phishing Heuristics** — Punycode, brand impersonation, suspicious TLDs
- **Attachment SHA-256** — Hash computation for IOC tracking
- **Dangerous Extension Detection** — 60+ executable file types flagged

### 🐛 Debug Mode (v4.1)
- **Real-time API status** — See which APIs succeeded/failed
- **Console logging** — Detailed logs in browser DevTools
- **Timestamp tracking** — Know exactly when each API was called
- **Error visibility** — Understand why an API might have failed

### 📊 Advanced Scoring Engine
Weighted composite score (0-100) across **8 dimensions**:
- 🔐 Authentication (15%)
- 🌐 IP Reputation (15%)
- 🔍 Enrichment (10%) — Shodan, GreyNoise, ThreatFox
- 🌍 Domain Age (15%)
- 🔗 URL Threats (15%)
- 📎 Attachments (10%)
- 📨 Header Anomalies (10%)
- 🎯 Spam / Bulk (10%)

---

## 🚀 Quick Start

### Option 1: GitHub Pages (Recommended)

    # 1. Fork or clone this repository
    git clone https://github.com/YOUR_USERNAME/email-threat-analyzer.git
    cd email-threat-analyzer
    
    # 2. Push to your GitHub repository
    git remote set-url origin https://github.com/YOUR_USERNAME/email-threat-analyzer.git
    git push -u origin main
    
    # 3. Enable GitHub Pages:
    #    Settings → Pages → Source: Deploy from branch → main → / (root)
    # 4. Access your tool at:
    #    https://YOUR_USERNAME.github.io/email-threat-analyzer/

### Option 2: Local Usage

Simply download `index.html` and open it in any modern browser. No installation required!

### Option 3: Any Static Host

Upload `index.html` to:
- **Netlify** (drag & drop)
- **Vercel**
- **Cloudflare Pages**
- **AWS S3 + CloudFront**
- **Any web server** (Apache, Nginx, etc.)

---

## 📖 Usage

1. **Upload**: Drag & drop `.eml` files or paste raw email source
2. **Analyze**: Wait for the tool to query threat intelligence APIs (~10-30 seconds)
3. **Review TL;DR**: Check the Executive Summary at the top
4. **Debug** (optional): Click 🐛 Debug button to see API status
5. **Deep Dive**: Explore tabs for technical details
6. **Export**: Download full report or print for management

### Supported Input Formats
- ✅ Raw `.eml` files (exported from Outlook, Gmail, Thunderbird)
- ✅ Pasted email source (full headers + body)
- ✅ `.msg` files (partial support)

---

## 🐛 Debug Mode

Introduced in **v4.1**, the Debug Mode provides full visibility into the analysis process:

### How to Use
1. After analysis completes, click the **🐛 Debug** button in the header
2. A panel will expand showing all API calls with timestamps
3. Each entry shows:
    - **Timestamp** — When the API was called
    - **API Name** — Which service was queried
    - **Status** — SUCCESS / WARNING / ERROR
    - **Message** — Detailed result or error

### Example Debug Output

    [14:32:15] Cloudflare DoH: SUCCESS - 198.2.175.96.zen.spamhaus.org → No records
    [14:32:16] ip-api.com: SUCCESS - 198.2.175.96 → Atlanta, United States
    [14:32:17] Shodan: SUCCESS - 198.2.175.96 → 3 ports, 0 vulns
    [14:32:18] GreyNoise: SUCCESS - 198.2.175.96 → noise: false, classification: unknown
    [14:32:19] ThreatFox: SUCCESS - 198.2.175.96 → 0 IOCs found
    [14:32:20] Wayback: SUCCESS - example .org → First seen: 2003-05-12 (8432 days ago)
    [14:32:21] RDAP: SUCCESS - example .org → Registered: 2001-08-15 (9000 days ago)
    [14:32:22] crt.sh: SUCCESS - example .org → 45 certs, 3 recent

### Browser Console
For developers, detailed logs are also available in the browser's DevTools console (F12).

---

## 🔌 Threat Intelligence APIs

All **9 APIs** are **free, no API key required, CORS-friendly, and validated**:

| # | API | Purpose | Rate Limit | Status |
|---|-----|---------|------------|--------|
| 1 | [Cloudflare DoH](https://developers.cloudflare.com/1.1.1.1/) | DNSBL reputation (10 blocklists) | Unlimited | ✅ Validated |
| 2 | [ip-api.com](https://ip-api.com/) | GeoIP / ISP / ASN lookup | 45 req/min | ✅ Validated |
| 3 | [URLhaus](https://urlhaus.abuse.ch/) | Malicious URL database | Free | ✅ Validated |
| 4 | [Wayback Machine](https://archive.org/) | Domain history & age | Free | ✅ Validated |
| 5 | [RDAP.org](https://rdap.org/) | Domain registration data | Free | ✅ Validated |
| 6 | [Shodan InternetDB](https://internetdb.shodan.io/) | IP ports, vulns, hostnames | Free | ✅ Validated |
| 7 | [GreyNoise](https://www.greynoise.io/) | IP scanner/noise detection | Free | ✅ Validated |
| 8 | [crt.sh](https://crt.sh/) | Certificate Transparency | Free | ✅ Validated |
| 9 | [ThreatFox](https://threatfox.abuse.ch/) | IOC lookup (IP/domain) | Free | ✅ Validated |

### DNSBL Blocklists Queried
- zen.spamhaus.org
- bl.spamcop.net
- b.barracudacentral.org
- dnsbl.sorbs.net
- spam.dnsbl.sorbs.net
- psbl.surriel.com
- dyna.spamrats.com
- noptr.spamrats.com
- spam.spamrats.com
- all.s5h.net

---

## 📊 Scoring Engine

### Verdict Thresholds

| Score | Verdict | Action |
|-------|---------|--------|
| 0-14 | ✅ SAFE | Allow — No significant threats |
| 15-29 | ℹ️ LOW | Review — Minor concerns |
| 30-49 | 🔶 MEDIUM | Review — Multiple indicators |
| 50-69 | ⚠️ HIGH | Quarantine — Investigate |
| 70-100 | 🚨 CRITICAL | Block — Clear malicious indicators |

### Email Classification

The tool classifies emails into:
- **Legitimate** — Normal business/personal email
- **Bulk Marketing** — Newsletter, promotional (via ESP detection)
- **Suspicious** — Multiple minor indicators warrant caution
- **Malicious** — High-confidence phishing, malware, or spoofing

### Contextual Penalties
Beyond the weighted scoring, additional penalties are applied for:
- **+25 points** — Bulk mail detected (unsolicited marketing)
- **+10 points** — Reply-To mismatch (common in phishing)

---

## 🏗️ Architecture

    ┌─────────────────────────────────────────────────┐
    │              Browser (Client-Side)              │
    │  ┌───────────────────────────────────────────┐  │
    │  │  PostalMime (Email Parsing)               │  │
    │  │  DOMPurify (XSS Protection)               │  │
    │  │  Web Crypto API (SHA-256 Hashing)         │  │
    │  └───────────────────────────────────────────┘  │
    │                      ↓                          │
    │  ┌───────────────────────────────────────────┐  │
    │  │  Analysis Engine (v4.1)                   │  │
    │  │  • Header Parser                          │  │
    │  │  • Auth Validator (SPF/DKIM/DMARC)        │  │
    │  │  • URL Analyzer                           │  │
    │  │  • Attachment Scanner                     │  │
    │  │  • Bulk Mail Detector                     │  │
    │  │  • Scoring Engine (8 dimensions)          │  │
    │  │  • Executive Summary Generator            │  │
    │  │  • Debug Logger                           │  │
    │  └───────────────────────────────────────────┘  │
    │                      ↓                          │
    │  ┌───────────────────────────────────────────┐  │
    │  │  API Connectors (9 Validated APIs)        │  │
    │  │  Cloudflare • ip-api • URLhaus            │  │
    │  │  Wayback • RDAP • Shodan • GreyNoise      │  │
    │  │  crt.sh • ThreatFox                       │  │
    │  └───────────────────────────────────────────┘  │
    └─────────────────────────────────────────────────┘

---

## 🛠️ Tech Stack

| Component | Technology | Version | License |
|-----------|------------|---------|---------|
| Email Parsing | [PostalMime](https://github.com/nicedoc/postal-mime) | 2.4.0 | MIT |
| XSS Protection | [DOMPurify](https://github.com/cure53/DOMPurify) | 3.1.6 | MIT/Apache-2.0 |
| Hashing | Web Crypto API (Native) | — | — |
| UI | Vanilla HTML/CSS/JS | — | MIT |
| Hosting | GitHub Pages / Any Static Host | — | — |

---

## 🔒 Privacy & Security

### 🛡️ Your Data Stays Local
- **100% client-side processing** — Email content is never sent to any server
- **Only metadata is queried** — IP addresses and suspicious URLs are sent to threat intel APIs
- **No tracking** — No analytics, no cookies, no third-party scripts
- **No storage** — All analysis is ephemeral and cleared on page refresh

### ⚠️ What Gets Sent to APIs
| Data | Sent To | Purpose |
|------|---------|---------|
| Sender IP addresses | Cloudflare, ip-api, Shodan, GreyNoise, ThreatFox | Reputation check |
| Suspicious URLs | URLhaus | Malware database lookup |
| Domain names | Wayback, RDAP, crt.sh | Age & history check |

**Note**: Email body, subject, and personal content are **never** transmitted.

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Ideas for Contributions
- 🌍 Additional language support
- 🔌 More threat intel API integrations
- 📊 Advanced visualization (charts, graphs)
- 🎨 Theme customization (light/dark mode)
- 📱 Mobile optimization
- 🧪 Unit tests

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

    © 2026 Mozes Sugiarto
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.

---

## 🙏 Acknowledgments

### Powered By
- 📧 [PostalMime](https://github.com/nicedoc/postal-mime) — Email parsing
- 🛡️ [DOMPurify](https://github.com/cure53/DOMPurify) — XSS protection
- ☁️ [Cloudflare](https://developers.cloudflare.com/1.1.1.1/) — DNS infrastructure
- 🌐 [ip-api.com](https://ip-api.com/) — GeoIP data
- 🚨 [URLhaus](https://urlhaus.abuse.ch/) — Malware URL database
- 🏛️ [Wayback Machine](https://archive.org/) — Web history
- 📅 [RDAP.org](https://rdap.org/) — Domain registration
- 🔍 [Shodan](https://internetdb.shodan.io/) — Internet scanning
- 📡 [GreyNoise](https://www.greynoise.io/) — Internet noise
- 📜 [crt.sh](https://crt.sh/) — Certificate Transparency
- 🦊 [ThreatFox](https://threatfox.abuse.ch/) — IOC database

### Special Thanks
- The open-source community for amazing free threat intelligence APIs
- SOC analysts worldwide for feedback and real-world use cases
- Everyone who contributed ideas and bug reports

---

<div align="center">

**Made with ❤️ in 🇮🇩 Indonesia**

**© 2026 Mozes Sugiarto** • Licensed under [MIT License](LICENSE)

⭐ If this project helps you, please give it a star!

[⬆ Back to Top](#-email-threat-analyzer--soc--management-edition)

</div>
