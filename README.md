# BurpSuite Security Testing Project

This repository contains security testing documentation and findings from penetration testing activities conducted on the OWASP Juice Shop application using Burp Suite.

## Project Overview

This project demonstrates various web application security vulnerabilities discovered through systematic penetration testing. The findings are documented with detailed reproduction steps, proof-of-concept screenshots, and remediation recommendations.

## Project Structure

```
BurpSuite - SecTest/
├── findings/                    
│   ├── IDOR.md                 
│   ├── SensitiveDataLeakage.md 
│   └── SQLi.md                 
├── screenshots/                
│   ├── IDOR_Intruder_Attack.png
│   ├── Sensitive_Data_Leakage.png
│   └── SQLi.jpg
└── README.md                   
```

## Vulnerabilities Discovered

### 1. Insecure Direct Object Reference (IDOR)
- **File**: [`findings/IDOR.md`](findings/IDOR.md)
- **Endpoint**: `/rest/basket/{id}`
- **Risk Level**: High
- **OWASP**: A01:2021 – Broken Access Control

### 2. Sensitive Data Leakage
- **File**: [`findings/SensitiveDataLeakage.md`](findings/SensitiveDataLeakage.md)
- **Endpoint**: `/rest/memories`
- **Risk Level**: Critical
- **OWASP**: A02:2021 – Cryptographic Failures

### 3. SQL Injection
- **File**: [`findings/SQLi.md`](findings/SQLi.md)
- **Endpoint**: `/rest/user/login`
- **Risk Level**: Critical
- **OWASP**: A03:2021 – Injection

## Testing Environment

- **Target Application**: OWASP Juice Shop
- **Testing Tool**: Burp Suite (Community Edition)
- **Setup**: `docker run --rm -p 3000:3000 bkimminich/juice-shop`
- **Proxy Configuration**: `127.0.0.1:8080`

## Testing Methodology

1. **Reconnaissance**: Application mapping and endpoint discovery
2. **Vulnerability Assessment**: Systematic testing using Burp Suite tools:
   - Proxy for traffic interception
   - Intruder for automated attacks
   - Repeater for manual testing
3. **Exploitation**: Proof-of-concept development
4. **Documentation**: Detailed reporting with screenshots and remediation steps

## Key Features

- Detailed vulnerability descriptions
- Step-by-step reproduction guides
- Visual proof-of-concept screenshots
- Business impact assessments
- OWASP Top 10 classification
- Comprehensive remediation recommendations

## Risk Assessment Summary

| Vulnerability | Severity | OWASP Category | Status |
|---------------|----------|----------------|---------|
| SQL Injection | Critical | A03:2021 | Documented |
| Sensitive Data Leakage | Critical | A02:2021 | Documented |
| IDOR | High | A01:2021 | Documented |

## Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/LakinduQA/Burp-Suite_JuiceShop_Security-Testing
   cd Burp-Suite_JuiceShop_Security-Testing
   ```

2. **Set up the testing environment**
   ```bash
   docker run --rm -p 3000:3000 bkimminich/juice-shop
   ```

3. **Configure Burp Suite**
   - Set proxy to `127.0.0.1:8080`
   - Configure browser to use Burp proxy

4. **Review findings**
   - Navigate to the `findings/` directory
   - Open any `.md` file to view detailed vulnerability reports

## Documentation Standards

Each vulnerability report includes:
- **Description**: Technical details of the vulnerability
- **Environment & Tools**: Setup requirements
- **Steps to Reproduce**: Detailed reproduction guide
- **Proof of Concept**: Visual evidence with screenshots
- **Impact**: Technical and business impact analysis
- **Remediation**: Specific mitigation recommendations

## Security Considerations

**Important**: This project is for educational and authorized testing purposes only. Do not use these techniques against systems without explicit permission.

## Project Timeline

- **Started**: July 5, 2025
- **Last Updated**: July 5, 2025
- **Current Phase**: Vulnerability Discovery & Documentation

---

## Project Status

**This is an ongoing project and is not yet complete.** Additional vulnerabilities may be discovered and documented as testing continues. Future updates will include:

- Additional vulnerability findings
- Advanced exploitation techniques
- Automated testing scripts
- Comprehensive security assessment report
- Risk mitigation strategies

*Last updated: July 5, 2025*
