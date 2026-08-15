# Task 1: Nmap Network Scanning

**Objective:** Perform network scanning to identify open ports and services.

**What is Nmap?**
Nmap (Network Mapper) is a free, open-source tool used for network discovery and security auditing. It helps identify devices on a network, open ports, and the services running on them.

**Commands Used:**
* `nmap 10.0.2.15` -> Basic scan to find open ports.
* `nmap -sV 10.0.2.15` -> Identifies software versions running on open ports.
* `sudo nmap -O 10.0.2.15` -> Detects the underlying Operating System.

**Findings & Analysis:**
* **Open Ports:** The scans returned "All 1000 scanned ports on 10.0.2.15 are in ignored states."
* **Security Risk:** This indicates a highly secure, fresh environment with no unnecessarily exposed services. No immediate security risks were detected.

*(Screenshots of the terminal output are attached in this repository folder).*
