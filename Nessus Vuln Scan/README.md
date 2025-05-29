
```markdown
# Vulnerability Assessment Report

## Overview
This project aims to identify security vulnerabilities on a local system using **OpenVAS Community Edition** or **Nessus Essentials**.
# Disclaimer

This project is solely for **educational purposes**. It is intended to demonstrate vulnerability assessment techniques using **OpenVAS Community Edition** and **Nessus Essentials** in a controlled environment.
Unauthorized scanning of systems without explicit permission may violate ethical guidelines and legal regulations. Always ensure compliance with cybersecurity laws and ethical hacking standards.

## Objective
Use free tools to identify common vulnerabilities on your computer.

## Tools Used
- OpenVAS Community Edition (Free vulnerability scanner)
- Nessus Essentials (Free for personal use)

## Methodology
### 1. Installation of the Scanner
Installed OpenVAS/Nessus Essentials on Kali Linux and configured necessary dependencies.

### 2. Setting Up Scan Target
Identified local machine IP using:
```bash
hostname -I
```
Configured scan to target **localhost (127.0.0.1)** or the local IP.

### 3. Executing the Scan
Launched vulnerability scan from the web interface:
- OpenVAS → **https://localhost:9392/**
- Nessus Essentials → **https://localhost:8834/**

### 4. Results & Findings
#### **Scan Information**
- **Start time:** Thu May 29 11:10:23 2025
- **End time:** Thu May 29 11:30:59 2025

#### **Host Information**
- **Netbios Name:** METASPLOITABLE
- **IP:** 192.XXX.XXX.XXX (use host scan )
- **MAC Address:** 00:YY:YY:YY:YY:YY
- **OS:** Linux Kernel 2.6 on Ubuntu 8.04 (Hardy)

#### **Vulnerabilities Identified**
**134862 - Apache Tomcat A JP Connector Request Injection (Ghostcat)**
- **Synopsis:** A vulnerable AJP connector is listening on the remote host.
- **Description:**  
  - A file read/inclusion vulnerability was discovered in the AJP connector.
  - A remote attacker could exploit this to read sensitive web application files.
  - If file uploads are allowed, an attacker could upload malicious JSP code and gain remote code execution (RCE).

**Risk Factor:** **High**  

#### **Solution**
- Update the **AJP** configuration to require authentication.
- Upgrade **Tomcat** to version **7.0.100**, **8.5.51**, **9.0.31** or later.

#### **CVSS Score**
| Version | Base Score | Temporal Score |
|---------|-----------|---------------|
| CVSS v3.0 | **9.8** (Critical) | **9.4** |
| CVSS v2.0 | **7.5** (High) | **6.5** |

#### **Additional References**
- [Nessus Report](http://www.nessus.org/u?8ebe6246)
- [Red Hat CVE-2020-1745](https://access.redhat.com/security/cve/CVE-2020-1745)
- [CISA Known Exploited Vulnerabilities](https://www.cisa.gov/known-exploited-vulnerabilities)

## Recommendations
- Update outdated software.
- Apply security patches.
- Improve firewall configurations.
- Enable additional security hardening measures.

## Installation Guide
### OpenVAS Installation
```bash
sudo apt update && sudo apt install openvas
sudo gvm-setup
sudo gvm-start
```
# Vulnerability Assessment Report

## Overview
This project aims to identify security vulnerabilities on a local system using **OpenVAS Community Edition** or **Nessus Essentials**.

## Objective
Use free tools to identify common vulnerabilities on your computer.

## Tools Used
- OpenVAS Community Edition (Free vulnerability scanner)
- Nessus Essentials (Free for personal use)

## Methodology
### 1. Installation of the Scanner
Installed OpenVAS/Nessus Essentials on Kali Linux and configured necessary dependencies.

### 2. Setting Up Scan Target
Identified local machine IP using:
```bash
hostname -I

### Nessus Essentials Installation
Download Nessus from [Tenable’s website](https://www.tenable.com/products/nessus) and install it:
```bash
sudo dpkg -i Nessus-version.deb
sudo systemctl start nessusd
```

## Running a Scan
1. Open the web interface:
   - OpenVAS → **https://localhost:9392/**
   - Nessus Essentials → **https://localhost:8834/**
2. Set the scan target as **localhost (127.0.0.1)** or your system’s IP.
3. Execute a full vulnerability scan and review results.

## Report & Findings
- After scanning, export results as **PDF** or **HTML**.
- Identify key vulnerabilities and recommend fixes.

---

### Upload to GitHub
To upload this file to your GitHub repository:
```bash
git add README.md
git commit -m "Added vulnerability assessment documentation with Nessus scan results"
git push origin main
```

Report & Findings
- After scanning, export results as PDF or HTML.
- Identify key vulnerabilities and recommend fixes

