# BurpSuite Security Testing Project

<img src="https://img.shields.io/badge/Burp_Suite-Community-FF6633?logo=burp-suite&logoColor=white" alt="Burp Suite">
<img src="https://img.shields.io/badge/OWASP_Top_10-2021-000000?logo=owasp&logoColor=white" alt="OWASP">
<img src="https://img.shields.io/badge/Docker-Required-2496ED?logo=docker&logoColor=white" alt="Docker">
<img src="https://img.shields.io/badge/Security-Penetration_Testing-red" alt="Security">
<img src="https://img.shields.io/badge/Status-Active-success" alt="Status">

Professional security testing documentation for web application vulnerabilities discovered in OWASP Juice Shop using Burp Suite.

## Overview

Comprehensive penetration testing project demonstrating critical web application security vulnerabilities. Each finding includes detailed reproduction steps, visual proof-of-concept, OWASP classification, and remediation strategies.

##  Project Structure

```
├── findings/           # Detailed vulnerability reports
├── screenshots/        # Proof-of-concept evidence
└── README.md          # Project documentation
```

##  Vulnerabilities Discovered

| Vulnerability          | Severity    | OWASP    | Endpoint            | Report                                   |
| ---------------------- | ----------- | -------- | ------------------- | ---------------------------------------- |
| SQL Injection          |  Critical | A03:2021 | `/rest/user/login`  | [View](findings/SQLi.md)                 |
| Sensitive Data Leakage |  Critical | A02:2021 | `/rest/memories`    | [View](findings/SensitiveDataLeakage.md) |
| IDOR                   |  High     | A01:2021 | `/rest/basket/{id}` | [View](findings/IDOR.md)                 |

##  Quick Start

### Prerequisites

- Docker installed
- Burp Suite Community Edition
- Web browser with proxy support

### Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/LakinduQA/Burp-Suite_JuiceShop_Security-Testing
   cd Burp-Suite_JuiceShop_Security-Testing
   ```

2. **Launch target application**

   ```bash
   docker run --rm -p 3000:3000 bkimminich/juice-shop
   ```

3. **Configure Burp Suite**
   - Proxy: `127.0.0.1:8080`
   - Configure browser proxy settings

4. **Review findings** → Navigate to [`findings/`](findings/) directory

##  Testing Methodology

- **Reconnaissance** → Application mapping and endpoint discovery
- **Assessment** → Burp Suite tools (Proxy, Intruder, Repeater)
- **Exploitation** → Proof-of-concept development
- **Documentation** → Comprehensive reporting with evidence

##  Report Structure

Each vulnerability report includes:

- Technical description and attack vectors
- Step-by-step reproduction guide
- Visual proof-of-concept with screenshots
- Business and technical impact analysis
- OWASP Top 10 classification
- Remediation recommendations

##  Disclaimer

**For Educational and Authorized Testing Only**

This project demonstrates security testing techniques on authorized systems. Unauthorized access to computer systems is illegal. Always obtain explicit permission before conducting security assessments.

##  License

MIT License - See LICENSE file for details

---

**Target Application:** OWASP Juice Shop  
**Last Updated:** July 5, 2025  
**Status:** Active Development
