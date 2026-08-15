# Task 7: Nikto Vulnerability Scan

**Name:** Ayush Chejara
**Track:** Cyber Security

## Objective
To scan a local web server (DVWA) to find security holes automatically using the Nikto scanning tool.

## Vulnerability Findings & Remediation

**1. Missing X-Frame-Options Header**
*   **What it is / Danger:** The server does not restrict framing, which makes the application vulnerable to Clickjacking attacks (where an attacker tricks a user into clicking something different from what they perceive).
*   **How to Fix:** Configure the web server (Apache) to send the `X-Frame-Options: DENY` or `SAMEORIGIN` header.

**2. Missing X-XSS-Protection Header**
*   **What it is / Danger:** Increases the risk of Cross-Site Scripting (XSS) attacks in older browsers as the built-in XSS filter is not explicitly enabled by the server.
*   **How to Fix:** Add the `X-XSS-Protection: 1; mode=block` header in the server configuration.

**3. No HTTPS Enforcement**
*   **What it is / Danger:** The site operates on standard HTTP, meaning all data (including logins) is transmitted in clear text, making it highly vulnerable to network sniffing.
*   **How to Fix:** Install an SSL/TLS certificate and configure the server to force redirects from HTTP to HTTPS.
