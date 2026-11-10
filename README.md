# NETWORKWALKS-OUATTARA_CHEICK-B083-WK2-CYBERSECURITY-RECON
# 🛡️ Network Reconnaissance & Vulnerability Assessment (Week 2)

Comprehensive passive and active reconnaissance of the target `networkwalks.com` and local network mapping.

## 📌 Project Overview
This project focuses on executing active and passive reconnaissance techniques using native Kali Linux tools, Zenmap network scanning, and Google Hacking Database (GHDB) operators to evaluate target attack surfaces safely and effectively.

---

## 🛠️ Module 1: CLI Reconnaissance (W2-PM1)
Execution of 6 essential reconnaissance commands against `networkwalks.com`:

* **WHOIS (`whois networkwalks.com`):** Domain registered via GoDaddy, hosted on HostGator Name Servers (`NS6135.HOSTGATOR.COM`).
* **WhatWeb (`whatweb networkwalks.com`):** Identified Apache web server, WordPress CMS, Bootstrap 7.1.4, and jQuery 3.7.1.
* **NSLookup (`nslookup networkwalks.com`):** Resolved target domain to IP address `192.232.216.135` using DNS `8.8.8.8`.
* **Curl (`curl -I https://networkwalks.com`):** Retrieved HTTP/2 200 OK headers, active REST API (`/wp-json/`), and Nginx caching headers.
* **Wafw00f (`wafw00f networkwalks.com`):** Successfully detected Web Application Firewall protection: **ModSecurity (SpiderLabs) WAF**.
* **DNSRecon (`dnsrecon -d networkwalks.com`):** Extracted SOA records, MX mail servers, SPF rules, and cPanel SRV service records.

*(Insérer ici vos captures d'écran de W2-PM1)*

---

## 🌐 Module 2: Network Discovery with Zenmap (W2-PM5)
Local network scanning using Zenmap GUI on Windows host environment:

* **Host IP Address:** `10.20.142.215`
* **Scanned Subnet:** `10.20.142.0/24`
* **Command Executed:** `nmap -sn 10.20.142.0/24` (Ping Scan)
* **Results:** 1 live host identified (`10.20.142.215`). Topology map generated and exported to `Zenmap1.pdf`.

*(Insérer ici vos captures d'écran de Zenmap)*

---

## 🔍 Module 3: Google Hacking & OSINT (W2-PM2)
Reconnaissance using advanced Google Dorks operators and GHDB:

1. **Admin Interfaces (`site:networkwalks.com inurl:admin OR inurl:login`):** 0 results found (No public admin portals exposed).
2. **Exposed Documents (`site:networkwalks.com filetype:pdf`):** Identified 4 public PDF resources (ARP & SNMP Cheat Sheets).
3. **Directory Listing (`site:networkwalks.com intitle:"index of"`):** 0 results found (Directory indexing disabled).
4. **Sensitive Logs/Backups (`site:networkwalks.com ext:log OR ext:sql`):** 0 results found (No backup leaks detected).
5. **GHDB Exploration:** Navigated Exploit-DB GHDB repository targeting vulnerable server categories.

*(Insérer ici vos captures d'écran Google Dorks)*

---

## 🔧 Troubleshooting & Resolution
* **DNS Resolution Error (`wafw00f`):** Encountered temporary `NameResolutionError` during Wafw00f execution due to transient network interface reset. 
* **Resolution:** Re-attempted command execution after connection stabilization, successfully confirming ModSecurity WAF presence.
