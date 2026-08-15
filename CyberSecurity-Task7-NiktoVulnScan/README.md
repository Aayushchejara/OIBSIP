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

## 📌 Overview
This repository contains the documentation, command logs, and analysis for **Task 7** of the Oasis Infobyte Cyber Security Internship. The objective of this task is to perform an automated web vulnerability scan using **Nikto**, analyze the security posture of a target web application, and document the findings along with remediation steps.

* **Target Environment:** Local Test Server running DVWA (Damn Vulnerable Web Application) at `http://192.168.29.130/dvwa/`
* **Tool Used:** Nikto v2.6.0 on Kali Linux

---

## 🛠️ 1. Installation Steps
To install Nikto on a Debian/Ubuntu/Kali Linux system, execute the following commands in the terminal:
```bash
sudo apt update
sudo apt install nikto
