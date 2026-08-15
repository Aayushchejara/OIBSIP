# Task 8: Wireshark Traffic Capture

**Objective:** Capture and analyze network traffic using Wireshark to understand packets, protocols, and unencrypted communications.

**Tools Used:** Wireshark

**Analysis & Findings:**
* **HTTP Traffic:** Captured plain-text HTTP requests which show that unencrypted data can be easily intercepted and read by malicious actors.
* **DNS Queries:** Observed domain name system lookups resolving human-readable URLs to IP addresses.
* **TCP Handshake:** Analyzed TCP packets showing connection establishment and flags (SYN, ACK).

**Security Risk:** Unencrypted HTTP traffic exposes sensitive information (like credentials and personal data) in cleartext, whereas HTTPS/TLS encrypts the communication channel to prevent sniffing.

*(Screenshots of HTTP, DNS, and TCP filters along with the `.pcap` capture file are attached in this folder).*
