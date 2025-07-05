# Insecure Direct Object Reference (OWASP Juice Shop)

## Description
An **Insecure Direct Object Reference** (IDOR) vulnerability was discovered in the `/rest/basket/{id}` endpoint of the OWASP Juice Shop application. By manipulating the `id` parameter, an attacker can access or modify other users' baskets without proper authorization.

---

## Environment & Tools
- OWASP Juice Shop (local or Docker): `docker run --rm -p 3000:3000 bkimminich/juice-shop`
- Burp Suite (Community/Professional)
- Browser configured to proxy through Burp Suite (`127.0.0.1:8080`)

---

## Steps to Reproduce
1. Launch Juice Shop and verify it’s reachable at `http://localhost:3000`.
2. Configure Burp Suite to intercept HTTP traffic.
3. Navigate to the **Baskets** API (e.g., via the frontend or directly via Repeater).
4. In Burp Intruder, set the attack position on the numeric `id` value in the request:
    ```http
    GET /rest/basket/<<id>> HTTP/1.1
    Host: 127.0.0.1:3000
    Authorization: Bearer <valid_token>
    ```
5. Use a simple numeric payload list (e.g., `1–10`) to enumerate baskets.
6. Send the payloads and inspect responses for differences in status codes, lengths, or content to identify valid IDs and unauthorized access.

---

## Proof of Concept
![Insecure Direct Object Reference](screenshots/IDOR - Intruder Attack.png)

---

## Impact
- Unauthorized disclosure and modification of other users’ basket contents.
- Potential privacy violations and data tampering.
- Enables further attacks by leveraging stolen session data or injection of malicious items.

---

## Business & Security Risk
- Violates OWASP Top 10 (A01:2021 – Broken Access Control).
- Can lead to unauthorized actions on behalf of other users.
- May expose personally identifiable information (PII) or purchase history.
- Could damage customer trust and violate data protection laws.

---

## Remediation & Mitigation
1. Enforce robust access control checks on every request.
2. Validate that the `id` parameter belongs to the authenticated user.
3. Implement role-based access controls and object-level authorization.
4. Use indirect references (e.g., mapping numeric IDs to random UUIDs).

---

*Report generated on July 5, 2025.*
