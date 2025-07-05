# Sensitive Data Leakage (OWASP Juice Shop)

## Description
During testing, the application exposed internal debug data, tokens, and configuration details in API responses, leading to **Sensitive Data Leakage**. Attackers can exploit this flaw to harvest secrets or session information.

---

## Environment & Tools
- OWASP Juice Shop (local or Docker): `docker run --rm -p 3000:3000 bkimminich/juice-shop`
- Burp Suite (Community/Professional)
- Browser configured to proxy through Burp Suite (`127.0.0.1:8080`)

---

## Steps to Reproduce
1. Start Juice Shop and confirm it’s reachable at `http://localhost:3000`.
2. Configure Burp Suite to intercept HTTP traffic.
3. Browse the application or call endpoints directly in Burp **Repeater**.
4. Inspect API responses, for example:
    ```http
    GET /api/track-order HTTP/1.1
    Host: 127.0.0.1:3000
    Authorization: Bearer <valid_token>
    ```
5. Observe the JSON response containing internal fields such as debug flags, session tokens, and file paths.

---

## Proof of Concept
![Sensitive Data Leakage](Sensitive Data leakage .png)

---

## Impact
- Disclosure of implementation details and sensitive tokens.
- Enables replay attacks, session hijacking, or targeted exploitation.
- May lead to full account takeover or infrastructure mapping.

---

## Business & Security Risk
- Violates OWASP Top 10 (A02:2021 – Cryptographic Failures).
- Exposes secrets that can be leveraged for further attacks.
- Risks regulatory non-compliance (e.g., GDPR) if PII is leaked.

---

## Remediation & Mitigation
1. Remove debug or verbose error messages in production.
2. Restrict sensitive fields from API responses (use DTOs to filter output).
3. Implement least privilege for tokens and rotate secrets regularly.
4. Use secure HTTP headers and content-security policies to limit data exposure.

---

*Report generated on July 5, 2025.*
