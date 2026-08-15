# Full Network Security Assessment Report
**Name:** Ayush Chejara
**Track:** Cyber Security
**Company:** Oasis Infobyte
**Date:** August 15, 2026

---

## 1. Executive Summary
This report presents the findings of a comprehensive network security assessment conducted as part of the Oasis Infobyte Cyber Security Internship. The assessment simulates a real-world penetration test, consisting of network reconnaissance, traffic analysis, and web vulnerability scanning on a controlled local environment (DVWA). 

The primary goal of this assessment was to identify security misconfigurations, unencrypted traffic flows, and web application vulnerabilities that could be exploited by a malicious actor. Several issues were discovered, including the transmission of unencrypted sensitive data over the network and potential web application flaws. Fixing these issues is highly recommended to secure the network infrastructure.

---

## 2. Phase 1: Reconnaissance (Nmap Network Scanning)
**Objective:** To identify active devices, open ports, and running services on the target machine.

**Results (Simulated from Scan):**
*   **Port 80 (HTTP):** Apache httpd 2.4.41 is running.
*   **Port 443 (HTTPS):** Active.
*   **Port 3306 (MySQL):** Database port is open and listening.
*   **Port 22 (SSH):** Open for remote administration.

*Analysis:* The scan revealed several open ports. Open ports running outdated or insecure services represent potential entry points for an attacker. Port 3306 being exposed can be risky if not properly firewalled.

---

## 3. Phase 2: Traffic Analysis (Wireshark Capture)
**Objective:** To monitor and analyze network traffic to identify unencrypted communications and potential data leaks.

**Results (HTTP & DNS Analysis):**
*   **DNS Traffic:** Captured standard DNS queries resolving local and external domains (e.g., DNS A records).
*   **Unencrypted HTTP Traffic:** Captured HTTP GET and POST requests. The login parameters (username and password) were transmitted in plain text.
*   **TCP Handshake:** Successfully captured the 3-way TCP handshake (SYN, SYN-ACK, ACK) establishing the connection.

*Analysis:* Capturing traffic revealed that standard HTTP transmits data in plain text. Without HTTPS (TLS/SSL), any attacker sniffing the network can easily intercept sensitive information, such as passwords or session cookies.

---

## 4. Phase 3: Web Vulnerability Scan (Nikto)
**Objective:** To automate the detection of outdated server software and common web vulnerabilities.

**Results (Simulated from Nikto Log):**
*   + The anti-clickjacking X-Frame-Options header is not present.
*   + The X-XSS-Protection header is not defined. 
*   + The site uses standard HTTP without enforcing HTTPS.
*   + Apache/2.4.41 appears to be outdated.

*Analysis:* The vulnerability scanner flagged several misconfigurations and missing security headers. These issues could allow attacks like Cross-Site Scripting (XSS) or Clickjacking.

---

## 5. Findings Table

| ID  | Description | Severity | Fix / Remediation |
| --- | --- | --- | --- |
| **VULN-01** | Open Unnecessary Ports (Nmap) | Medium | Close unused ports (like 3306 to the public) and implement a strict firewall policy. |
| **VULN-02** | Unencrypted HTTP Traffic (Wireshark) | High | Enforce HTTPS using TLS/SSL certificates for all web communications to encrypt data. |
| **VULN-03** | Missing Security Headers (Nikto) | Low/Medium | Configure the web server to include headers like X-Frame-Options and Content-Security-Policy. |

---

## 6. Remediation Roadmap

To properly secure the infrastructure, the following prioritized roadmap should be followed:

**High Priority (Immediate Action):**
*   **Migrate to HTTPS:** Stop using plaintext HTTP to prevent packet sniffing. (Difficulty: Medium)

**Medium Priority (Next 30 Days):**
*   **Close Risky Ports:** Review the Nmap scan and disable any services/ports that are not strictly required for business operations. (Difficulty: Low)
*   **Update Server Headers:** Apply the recommended security headers found in the Nikto report to prevent client-side attacks. (Difficulty: Low)
