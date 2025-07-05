# SQL Injection Vulnerability (OWASP Juice Shop)

## Description
A classic **SQL Injection** flaw was identified in the authentication endpoint of the OWASP Juice Shop application. By injecting malicious SQL code into the login parameters, an attacker can bypass authentication controls and gain unauthorized access.

---

## Environment & Tools
- OWASP Juice Shop (local or Docker): `docker run --rm -p 3000:3000 bkimminich/juice-shop`
- Burp Suite (Community/Professional)
- Browser configured to proxy through Burp Suite (`127.0.0.1:8080`)

---

## Steps to Reproduce
1. Launch Juice Shop and ensure it’s reachable at `http://localhost:3000`.
2. Configure Burp Suite to intercept HTTP traffic.
3. Navigate to the **Login** page.
4. In the login form, enter the following JSON payload and submit:
    ```json
    {
      "email": "' OR 1=1--",
      "password": "TestSQLi"
    }
    ```
5. Intercept and forward the HTTP request via Burp’s **Repeater**.
6. Observe the response containing a valid authentication token and admin user details.

---

## Proof of Concept
![SQL Injection](SQLi.jpg)

---

## Impact
- Bypasses authentication, granting admin-level access without valid credentials.
- Allows full control over the application, including data exfiltration and administrative functions.

---

## Business & Security Risk
- Violates OWASP Top 10 security standards (A03:2021 – Injection).
- Could lead to complete compromise of backend databases and sensitive data.
- Poses severe reputational, regulatory, and financial risks if exploited in production.

---

## Remediation & Mitigation
1. Implement parameterized queries or prepared statements in all database interactions.
2. Use an ORM (e.g., Sequelize, TypeORM) to abstract SQL handling.
3. Validate and sanitize all user inputs on both client and server sides.
4. Employ web application firewalls (WAF) to detect and block malicious injection patterns.

---

*Report generated on July 5, 2025.*
