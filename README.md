<!-- Header -->
<div align="center">
  <br/>
  <img src="https://phishguard.qzz.io/assets/images/favicon.png" width="90" alt="PhishGuard" />
  <br/><br/>

  <h1>⚡ PhishGuard</h1>

  <p><strong>Verify Before You Trust</strong></p>
  <p>AI-powered phishing & malicious URL detection — real-time, multi-layer, and built for everyone.</p>

  <br/>

  <a href="https://phishguard.qzz.io">
    <img src="https://img.shields.io/badge/%F0%9F%8C%90%20Live%20Demo-phishguard.qzz.io-22C55E?style=for-the-badge&labelColor=0B0F12" alt="Live Demo"/>
  </a>
  &nbsp;
  <img src="https://img.shields.io/badge/Status-Live%20%26%20Active-22C55E?style=for-the-badge&labelColor=0B0F12" alt="Status"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Source_Code-Private-ff4d4d?style=for-the-badge&labelColor=0B0F12" alt="Private"/>
  &nbsp;
  <img src="https://img.shields.io/badge/ML_Model-450K%20URLs-8B5CF6?style=for-the-badge&labelColor=0B0F12" alt="ML Model"/>

  <br/><br/>

  <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white"/>
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/>
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black"/>
  <img src="https://img.shields.io/badge/Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white"/>

  <br/><br/>
</div>

---

<div align="center">

> 🔒 **This is a public showcase repository.** &nbsp;Source code, backend logic, Firebase config, and security rules are maintained privately.

</div>

---

## 📸 Preview

<div align="center">

### Home
<img src="screenshots/home.png" width="900" alt="PhishGuard Home"/>

<br/>

### URL Scanner
<img src="screenshots/scanner.png" width="900" alt="URL Scanner"/>

<br/>

### Scan Result
<img src="screenshots/scan-result.png" width="900" alt="Scan Result"/>

<br/>

### Dashboard
<img src="screenshots/dashboard.png" width="900" alt="Dashboard"/>

<br/>

### Authentication
<img src="screenshots/login.png" width="900" alt="Login"/>

<br/>

### Mobile View
<img src="screenshots/mobile.png" width="360" alt="Mobile View"/>

</div>

---

## 🧠 What is PhishGuard?

PhishGuard is a cybersecurity web application that helps users evaluate the safety of any URL before visiting it. Instead of drowning users in raw technical data, it translates dozens of security signals into a single, clean visual report — a score, a status, and a clear breakdown of exactly what looks suspicious and why.

No installation. No technical knowledge required. Just paste a URL and get an answer.

---

## 🛡️ Detection Engine — 4 Layers Deep

PhishGuard doesn't rely on a single method. Every scan passes through four independent layers:

```
 ┌─────────────────────────────────────────────────────────────────┐
 │                                                                 │
 │   Layer 1  ░  Blocklist         Known phishing domains          │
 │               ──────────────    Instant match, zero latency     │
 │                    │                                            │
 │   Layer 2  ░  ML Model          Trained on 450,000 URLs         │
 │               ──────────────    21 lexical features per URL     │
 │                    │                                            │
 │   Layer 3  ░  Heuristics        TLDs · Brand impersonation      │
 │               ──────────────    Lookalikes · IP hosts · Keywords│
 │                    │                                            │
 │   Layer 4  ░  VirusTotal API    70+ security engines            │
 │               ──────────────    Final authoritative override    │
 │                                                                 │
 │              ↓  Score  ·  Status  ·  Threat Flags               │
 └─────────────────────────────────────────────────────────────────┘
```

| Layer | Method | Catches |
|:-----:|--------|---------|
| 1 | **Blocklist** | Known phishing domains from a curated dataset |
| 2 | **ML Model** | Novel patterns not yet in any blocklist |
| 3 | **Heuristics** | Suspicious TLDs, lookalike domains, phishing keywords, brand impersonation, IP hosts |
| 4 | **VirusTotal** | Cross-validated against 70+ live security engines |

---

## ✨ Features

<table>
<tr>
<td width="50%" valign="top">

**🔍 URL Scanner**
- Real-time phishing detection
- Safety score `0 – 100`
- `Safe` / `Suspicious` / `Phishing` / `Malicious` classification
- Detailed per-flag threat breakdown
- No login required

**📊 Dashboard**
- 7-day activity line chart
- Threat distribution pie chart
- Animated metric cards
- Searchable scan history table
- CSV export for reports

</td>
<td width="50%" valign="top">

