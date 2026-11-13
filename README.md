# NETWORKWALKS-ALEXANDRU-DRUMEA-B084J-WK2-FOOTPRINTING-AND-NETWORK-SCANNING
NetworkWalks Cybersecurity Internship 2026 – Week 2, Project Modules 1 to 5. Hands-on experience with footprinting, reconnaissance, OSINT, Google Hacking, and network discovery.

**Performing passive and active reconnaissance, OSINT gathering, and subnet discovery for ethical hacking and penetration testing**

![](https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000) ![](https://img.shields.io/badge/Batch-B084J-0070C0?style=flat-square&labelColor=000000) ![](https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white) ![](https://img.shields.io/badge/Skill-OSINT-404040?style=flat-square&labelColor=C00000) ![](https://img.shields.io/badge/Network-192.168.56.0%2F24-238F89?style=flat-square&labelColor=000000) ![](https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white) ![](https://img.shields.io/badge/Skill-Reconnaissance-404040?style=flat-square&labelColor=C00000) ![](https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white) ![](https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white) ![](https://img.shields.io/badge/Author-Alexandru%20Drumea-C00000?style=flat-square)

---

## 📌 Project Overview

This project covers the complete practical deliverables of **Week 2** of my Cybersecurity & Ethical Hacking internship at Networkwalks (Batch **B084J**).

The objective is to master **Phase 1 (Reconnaissance & Footprinting)** and **Phase 2 (Scanning & Network Discovery)** of the penetration testing lifecycle. The project demonstrates how an attacker or professional pentester moves from gathering public OSINT intelligence and domain information to mapping live hosts on an internal subnet.

---

## 🎯 Objectives

The main objectives of this week's modules are to:

-   Perform domain footprinting and infrastructure reconnaissance using multiple Kali Linux command-line tools (`whois`, `nslookup`, `curl`, `wafw00f`, `dnsrecon`).
-   Leverage the **Google Hacking Database (GHDB)** and advanced Google Dorks to locate publicly exposed IoT cameras and open directories containing educational PDFs.
-   Conduct visual link analysis and OSINT entity mapping using **Maltego Graph**.
-   Harvest emails, subdomains, and host data using **theHarvester**.
-   Perform host discovery and topology mapping on a local subnet using **Zenmap (Nmap GUI)**.
-   Document findings, risk levels, and actionable security recommendations in a professional report.

---

## 🛡️ Scope & Authorization

All reconnaissance and scanning activities were performed in accordance with authorized educational guidelines:
-   **Target 1:** `networkwalks.com` (secured written permission already provided by the client).
-   **Target 2:** Publicly indexed web assets via GHDB & Microsoft domain (`microsoft.com` passive OSINT).
-   **Target 3:** My own local LAN / VirtualBox Host-Only Network (`192.168.56.1/24`).

⚠️ **Important:** Reconnaissance and scanning must always be conducted strictly within authorized scope. Unauthorized access is illegal.

---

## 🏗️ Modules Completed

| Module ID | Focus Area | Primary Tools Used |
| :--- | :--- | :--- |
| **W2-PM1** | Domain Footprinting & Web Recon | `whois`, `nslookup`, `curl`, `wafw00f`, `dnsrecon` |
| **W2-PM2** | Google Hacking & Advanced Dorking | Google Search, GHDB (Exposed Cameras & Open Directories) |
| **W2-PM3** | OSINT & Visual Graph Mapping | Maltego Graph (Desktop v4.14.0) |
| **W2-PM4** | Email & Subdomain Harvesting | theHarvester (v4.10.1) |
| **W2-PM5** | Local Subnet Scanning & Discovery | Windows CMD (`ipconfig`), Zenmap (Nmap v7.93) |

---

## ⚙️ Environment Configuration

| 🧩 Component | ⚙️ Configuration |
| --- | --- |
| 🖥️ Host OS | Windows 11 / Host-Only Virtual Network (`192.168.56.1/24`) |
| 🐉 Security OS | Kali Linux (VirtualBox Environment) |
| 🎯 Target Domain | `networkwalks.com` |
| 🌐 Target IPv4 | `192.232.216.135` |
| 🛡️ Firewall Detected | ModSecurity (SpiderLabs) WAF |
| 🔎 DNS Name Servers | HostGator (`ns6135.hostgator.com`, `ns6136.hostgator.com` running BIND `9.16.23-RH`) |

---

# 🪜 Activities Performed & Technical Findings

## 1. Footprinting & Reconnaissance (W2-PM1)
- **WHOIS:** Identified registrar GoDaddy, creation date `2019-11-06`, expiry `2027-11-06`, and transfer locks.
- **Nslookup:** Resolved `networkwalks.com` to `192.232.216.135`.
- **Curl:** Inspected HTTP headers exposing Apache server, WordPress cache, `__wpdm_client` cookies, and `/wp-json/` REST API endpoints.
- **Wafw00f:** Confirmed protection behind ModSecurity (SpiderLabs) WAF.
- **DNSRecon:** Enumerated SOA, NS, MX, TXT/SPF records, and 8 SRV autodiscover records.

## 2. Google Hacking & GHDB (W2-PM2)
- Discovered 10 unauthenticated live IP cameras (including MOBOTIX feeds in Buzău and Belgrade) using dorks like `inurl:control/camerainfo`.
- Located 10 open directory listings (`Index of /`) exposing downloadable mathematics books and PDF archives using `intitle:index.of "parent directory" mathematics pdf`.

## 3. OSINT Graph Mapping with Maltego (W2-PM3)
- Executed domain-to-email transforms on `networkwalks.com` in Maltego, successfully harvesting organizational email entity `info@networkwalks.com`.

## 4. Harvesting with theHarvester (W2-PM4)
- Explored passive OSINT collection against `microsoft.com` using public search sources (`-b baidu`) and validated CLI syntax options in Kali Linux.

## 5. Network Scanning with Zenmap (W2-PM5)
- Identified local interface configuration (`192.168.56.1/24`) via `ipconfig`.
- Executed an Nmap Ping Scan (`nmap -sn 192.168.56.1/24`) in Zenmap, discovering active host `192.168.56.1`.
- Generated and exported the network topology diagram in PDF format (`Nmap - Zenmap GUI.pdf`).

---

# 🔍 Risk Analysis Summary

| # | Risk / Finding | Potential Impact | Risk Level |
| :--- | :--- | :--- | :--- |
| **1** | Web server & CMS technology disclosure (`/wp-json/`) | Enables attackers to fingerprint the web stack and research CMS vulnerabilities | **● Medium** |
| **2** | DNS version disclosure & lack of DNSSEC | Exposes BIND daemon version and leaves DNS queries without cryptographic validation | **● Medium** |
| **3** | Unauthenticated IoT cameras indexed via GHDB | Severe privacy breach and unauthorized access to physical surveillance feeds | **● Critical** |
| **4** | Open directory listings enabled (`Index of /`) | Bulk downloading and enumeration of internal or unlinked files | **● Medium** |
| **5** | Public email & domain entity exposure | Harvested corporate emails can be targeted in phishing campaigns | **● Low** |

---

# 💡 What I Learned

Through these modules, I gained practical experience in:
1. **Passive vs. Active Reconnaissance:** Understanding how to gather critical infrastructure intelligence without triggering alarms.
2. **OSINT & Footprinting Tools:** Utilizing industry-standard tools (`whois`, `dnsrecon`, `Maltego`, `theHarvester`) for comprehensive target profiling.
3. **Search Engine Intelligence (GHDB):** Recognizing how misconfigured IoT devices and open directories expose organizations to risk.
4. **Network Discovery:** Using Nmap/Zenmap to map live hosts and subnets safely in a controlled environment.
5. **Professional Reporting:** Documenting findings, risk levels, and remediation steps in a structured penetration testing report.

---

# 👤 Author

**Alexandru Drumea**  
Cybersecurity Professional | Batch **B084J**  

🔗 [LinkedIn Profile](https://www.linkedin.com/in/alex-drumea-7971a8155)

---

## 📌 Project Information

**Program Name:** Cybersecurity Program at Networkwalks  
**Week:** 02  
**Batch:** B084J  
**Modules Covered:** W2-PM1 to W2-PM5  
**Repository:** GitHub
