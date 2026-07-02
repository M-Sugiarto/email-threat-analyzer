# 🛡️ Email Threat Analyzer — SOC & Management Edition

> **A powerful, client-side email metadata analyzer & threat scoring engine.**
> No backend required — runs 100% in your browser with 9+ free threat intelligence APIs.

<div align="center">

![Version](https://img.shields.io/badge/version-4.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/type-Static%20HTML-orange)
![Made in](https://img.shields.io/badge/Made%20in-Indonesia-red)

[🚀 Live Demo](https://m-sugiarto.github.io/email-threat-analyzer/) • [📖 Documentation](#-usage) • [🐛 Report Bug](https://github.com/mozes-sugiarto/email-threat-analyzer/issues)

</div>

---

## 🎯 Overview

**Email Threat Analyzer** is a comprehensive static HTML tool designed for **SOC analysts** and **security management** to quickly assess email threats. It combines traditional email header analysis with modern threat intelligence APIs.

### ✨ Key Features

- 📋 **Executive Summary (TL;DR)** — Plain-language findings for management
- 🔍 **Deep Technical Analysis** — Full metadata extraction for SOC teams
- 📊 **Weighted Threat Scoring** — 0-100 score across 8 dimensions
- 🚨 **Actionable Recommendations** — Allow / Review / Quarantine / Block
- 🐛 **Debug Mode** — See which APIs succeeded/failed
- 🔌 **9 Free APIs** — All CORS-friendly, no API keys required

---

## 🔌 Threat Intelligence APIs

All APIs are **free, no API key required, and CORS-friendly**:

| API | Purpose | Status |
|-----|---------|--------|
| ✅ [Cloudflare DoH](https://developers.cloudflare.com/1.1.1.1/) | DNSBL reputation (10 blocklists) | Working |
| ✅ [ip-api.com](https://ip-api.com/) | GeoIP / ISP / ASN lookup | Working |
| ✅ [URLhaus](https://urlhaus.abuse.ch/) | Malicious URL database | Working |
| ✅ [Wayback Machine](https://archive.org/) | Domain history & age | Working |
| ✅ [RDAP.org](https://rdap.org/) | Domain registration data | Working |
| ✅ [Shodan InternetDB](https://internetdb.shodan.io/) | IP ports, vulns, hostnames | Working |
| ✅ [GreyNoise](https://www.greynoise.io/) | IP scanner/noise detection | Working |
| ✅ [crt.sh](https://crt.sh/) | Certificate Transparency | Working |
| ✅ [ThreatFox](https://threatfox.abuse.ch/) | IOC lookup (IP/domain) | Working |

---

## 🚀 Quick Start

### Option 1: GitHub Pages (Recommended)

```bash
# 1. Clone this repository
git clone https://github.com/YOUR_USERNAME/email-threat-analyzer.git
cd email-threat-analyzer

# 2. Push to your GitHub
git remote set-url origin https://github.com/YOUR_USERNAME/email-threat-analyzer.git
git push -u origin main

# 3. Enable GitHub Pages:
#    Settings → Pages → Source: Deploy from branch → main → / (root)
# 4. Access at: https://YOUR_USERNAME.github.io/email-threat-analyzer/
