<div align="center">

# 🔬 ForensicAI

### AI-Powered Digital Forensics Investigation Platform

**Keshav Memorial Institute of Technology (KMIT)**
Real Time Research Project (RTRP) — 2025–2026

[![Live Demo](https://img.shields.io/badge/Live%20Demo-forensicai.onrender.com-blue?style=for-the-badge)](https://forensicai.onrender.com)
[![GitHub](https://img.shields.io/badge/GitHub-cybersecurity26%2FForensicAI-black?style=for-the-badge&logo=github)](https://github.com/cybersecurity26/ForensicAI)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://github.com/cybersecurity26/ForensicAI/blob/main/LICENSE)

</div>

---

## 👨‍🎓 Student Details

| Field | Details |
|---|---|
| **Name** | Vinay Vivek |
| **Roll Number** | *(Add Roll Number)* |
| **Branch** | *(Add Branch)* |
| **Year / Semester** | *(Add Year / Semester)* |
| **Course** | RTRP — Real Time Research Projects |
| **Guide / Mentor** | *(Add Faculty Guide Name)* |
| **Academic Year** | 2025 – 2026 |

---

## 📖 About the Project

**ForensicAI** is a full-stack, production-ready digital forensics investigation platform that combines **Artificial Intelligence** with rigorous forensic methodology. It is designed for cybersecurity professionals, incident responders, and digital forensics examiners, providing a unified environment to manage the entire investigation lifecycle — from evidence collection and automated parsing to AI-assisted formal report generation.

The platform is built on the **Human-in-the-Loop (HITL)** principle: AI assists with analysis and drafting, but all conclusions require human review before finalization — ensuring legal defensibility and investigator accountability.

### 🔗 Links
- **Live Application:** https://forensicai.onrender.com
- **Source Code:** https://github.com/cybersecurity26/ForensicAI

---

## ✨ Key Features

| Feature | Description |
|---|---|
| **Case Management** | Create, track, and manage forensic investigations with status lifecycle, priority, and audit trails |
| **Evidence Upload & Parsing** | Drag-and-drop upload supporting LOG, CSV, JSON, TXT, XML, PCAP, EVTX with automatic format detection |
| **SHA-256 Integrity Hashing** | Every uploaded file is immediately hashed for chain-of-custody verification |
| **Timeline Reconstruction** | Unified, filterable event timelines across multiple evidence sources with severity classification |
| **AI Report Generation** | Generates professional forensic reports with Executive Summary, Key Findings, IOCs, and Recommendations |
| **Case RAG Chat Copilot** | Natural language Q&A chatbot over case evidence using Retrieval-Augmented Generation (RAG) |
| **MITRE ATT&CK Mapping** | Automatically correlates parsed log events to MITRE ATT&CK Tactics & Techniques |
| **Threat Intelligence (IOCs)** | Live IP reputation (AbuseIPDB) and malware hash checks (VirusTotal) |
| **Role-Based Access Control** | Administrator, Analyst, Investigator, and Viewer roles with enforced permission boundaries |
| **Case Sharing & Isolation** | Share cases with specific users by email; strict database-level case isolation |
| **WebAuthn Passkeys** | Modern passwordless biometric authentication (W3C WebAuthn standard) |
| **Two-Factor Authentication** | Optional TOTP-based 2FA with authenticator app support |
| **Audit Logging** | Immutable, complete audit trail of every action on the platform |
| **Dark / Light Theme** | Full theme support with smooth transitions |
| **PDF Export** | Server-side forensic report PDF generation |

---

## 🛠️ Tech Stack

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| React | 18.3.1 | UI framework with hooks and functional components |
| Vite | 6.4.1 | Build tool and dev server with HMR |
| React Router | 6 | Client-side routing and navigation |
| Framer Motion | 11 | Smooth page transitions and micro-animations |
| Recharts | 2.14 | Interactive data visualization (charts, pie graphs) |
| Lucide React | 0.460 | Modern, consistent icon library |

### Backend
| Technology | Version | Purpose |
|---|---|---|
| Node.js | 18+ | JavaScript runtime |
| Express.js | 4.21 | REST API framework |
| MongoDB + Mongoose | Atlas + 8.8 | Cloud NoSQL database with ODM |
| JSON Web Tokens | — | Secure token-based session management |
| bcryptjs | — | Password hashing (cost factor 12) |
| Multer | — | File upload middleware |
| Helmet | — | HTTP security headers |
| express-rate-limit | — | API rate limiting |
| PDFKit | 0.15 | Server-side PDF report generation |
| @simplewebauthn | 13.2 | WebAuthn passkey authentication |

### AI Providers (Configurable)
| Provider | Models Supported |
|---|---|
| **OpenAI** | GPT-4, GPT-4o, GPT-3.5-turbo |
| **Google Gemini** | gemini-1.5-pro, gemini-1.5-flash |
| **Mistral AI** | mistral-large, mistral-medium, mistral-small |

### Deployment
| Component | Platform |
|---|---|
| Backend API | Render Web Service |
| Frontend | Render Static Site |
| Database | MongoDB Atlas (Cloud) |

---

## 🏗️ Project Structure

```
ForensicAI/
├── client/                     # React 18 + Vite frontend
│   └── src/
│       ├── pages/              # Dashboard, Cases, Evidence, Timeline,
│       │                       # Reports, Settings, MITRE, IOCs, Chat
│       ├── components/         # Header, Sidebar (reusable)
│       ├── context/            # AuthContext (JWT management)
│       └── api.js              # Centralized API helper
│
├── server/                     # Node.js + Express backend
│   ├── models/                 # Mongoose schemas (Case, Evidence, Report, User, AuditLog)
│   ├── routes/                 # REST API route handlers
│   ├── services/               # aiService.js, threatIntelService.js
│   └── utils/                  # parser.js, attackMapper.js, hash.js
│
└── documentation.md            # Full platform documentation
```

---

## 🔐 Security Architecture

| Layer | Implementation |
|---|---|
| Authentication | JWT with 24h expiry + WebAuthn Passkeys + TOTP 2FA |
| Case Isolation | Database-level `createdBy` + `sharedWith` filtering |
| Password Security | bcrypt hashing with cost factor 12 |
| API Protection | Rate limiting + Helmet HTTP headers |
| File Validation | Server-side extension whitelist on upload |
| Audit Trail | Immutable log of every create / read / update / delete / share |

---

## 📸 Screenshots

> Visit the live application at **https://forensicai.onrender.com** to explore the full interface.

---

## 🚀 How to Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/cybersecurity26/ForensicAI.git
cd ForensicAI

# 2. Setup server
cd server
npm install
cp .env.example .env
# Edit .env with your MongoDB URI, JWT secret, and AI API key
npm run dev

# 3. Setup client (in a new terminal)
cd ../client
npm install
npm run dev

# 4. Open in browser
# http://localhost:5173
```

---

## 📄 License

This project is licensed under the **MIT License**.  
See [LICENSE](https://github.com/cybersecurity26/ForensicAI/blob/main/LICENSE) for details.

---

<div align="center">

**Built with ❤️ at KMIT for the cybersecurity community**

[🌐 Live Demo](https://forensicai.onrender.com) · [📂 Source Code](https://github.com/cybersecurity26/ForensicAI) · [🐛 Report Issue](https://github.com/cybersecurity26/ForensicAI/issues)

</div>