**🧩 Browser Extension**
- Auto-scans every page you visit
- Color-coded badge — 🟢 Safe · 🟡 Suspicious · 🔴 Malicious
- Desktop threat notifications
- iOS-style liquid glass popup UI
- Chrome · Edge · Brave · Opera

**🔐 Authentication**
- Firebase Auth — Google Sign-In + Email
- Firestore — scan history syncs across devices
- Graceful fallback to localStorage

</td>
</tr>
</table>

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         User Interfaces                          │
│                                                                  │
│     ┌─────────────────────────┐   ┌──────────────────────────┐  │
│     │      Web App (SPA)      │   │    Browser Extension     │  │
│     │   phishguard.qzz.io     │   │   Manifest V3 · MV3      │  │
│     │  HTML · CSS · Vanilla JS│   │  Chrome · Edge · Brave   │  │
│     └────────────┬────────────┘   └─────────────┬────────────┘  │
└──────────────────┼──────────────────────────────┼───────────────┘
                   │                              │
                   ▼                              ▼
┌──────────────────────────────────────────────────────────────────┐
│                  Netlify Serverless Function                      │
│                         /api/scan                                │
│                                                                  │
│    Blocklist  →  ML Model  →  Heuristics  →  VirusTotal API      │
│                                                                  │
│          Returns: score · status · flags · domain info           │
└───────────────────────────┬──────────────────────────────────────┘
                            │
              ┌─────────────┴──────────────┐
              ▼                            ▼
┌─────────────────────┐      ┌──────────────────────────────┐
│   Firebase Auth     │      │      Cloud Firestore          │
│   Google + Email    │      │   users/{uid}/scans           │
└─────────────────────┘      └──────────────────────────────┘
```

---

## 🛠️ Tech Stack

<table>
<tr>
<th>Layer</th>
<th>Technology</th>
<th>Purpose</th>
</tr>
<tr>
<td rowspan="3"><strong>Frontend</strong></td>
<td>HTML5 · CSS3</td>
<td>Semantic markup, glassmorphism design</td>
</tr>
<tr>
<td>Vanilla JavaScript (ES6+)</td>
<td>SPA routing, Canvas charts, animations</td>
</tr>
<tr>
<td>History API</td>
<td>Back-button support, clean URLs</td>
</tr>
<tr>
<td rowspan="3"><strong>Backend</strong></td>
<td>Netlify Functions</td>
<td>Serverless scan API</td>
</tr>
<tr>
<td>VirusTotal API</td>
<td>70+ AV engine cross-validation</td>
</tr>
<tr>
<td>Firebase (Auth + Firestore)</td>
<td>Authentication & cloud storage</td>
</tr>
<tr>
<td rowspan="2"><strong>ML</strong></td>
<td>Python · scikit-learn</td>
<td>Model training pipeline</td>
</tr>
<tr>
<td>450,000-URL dataset</td>
<td>21 lexical features · joblib serving</td>
</tr>
<tr>
<td rowspan="2"><strong>Extension</strong></td>
<td>Chrome Manifest V3</td>
<td>Background monitoring, badge updates</td>
</tr>
<tr>
<td>Chrome Storage · Notifications API</td>
<td>Local history, real-time alerts</td>
</tr>
</table>

---

## 🔭 Roadmap

- [x] URL safety scanner
- [x] 4-layer detection engine
- [x] ML model (450K dataset)
- [x] User dashboard with charts
- [x] Firebase authentication
- [x] Scan history & CSV export
- [x] Browser extension (MV3)
- [ ] Email phishing scanner
- [ ] QR code safety checker
- [ ] SSL certificate deep inspection
- [ ] WHOIS & domain age analysis
- [ ] Password leak detection
- [ ] Threat intelligence integration
- [ ] Mobile app

---

## ⚠️ Disclaimer

PhishGuard is developed for educational, research, and cybersecurity awareness purposes. Security reports are informational and should not replace comprehensive professional security assessments.

---

## 👤 Author

**Rishipratim Karmakar**

Open to discussions, collaboration, and feedback.

---

<div align="center">
  <br/>
  <a href="https://phishguard.qzz.io">
    <img src="https://img.shields.io/badge/%F0%9F%8C%90%20Try%20PhishGuard%20Live-phishguard.qzz.io-22C55E?style=for-the-badge&labelColor=0B0F12" alt="Live Demo"/>
  </a>
  <br/><br/>
  <sub>⭐ Star this repo if you found it useful</sub>
  <br/><br/>
</div>
