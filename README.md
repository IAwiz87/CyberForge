<div align="center">

<img width="1368" height="768" alt="CyberForge" src="https://github.com/user-attachments/assets/199a01dc-c8c2-4d2d-a5f4-afee766dc2a9" />

# CyberForge

**Open-source tools for federal compliance, vulnerability management, and GRC workflows.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Tools](https://img.shields.io/badge/Tools-1-brightgreen.svg)](#tools)
[![CISA KEV](https://img.shields.io/badge/Data-CISA%20KEV-red.svg)](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/)

</div>

---

## About

CyberForge is a collection of standalone, practical tools built for cybersecurity professionals working in **federal compliance**, **vulnerability management**, and **GRC (Governance, Risk & Compliance)** disciplines.

Every tool in this repository is designed with the same philosophy:

- **No bloat** — minimal or zero dependencies
- **No infrastructure** — runs locally without servers, containers, or cloud accounts
- **No barriers** — open-source, free to use, and built to be understood
- **Compliance-focused** — aligned with NIST, CISA, FedRAMP, and federal security standards

Whether you are tracking known exploited vulnerabilities, preparing for an ATO, or managing a POAM — CyberForge has tools built for that work.

---

## Tools

> 📁 Browse all tools: [`tools/`](tools/)

---

### 🛡️ CISA KEV Browser
> [`tools/cisa-kev-browser/`](https://github.com/IAwiz87/CyberForge/tree/main/tools/cisa-kev-browser)

---

### 📋 FedRAMP Baseline → POA&M Pipeline *(Private)*
> [`tools/fedramp-poam-pipeline/`](https://github.com/IAwiz87/CyberForge/tree/main/tools/fedramp-poam-pipeline)

Combines NIST OSCAL baseline awareness with multi-scanner vulnerability ingestion to produce FedRAMP-compliant POA&M documentation automatically.

| | |
|---|---|
| **Baselines** | LI-SaaS · Low · Moderate · High |
| **Scanners** | Qualys VM · Tenable · Wiz · Generic CSV |
| **SLA windows** | FedRAMP ConMon: Critical=30d · High=90d · Medium=180d · Low=365d |
| **Dependencies** | pandas · openpyxl · python-dateutil |
| **Outputs** | Excel POA&M · HTML Dashboard · Gap Report · Out-of-Scope CSV |

**Key capabilities:**
- 🗺️ Maps every finding to its NIST 800-53 control automatically
- 🎯 Classifies findings as in-scope or out-of-scope for your baseline
- ⏱️ Applies FedRAMP ConMon SLA windows (not generic CVSS dates)
- 🔴 Flags Critical/High findings as FedRAMP 20x KSI triggers
- 📋 Gap report surfaces baseline controls with no findings (scanner blind spots)
- 📊 Standalone HTML dashboard — no server, no install required

**Quick start:**
```bash
cd tools/fedramp-poam-pipeline
pip install -r requirements.txt

# Run against your scan
python FedRAMP_pipeline.py --scan your_scan.csv --baseline Moderate --html

# Test with included samples
python FedRAMP_pipeline.py \
  --scan tests/sample_qualys_scan.csv \
  --baseline Moderate --html
```

📄 [Full documentation](https://github.com/IAwiz87/fedramp-poam-pipeline#readme) · 🔒 [Private repo](https://github.com/IAwiz87/fedramp-poam-pipeline)

A fully standalone, offline-capable browser for the [CISA Known Exploited Vulnerabilities (KEV) Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog).

| | |
|---|---|
| **Catalog entries** | 1,558+ KEVs tracked |
| **Ransomware-confirmed** | 313 vulnerabilities |
| **Data source** | CISA live JSON feed |
| **Dependencies** | Zero (Python stdlib only) |
| **Output** | Single standalone HTML file |

**Key capabilities:**
- 🔍 Full-text search across CVE ID, vendor, product, description, CWE, and notes
- 🎛️ Filter by vendor, ransomware campaign use, CWE, and date range
- 📊 Sortable columns — newest CVEs displayed first by default
- 📋 Detail modal per CVE — required action, due date, NVD/CISA/vendor reference links
- ⚠️ Overdue remediation date highlighting
- 📤 Export any filtered view to CSV
- 🔄 One command to pull the latest data from CISA

**Quick start:**
```bash
# Clone CyberForge with all tools
git clone --recurse-submodules https://github.com/IAwiz87/CyberForge.git
cd CyberForge/tools/cisa-kev-browser

python3 build.py            # fetches latest CISA KEV data
open cisa-kev-browser.html  # open in any browser
```

📄 [Full documentation](https://github.com/IAwiz87/CyberForge/blob/main/tools/cisa-kev-browser/README.md) · 🌐 [Project page](https://iawiz87.github.io/cisa-kev-browser) · 📦 [Standalone repo](https://github.com/IAwiz87/cisa-kev-browser)

---

## Roadmap

Tools planned or in development for this repository:

| Tool | Focus Area | Status |
|------|-----------|--------|
| CISA KEV Browser | Vulnerability Management | ✅ Live |
| FedRAMP Baseline → POA&M Pipeline | FedRAMP / GRC / ATO | Testing_alpha |
| NIST SP 800-53 Control Browser | Compliance / ATO | 🔜 Planned |
| CertForge — FIPS 140-3 Cert. CMVP Readiness Platform | Cryptographic Compliance | 🔜 Planned |

---

## Standards & Frameworks

Tools in this repository are built with awareness of and alignment to:

- [NIST SP 800-53](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) — Security and Privacy Controls
- [NIST CSF 2.0](https://www.nist.gov/cyberframework) — Cybersecurity Framework
- [CISA KEV Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) — Known Exploited Vulnerabilities
- [FedRAMP](https://www.fedramp.gov/) — Federal Risk and Authorization Management Program
- [NIST SP 800-171](https://csrc.nist.gov/publications/detail/sp/800-171/rev-2/final) — CUI Protection
- [FIPS 140-3](https://csrc.nist.gov/publications/detail/fips/140/3/final) — Cryptographic Module Validation

---

## Repository Structure

```
CyberForge/
├── tools/
│   └── cisa-kev-browser/     # CISA KEV standalone browser (submodule)
│       ├── build.py           # fetches latest KEV data from CISA
│       ├── cisa-kev-browser.html  # fully offline standalone app
│       ├── README.md
│       └── docs/              # GitHub Pages project documentation
└── README.md
```

---

## Using This Repo

**Clone with all tools:**
```bash
git clone --recurse-submodules https://github.com/IAwiz87/CyberForge.git
```

**If already cloned without submodules:**
```bash
git submodule update --init --recursive
```

**Update all tools to latest versions:**
```bash
git submodule update --remote --merge
```

---

## Contributing

Have a tool idea focused on federal compliance, vulnerability management, or GRC?
Open an issue or submit a pull request. Contributions that align with the project's
no-bloat, compliance-first philosophy are welcome.

---

## Disclaimer

This repository is an independent open-source project. It is not affiliated with,
endorsed by, or produced by CISA, NIST, or the U.S. Government. Always refer to
official sources for authoritative compliance and security guidance.

---

<div align="center">

**Built for the federal cybersecurity and GRC community**

[🛡️ CISA KEV Browser](https://github.com/IAwiz87/cisa-kev-browser) · [🌐 Project Page](https://iawiz87.github.io/cisa-kev-browser) · [📋 Issues](https://github.com/IAwiz87/CyberForge/issues)

</div>
