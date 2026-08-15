# Task 7: Nikto Vulnerability Scan

**Name:** Ayush Chejara  
**Track:** Cyber Security  

## Objective
To scan a local web server (DVWA) to find security holes automatically using the Nikto scanning tool.

---

## 📌 Overview
This repository contains the documentation, command logs, and analysis for Task 7 of the Oasis Infobyte Cyber Security Internship. The objective of this task is to perform an automated web vulnerability scan using Nikto, analyze the security posture of a target web application, and document the findings along with remediation steps.

* **Target Environment:** Local Test Server running DVWA (Damn Vulnerable Web Application) at `http://192.168.29.130/dvwa/`
* **Tool Used:** Nikto v2.6.0 on Kali Linux

---

## 🛠️ 1. Installation Steps
To install Nikto on a Debian/Ubuntu/Kali Linux system, execute the following commands in the terminal:
```bash
sudo apt update
sudo apt install nikto

```

---

## 🚀 2. Execution & Commands Used

### A. Basic Scan

To perform a standard vulnerability scan against the target web application:

```bash
nikto -h [http://192.168.29.130/dvwa/](http://192.168.29.130/dvwa/)

```

### B. Saving Output to a File

To save the scan results into a text file for reporting and documentation:

```bash
nikto -h [http://192.168.29.130/dvwa/](http://192.168.29.130/dvwa/) -o nikto_scan_results.txt

```

---

## 🔍 3. Key Concepts & Definitions

* **What is Nikto?**
Nikto is an Open Source (GPL) web server scanner that performs comprehensive tests against web servers for multiple items, including over 6,700 potentially dangerous files/programs, checks for outdated versions of servers, and version-specific problems.
* **Nikto vs. Nmap:**
* **Nmap:** Primarily used for network discovery, port scanning, identifying open ports, and OS detection.
* **Nikto:** Specifically focuses on web servers, going deep into directories, configuration files, and known web vulnerabilities.


* **What is a "Noisy" Scanner?**
Nikto generates a massive volume of HTTP requests in a very short time, which easily triggers alarms in Intrusion Detection Systems (IDS) and Web Application Firewalls (WAF).

---

## 📊 4. Vulnerability Findings & Remediation

### 1. Missing Security Headers (Medium / Low Risk)

* **Finding:** The server response lacks security headers such as `X-Content-Type-Options`, `X-Frame-Options`, and `Content-Security-Policy`.
* **Risk:** Leaves the application vulnerable to Clickjacking, XSS, and MIME-sniffing attacks.
* **Remediation:** Configure the web server (Apache/Nginx) to explicitly send these security headers.

### 2. Outdated Web Server / Component Information (Informational)

* **Finding:** Apache and PHP versions are explicitly revealed in HTTP headers (`Server: Apache/2.4.58`, `X-Powered-By: PHP/8.2.12`).
* **Risk:** Attackers can look up known vulnerabilities corresponding to these specific software versions.
* **Remediation:** Disable version signature disclosure in server configuration files.

### 3. Presence of Default/Example Files (Medium Risk)

* **Finding:** Nikto identified default installation directories and setup scripts.
* **Remediation:** Remove all default files and sample pages from the production web root.

---

## 📸 5. Screenshots

* Terminal scan progress: `![Scan Progress](images/nikto_scan_progress.png)`
* Scan output results: `![Scan Results](images/nikto_results.png)`

---

## 📝 Conclusion

This task demonstrated how automated vulnerability scanners like Nikto help security professionals quickly identify misconfigurations and missing headers in web applications before malicious actors exploit them.

```

```
