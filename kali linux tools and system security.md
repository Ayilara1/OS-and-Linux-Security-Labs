# 🌐 Network Reconnaissance and Traffic Analysis Labs

![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-Network%20Scanner-blue?style=for-the-badge)
![Wireshark](https://img.shields.io/badge/Wireshark-Packet%20Analysis-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![OWASP](https://img.shields.io/badge/OWASP-Security-red?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-Command%20Line-black?style=for-the-badge&logo=linux)

---

# 📖 Overview

This project demonstrates practical reconnaissance, website enumeration, vulnerability assessment, network traffic analysis, and packet inspection using industry-standard cybersecurity tools.

The exercises simulate the early phases of penetration testing and Security Operations Center (SOC) investigations, providing hands-on experience with information gathering, service enumeration, vulnerability identification, and network monitoring.

---

# 🎯 Objectives

- Perform passive and active reconnaissance
- Gather DNS and WHOIS information
- Enumerate websites and technologies
- Discover subdomains and directories
- Perform network and vulnerability scanning
- Analyze network traffic using Wireshark
- Investigate TCP, DNS, HTTP, and HTTPS communications
- Document findings and recommend security improvements

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Target VM | OWASP Broken Web Applications |
| Packet Analyzer | Wireshark |
| Command Line Analyzer | Tshark |
| Network Scanner | Nmap |
| Web Scanner | Nikto |
| Enumeration Tools | WhatWeb, Sublist3r, theHarvester |

---

# Tools Used

- Ping
- Whois
- NSLookup
- WhatWeb
- Sublist3r
- Gobuster
- theHarvester
- Nmap
- Nikto
- Wireshark
- Tshark

---

# Lab 1 – Reconnaissance

## Objective

Gather publicly available information about target domains.

---

## Exercise 1 – Ping Sweep

Domains tested

- Facebook
- Twitter (X)
- Amazon

### Results

| Domain | IP Address |
|---------|------------|
| facebook.com | 102.132.101.35 |
| twitter.com | 104.244.42.1 |
| amazon.com | 54.239.28.8 |

### Observation

Network connectivity to all targets was successful. Packet loss was minimal, indicating stable connectivity during testing.

<img width="975" height="526" alt="image" src="https://github.com/user-attachments/assets/ac0dc1d5-395e-4c53-b97f-1cb2b57aab05" />

---

## Exercise 2 – WHOIS Enumeration

Domains investigated

- GitHub
- LinkedIn
- Apple

### Findings

| Item | Result |
|------|---------|
| GitHub Expiration | 09 October 2026 |
| LinkedIn Registrar | MarkMonitor Inc. |
| Apple Registrant Country | United States |

<img width="975" height="574" alt="image" src="https://github.com/user-attachments/assets/20f941c6-4d31-4747-985c-db2cabaaf111" />

---

## Exercise 3 – DNS Enumeration

Tool

```bash
nslookup
```

Domains

- bbc.co.uk
- netflix.com

### Information Collected

- IP Address
- Name Servers
- DNS Records

<img width="733" height="619" alt="image" src="https://github.com/user-attachments/assets/2e903a5d-cbf0-4375-b0de-108d525bc810" />

---

# Lab 2 – Website Enumeration

## WhatWeb Technology Detection

Targets

- example.com
- stackoverflow.com
- github.com

### Technologies Identified

- HTML5
- Cloudflare
- GitHub Server
- JQuery
- Open Graph Protocol
- HTTP Strict Transport Security
- Content Security Policy

### Security Headers Observed

- X-Frame-Options
- Strict-Transport-Security
- HttpOnly Cookies
- Content Security Policy

<img width="1025" height="288" alt="image" src="https://github.com/user-attachments/assets/4b53da38-2191-4303-abc3-bd4fe87d2d58" />

---

## Aggressive WhatWeb Scan

Targets

- Google
- Facebook

### Information Collected

- Web Server
- HTTP Headers
- HTML Version
- Security Policies
- Country Hosting Information
- Redirect Behaviour

---

<img width="975" height="430" alt="image" src="https://github.com/user-attachments/assets/4a0e2aa0-52e0-44f4-b0a7-2fa6b980814c" />

# Lab 3 – Subdomain Enumeration

## Tool

```bash
Sublist3r
```

### GitHub

Unique subdomains discovered

**95**

Examples

- docs.github.com
- classroom.github.com
- community.github.com
- cloud.github.com
- codespaces.github.com

---

### Google

Unique subdomains discovered

**97**

Examples

- accounts.google.com
- adwords.google.com
- login.corp.google.com
- proxyconfig.corp.google.com

---

<img width="975" height="749" alt="image" src="https://github.com/user-attachments/assets/e24c5d51-70c1-4ecc-b88a-6049ebace0b1" />

## Directory Discovery

Targets

- example.com
- example.org

Tool used

Gobuster

Observation

No publicly accessible directories were discovered.

---

## Email Enumeration

Tool

theHarvester

Information collected

- Email addresses
- Hosts
- DNS Records

---

<img width="975" height="835" alt="image" src="https://github.com/user-attachments/assets/ed0c5e68-f2d7-4e6a-9bbb-23c30aba3966" />

# Lab 4 – Port Scanning and Vulnerability Assessment

## Basic Nmap Scan

Open Ports

| Port | Service |
|-------|----------|
|22|SSH|
|80|HTTP|
|139|NetBIOS|
|143|IMAP|
|443|HTTPS|
|445|SMB|
|5001|Custom Service|
|8080|HTTP Alternate|
|8081|HTTP Alternate|

---

## Service Enumeration

Identified Services

- Apache HTTP Server
- OpenSSH
- Samba
- Courier IMAP
- Apache Tomcat
- Jetty

Operating System

Ubuntu Linux


<img width="975" height="881" alt="image" src="https://github.com/user-attachments/assets/99cf2cc7-c12c-425c-8249-b74e3485a01e" />

<img width="975" height="496" alt="image" src="https://github.com/user-attachments/assets/8aa967ff-d27d-4424-a6a9-1ccc0b82c234" />

---

## Vulnerability Scan

Major vulnerabilities identified

- Apache ByteRange DoS (CVE-2011-3192)
- Weak Diffie-Hellman Parameters
- SSL CCS Injection
- Cross-Domain Policy Misconfiguration
- SMB DoS Vulnerability

<img width="975" height="607" alt="image" src="https://github.com/user-attachments/assets/90722bd0-4354-4173-bec1-e84031ab4017" />

### Risk Assessment

| Vulnerability | Severity |
|--------------|----------|
|Apache DoS|High|
|Weak TLS|High|
|SSL CCS Injection|High|
|SMB DoS|Medium|

---

## Nikto Assessment

Findings included

- Missing X-Frame-Options
- Missing X-Content-Type-Options
- Directory Indexing
- Outdated Apache
- Outdated PHP
- Outdated OpenSSL
- Outdated Python
- Outdated mod_ssl

<img width="975" height="542" alt="image" src="https://github.com/user-attachments/assets/19065c47-d4df-41e0-a061-18807eed354d" />

### Security Recommendation

- Upgrade outdated software
- Disable directory listing
- Implement secure HTTP headers
- Harden TLS configuration

---

# Lab 5 – Network Traffic Analysis

## Tool

Wireshark

---

## Traffic Analysis

Protocols observed

- HTTP
- HTTPS
- DNS
- TCP

### Packet Statistics

| Protocol | Packets |
|-----------|---------|
|HTTP|8|
|DNS|375|

<img width="806" height="456" alt="image" src="https://github.com/user-attachments/assets/09208f7f-f253-4ae2-8e6d-5327fcd9eec7" />

---

## Packet Inspection

Example Packet

| Field | Value |
|---------|------|
|Source IP|10.0.2.15|
|Destination IP|192.168.72.171|
|Protocol|DNS|

---

## TCP Stream Analysis

The TCP conversations were followed to inspect client-server communication.

Observation

HTTPS traffic remained encrypted, preventing inspection of application-layer content.

<img width="796" height="534" alt="image" src="https://github.com/user-attachments/assets/eefc47c1-f9ec-44e8-b8a1-f5d5647a3345" />

---

## IO Graph Analysis

The IO Graph showed bursts of TCP activity followed by periods of lower utilization, indicating normal browsing behaviour rather than sustained flooding or denial-of-service activity.

<img width="905" height="411" alt="image" src="https://github.com/user-attachments/assets/04ef6caa-2cef-4f09-a87d-7a39ede64dae" />

---

# Lab 6 – Advanced Packet Analysis

## Topics Covered

- TCP Handshake
- SYN Flag
- ACK Flag
- HTTP Requests
- HTTPS Handshake
- DNS Queries
- Display Filters

Example Filters

```text
http

dns

tcp

ip.addr==192.168.72.171

tcp.port==80
```

<img width="940" height="491" alt="image" src="https://github.com/user-attachments/assets/d1835563-5785-4197-a1f2-6fdc3a98ac73" />

---

# Key Findings

✅ Successful information gathering

✅ DNS enumeration completed

✅ Website technologies identified

✅ Subdomains discovered

✅ Network services enumerated

✅ Multiple vulnerabilities detected

✅ HTTP and DNS traffic analyzed

✅ TCP sessions investigated

---

# Skills Demonstrated

- Reconnaissance
- OSINT
- DNS Enumeration
- Website Fingerprinting
- Subdomain Discovery
- Directory Enumeration
- Network Scanning
- Vulnerability Assessment
- Packet Analysis
- Traffic Investigation
- Network Security Monitoring
- Wireshark Analysis
- SOC Investigation Techniques

---

# Recommendations

- Upgrade outdated software and libraries.
- Enforce modern TLS configurations.
- Implement secure HTTP response headers.
- Disable unnecessary services and directory indexing.
- Apply the Principle of Least Privilege.
- Continuously monitor network traffic for anomalous behaviour.
- Conduct regular vulnerability assessments and patch management.

---

# Conclusion

This lab provided practical experience in the reconnaissance and analysis phases of cybersecurity assessments. Using tools such as Nmap, WhatWeb, Sublist3r, Nikto, and Wireshark, I successfully gathered intelligence, enumerated services, identified vulnerabilities, and analyzed network traffic. These exercises strengthened my skills in penetration testing, network security, and Security Operations Center (SOC) investigations.

---

## 👨‍💻 Author

**Ayilara Busari Dare**

Electrical Engineer | Cybersecurity Analyst | SOC Analyst | Linux Security Enthusiast | Blue Team Learner
