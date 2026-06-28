<div align="center">

<img src="screenshots/banner.png" width="100%" alt="PhishGuard — Verify Before You Trust" />

<br/>
<br/>

<a href="https://phishguard.qzz.io">
  <img src="https://img.shields.io/badge/-%F0%9F%8C%90%20%20Visit%20Live%20Site-22C55E?style=for-the-badge&labelColor=0B0F12&color=22C55E" height="32" />
</a>

<br/>
<br/>

<img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" />
<img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" />
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" />
<img src="https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black" />
<img src="https://img.shields.io/badge/Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white" />
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white" />
<img src="https://img.shields.io/badge/Chrome_Extension-4285F4?style=flat-square&logo=googlechrome&logoColor=white" />

<br/>
<br/>

<img src="https://img.shields.io/badge/Status-Live%20%26%20Active-22C55E?style=flat-square&labelColor=0B0F12" />
<img src="https://img.shields.io/badge/Source%20Code-Private-ff4d4d?style=flat-square&labelColor=0B0F12" />
<img src="https://img.shields.io/badge/ML%20Dataset-450K%20URLs-8B5CF6?style=flat-square&labelColor=0B0F12" />
<img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square&labelColor=0B0F12" />

</div>

<br/>

---

<br/>

## 🛡️ &nbsp; About

**PhishGuard** is a real-time cybersecurity web application that helps users determine whether a URL is safe to visit — before they click it.

Paste any link and get an instant security report with a **safety score**, **risk classification**, and a **detailed breakdown** of every suspicious signal detected. No installation. No technical knowledge needed.

> 🔒 &nbsp; This repository is a **public showcase**. The complete source code, backend logic, Firebase configuration, ML model, and security rules are maintained in a private repository.

<br/>

---

<br/>

## ⚡ &nbsp; Detection Engine

PhishGuard runs every URL through **4 independent layers** — so no single method is a point of failure.

<br/>

<div align="center">

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   ①  BLOCKLIST          Instant lookup against known phishing domains   │
│          │                                                              │
│   ②  ML MODEL           450K-URL trained classifier · 21 URL features  │
│          │                                                              │
│   ③  HEURISTICS         TLDs · Brand spoofing · Lookalikes · Keywords   │
│          │                                                              │
│   ④  VIRUSTOTAL API     Cross-checked against 70+ security engines      │
│          │                                                              │
│          ▼                                                              │
│     Score · Status · Threat Flags                                       │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

</div>

<br/>

<div align="center">

| Score | &nbsp; | Status | Risk Level |
|:---:|:---:|:---|:---|
| `80 – 100` | 🟢 | **Safe** | Low |
| `58 – 79` | 🟡 | **Suspicious** | Medium |
| `32 – 57` | 🟠 | **Phishing** | High |
| `0 – 31` | 🔴 | **Malicious** | Critical |

</div>

<br/>

---

<br/>

## ✨ &nbsp; Features

<br/>

<div align="center">

| 🔍 URL Scanner | 📊 Dashboard |
|:---|:---|
| Real-time phishing detection | 7-day activity line chart |
| Safety score `0 – 100` | Threat distribution pie chart |
| Safe / Suspicious / Phishing / Malicious | Animated live metric cards |
| Per-flag threat breakdown | Searchable scan history table |
| No account required | One-click CSV export |

| 🧩 Browser Extension | 🔐 Authentication |
|:---|:---|
| Auto-scans every URL you visit | Google Sign-In + Email/Password |
| Live badge — 🟢 🟡 🔴 | Scan history synced to Firestore |
| Desktop threat notifications | Works offline with localStorage |
| Liquid glass popup UI | Multi-device sync |
| Chrome · Edge · Brave · Opera | Secure session management |

</div>

<br/>

---

<br/>

## 📸 &nbsp; Screenshots

<br/>

<div align="center">

#### URL Scanner
<img src="screenshots/scanner.png" width="880" />

<br/><br/>

#### Scan Result
<img src="screenshots/scan-result.png" width="880" />

<br/><br/>

#### Dashboard
<img src="screenshots/dashboard.png" width="880" />

<br/><br/>

#### Sign In
<img src="screenshots/login.png" width="880" />

<br/><br/>

</div>

<br/>

---

<br/>

## 🏗️ &nbsp; Architecture

<br/>

```
╔══════════════════════════════════════════════════════════════════════╗
║                          User Interfaces                            ║
║                                                                      ║
║    ┌───────────────────────────┐   ┌────────────────────────────┐   ║
║    │       Web App  (SPA)      │   │     Browser Extension      │   ║
║    │    phishguard.qzz.io      │   │     Chrome Manifest V3     │   ║
║    │    HTML · CSS · JS        │   │     Chrome · Edge · Brave  │   ║
║    └──────────────┬────────────┘   └───────────────┬────────────┘   ║
╚══════════════════╪═══════════════════════════════╪═════════════════╝
                   └─────────────────┬─────────────┘
                                     ▼
╔══════════════════════════════════════════════════════════════════════╗
║              Netlify Serverless Function  ·  /api/scan              ║
║                                                                      ║
║    [Blocklist] → [ML Model] → [Heuristics] → [VirusTotal API]       ║
║                                                                      ║
║              score  ·  status  ·  flags  ·  domain info             ║
╚══════════════════════════╤═══════════════════════════════════════════╝
                           │
             ┌─────────────┴──────────────────┐
             ▼                                ▼
  ┌──────────────────────┐       ┌───────────────────────────┐
  │    Firebase Auth      │       │      Cloud Firestore       │
  │    Google · Email     │       │    users/{uid}/scans       │
  └──────────────────────┘       └───────────────────────────┘
```

<br/>

---

<br/>

## 🛠️ &nbsp; Tech Stack

<br/>

<div align="center">

| Layer | Technology | Purpose |
|:------|:-----------|:--------|
| **Frontend** | HTML5 · CSS3 · Vanilla JS (ES6+) | SPA, glassmorphism UI, Canvas charts |
| **Routing** | History API | Clean URLs, back-button support |
| **Serverless** | Netlify Functions | Scan API endpoint |
| **Threat Intel** | VirusTotal API | 70+ AV engine cross-validation |
| **Auth** | Firebase Authentication | Google Sign-In & Email/Password |
| **Database** | Cloud Firestore | Scan history, user profiles |
| **ML Pipeline** | Python · scikit-learn · joblib | Trained on 450K URLs, 21 features |
| **Extension** | Chrome Manifest V3 | Background monitoring, alerts |

</div>

<br/>

---

<br/>

## 🗺️ &nbsp; Roadmap

<br/>

**Shipped ✅**

- [x] 4-layer URL detection engine
- [x] ML model trained on 450,000 URLs
- [x] Real-time safety scanner
- [x] Interactive dashboard with charts
- [x] Firebase auth & Firestore sync
- [x] CSV export
- [x] Browser extension (Manifest V3)

**Coming Soon 🚧**

- [ ] Email phishing scanner
- [ ] QR code safety checker
- [ ] SSL certificate deep inspection
- [ ] WHOIS & domain age analysis
- [ ] Password leak detection
- [ ] Threat intelligence feed
- [ ] Mobile app

<br/>

---

<br/>

## 👤 &nbsp; Author

Built by **Rishipratim Karmakar** · Open to discussions, collaboration, and feedback.

<br/>

---

<br/>

<div align="center">

<a href="https://phishguard.qzz.io">
  <img src="https://img.shields.io/badge/-%F0%9F%8C%90%20%20Try%20PhishGuard%20Live%20%E2%80%94%20phishguard.qzz.io-22C55E?style=for-the-badge&labelColor=0B0F12&color=22C55E" height="36" />
</a>

<br/><br/>

<sub>⭐ &nbsp; If you found this useful, consider starring the repository</sub>

<br/>

</div>
