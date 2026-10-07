# Enumeration Techniques for Penetration Testing

A practical, structured collection of notes for **reconnaissance, service enumeration, vulnerability discovery, authentication testing, and security assessment workflows** across common network and application services.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and is intended as a hands-on reference for cybersecurity learning, penetration testing practice, and authorized security assessments.

---

## Overview

Enumeration is the process of actively gathering detailed information about systems, services, applications, users, and exposed resources after initial discovery.

This collection progresses from password and exploitation tooling into web, CMS, file-sharing, RPC, SMB, NFS, SQL, SSH, and VNC enumeration.

The notes include both **enumeration fundamentals** and **service-specific testing techniques**, with practical references to tools such as Nmap, Metasploit, Hydra, Gobuster, Dirsearch, WPScan, NetExec, Impacket, Subfinder, dnsx, massdns, SQL clients, and SSH utilities.

---

## Learning Path

**Password & Authentication Testing → Metasploit → General Enumeration → Web Enumeration → CMS Enumeration → FTP/File Services → RPC → SMB → NFS → SQL → SSH → VNC**

---

## Repository Structure

| Section | Focus |
|---|---|
| [01. Password Cracking](./01.Password_Cracking) | Online/offline password testing, wordlists, Hydra, John, Medusa, Patator, and related techniques |
| [02. Metasploit Framework](./02.Metasploit%20Framework) | Modules, auxiliary scanning, exploits, payloads, Meterpreter, and client-side testing |
| [03. Enumeration Techniques](./03.Enumeration%20Techniques%20for%20Penetration%20Testing) | DNS, subdomain discovery, passive/active enumeration, virtual probing, and DNS tooling |
| [04. Web Enumeration](./04.Web_Enumeration) | Web server discovery, directory enumeration, HTTP methods, known web-server weaknesses, and CMS discovery |
| [05. CMS](./05.CMS) | WordPress, Joomla, Drupal, CMS enumeration, vulnerable components, and related testing |
| [06. File Enumeration](./06.File_Enum) | FTP, TFTP, SFTP, file-transfer services, SMB relay, and payload/file-transfer related notes |
| [07. RPC Enumeration](./07.RPC_Enum) | RPC, rpcbind, Microsoft RPC, and RPC enumeration tools |
| [08. SMB Enumeration](./08.SMB_Enum) | SMB discovery, shares, anonymous access, Nmap, NetExec, Impacket, and SMB-related vulnerabilities |
| [09. NFS Enumeration](./09.NFS_Enum) | NFS service discovery and enumeration |
| [10. SQL Enumeration](./10.SQL_Enum) | MySQL and Microsoft SQL Server enumeration, clients, NSE scripts, queries, and credential/hash-related topics |
| [11. SSH Enumeration](./11.SSH_Enum) | SSH host keys, enumeration, key generation, authentication testing, restricted shells, and SSH command execution |
| [12. VNC Enumeration](./12.VNC_Enum) | VNC service/version discovery, password handling, and authentication testing |
| [13. RDP Enumeration](./13.RDP_Enum) | Remote Desktop Protocol fundamentals and enumeration |
| [14. Telnet Enumeration](./14.Telnet_Enum) | Telnet service enumeration and assessment |

---

## 01. Password Cracking

The password-cracking section covers both online and offline approaches used in authorized security testing.

### Topics Covered

- Password-cracking fundamentals
- Password-cracking techniques
- Wordlist creation
- Crunch
- Hydra
- John the Ripper
- Offline password cracking
- Shadow file password testing
- Windows password extraction and cracking
- Document password cracking
- Online authentication testing
- Medusa
- Patator
- Nmap NSE brute-force scripts

This section is useful for understanding how weak credentials can affect the overall security of an environment.

---

## 02. Metasploit Framework

The Metasploit section focuses on using the framework for security testing, service discovery, exploitation, and post-exploitation in controlled environments.

### Topics Covered

- Metasploit fundamentals
- Common commands
- Exploit modules
- Auxiliary modules
- Port scanning with auxiliary modules
- Payloads
- Meterpreter
- Meterpreter post-exploitation
- Client-side attacks
- Windows binary payloads
- Linux binary payloads
- Browser exploits

---

## 03. Enumeration Techniques

This section focuses heavily on **DNS and subdomain enumeration**.

### Topics Covered

- Protocol and port reference
- Enumeration fundamentals
- DNS enumeration
- Passive subdomain enumeration
- Subfinder
- dnsx
- Internet Archive-based discovery
- GitHub subdomain discovery
- Virtual host probing
- Active subdomain enumeration
- DNS zone transfer (AXFR)
- Subdomain brute-forcing
- PureDNS
- Subdomain takeover concepts
- massdns

### Enumeration Workflow

**Passive Discovery → DNS Resolution → Active Enumeration → Virtual Host Discovery → Brute Force → Validation**

---

## 04. Web Enumeration

The web enumeration section focuses on discovering web technologies, directories, files, HTTP behavior, and common web-server weaknesses.

### Topics Covered

- Web enumeration fundamentals
- Web-server identification
- Directory brute-forcing
- Dirsearch
- Gobuster
- Wfuzz
- HTTP methods
- WebDAV
- IIS tilde short-name enumeration
- PHP exploitation
- Tomcat HTTP PUT testing
- Shellshock
- Nostromo
- HFS
- Oracle GlassFish Server
- Webmin
- CMS discovery
- WordPress enumeration with Nmap

This section is especially useful before moving into web application vulnerability testing.

---

## 05. CMS Enumeration

This section focuses on identifying and assessing common content management systems and known vulnerable components.

### Platforms & Topics

**WordPress**
- WordPress enumeration
- WPScan
- XML-RPC
- Plugin-related weaknesses
- Arbitrary file download/upload
- Local file inclusion
- Remote code execution
- Reverse-shell concepts

**Joomla**
- Joomla enumeration
- Joomla CVE-based exploitation references

**Tiki-Wiki**
- Authentication bypass

**Drupal**
- Drupal 7 RCE / Drupalgeddon2

The goal is to understand how CMS fingerprinting and component enumeration can reveal security weaknesses.

---

## 06. File Enumeration

The file-service section covers common file-transfer protocols and related assessment techniques.

### Topics Covered

- FTP enumeration
- TFTP
- SFTP
- TFTP enumeration
- File-transfer utilities
- msfvenom
- SMB relay concepts
- SFTP/FTP vulnerable-service references
- Payload delivery and reverse-shell related notes

---

## 07. RPC Enumeration

RPC enumeration helps identify exposed remote procedure call services and understand their available interfaces.

### Topics Covered

- RPC enumeration fundamentals
- rpcbind
- RPC services
- Microsoft RPC
- RPC enumeration tools

---

## 08. SMB Enumeration

SMB is a major focus because it frequently exposes useful information in Windows and Samba environments.

### Topics Covered

- SMB version detection
- Anonymous/null sessions
- SMB Nmap enumeration
- SMB client
- SMBMap
- Mounting SMB shares
- Impacket
- NetExec
- Metasploit SMB enumeration
- SID enumeration
- Remote service enumeration
- Impacket execution tools
- SMB-related vulnerabilities

### Impacket Coverage

The notes include references for:

- atexec
- psexec
- smbexec
- wmiexec
- getArch
- lookupsid
- samrdump
- Mimikatz-related usage
- services
- registry interaction
- rpcdump

The section also contains references to legacy SMB/Samba vulnerabilities such as **MS08-067**, **MS17-010**, and **Samba-based weaknesses**.

---

## 09. NFS Enumeration

The NFS section provides a focused reference for identifying and assessing **Network File System** services.

### Core Areas

- NFS service discovery
- Export/share enumeration
- Understanding exposed NFS resources

---

## 10. SQL Enumeration

The SQL enumeration section covers both **MySQL** and **Microsoft SQL Server**.

### MySQL

- MySQL enumeration
- Remote access configuration
- Connection testing
- Banner grabbing
- Version detection
- Nmap NSE scripts
- Brute-force testing
- Useful SQL queries
- User-defined functions (UDF)

### Microsoft SQL Server

- MSSQL enumeration
- SQLCMD
- MSSQL client tools
- SQL Server information gathering
- SQL Server hash extraction references

---

## 11. SSH Enumeration

The SSH section focuses on service identification, authentication, keys, and restricted access.

### Topics Covered

- SSH host keys
- SSH enumeration
- SSH key generation
- Public-key authentication testing
- Encrypted private-key cracking
- Running operating-system commands through SSH
- Restricted shells
- Command restrictions

---

## 12. VNC Enumeration

The VNC section contains practical references for assessing remote-desktop services.

### Topics Covered

- VNC enumeration
- VNC version detection
- VNC authentication testing
- VNC password handling/decryption references

---

## 13. RDP Enumeration

The RDP section introduces **Remote Desktop Protocol** and its role in Windows environment assessment.

### Core Areas

- RDP fundamentals
- Service identification
- Remote desktop security considerations

---

## 14. Telnet Enumeration

The Telnet section provides a focused reference for identifying and assessing Telnet services.

### Core Areas

- Telnet service enumeration
- Understanding legacy remote-access exposure
- Security implications of insecure remote administration protocols

---

## Common Tools

The repository references a broad set of penetration-testing and enumeration tools:

**Nmap · Metasploit · Hydra · John the Ripper · Crunch · Medusa · Patator · Subfinder · dnsx · PureDNS · massdns · Gobuster · Dirsearch · Wfuzz · WPScan · SMBMap · NetExec · Impacket · SQLCMD · SSH utilities · cURL**

---

## Practical Enumeration Workflow

A structured service-enumeration workflow can be organized as:

### 1. Reconnaissance

Identify the target scope, IP addresses, domains, and known assets.

### 2. Port & Service Discovery

Use network scanning to identify open ports, protocols, and service versions.

### 3. Service-Specific Enumeration

Choose the appropriate methodology based on the exposed service:

**DNS → Web → SMB → RPC → FTP/TFTP → NFS → SQL → SSH → RDP → VNC → Telnet**

### 4. Information Collection

Record banners, versions, hostnames, usernames, shares, directories, virtual hosts, databases, and other relevant information.

### 5. Vulnerability Identification

Compare the discovered service information with known weaknesses and determine which findings require validation.

### 6. Validation

Safely verify applicable vulnerabilities within the agreed scope while minimizing operational impact.

### 7. Documentation

Document the affected asset, evidence, impact, reproduction steps, risk, and remediation recommendations.

---

## Key Enumeration Principles

Good enumeration should answer:

- **What is exposed?**
- **Which services are running?**
- **What versions are present?**
- **What information is publicly or anonymously accessible?**
- **Which users, shares, directories, hosts, or databases can be identified?**
- **Which findings require further security validation?**
- **What attack surface should be investigated next?**

---

## Recommended Study Order

For a strong foundation, follow this progression:

**Network & Port Identification → DNS/Subdomain Enumeration → Web Enumeration → CMS Enumeration → SMB/RPC → File Services → SQL → SSH → RDP/VNC/Telnet → Metasploit → Authentication Testing**

Practice each topic in an isolated lab before applying the methodology to authorized assessments.

---

## Reporting Checklist

For each enumeration activity, record:

| Item | Example |
|---|---|
| Target | IP, hostname, domain, URL |
| Service | HTTP, SMB, SSH, DNS, SQL, etc. |
| Port | TCP/UDP port |
| Version | Detected service/version |
| Finding | Information disclosure, weak configuration, vulnerable service |
| Evidence | Command output, screenshots, response, or captured metadata |
| Risk | Security impact |
| Validation | Safe reproduction details |
| Recommendation | Hardening or remediation guidance |

---

## Responsible Use

The material in this section is intended for:

**Education · CTFs · Security Labs · Authorized Penetration Testing · Defensive Security Research**

Only enumerate or test systems that you own or have explicit permission to assess.

Some notes reference password testing, exploitation, payloads, credential handling, and known vulnerabilities. Keep these activities within controlled and authorized environments.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Related areas include:

- Active Directory
- Networking
- File Transfer
- Privilege Escalation
- Tunneling & Port Forwarding
- Wireless Pentesting
- Information Security

---

## Author

**Kartik Yadav**

Cybersecurity | Penetration Testing | Ethical Hacking

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical reference for building strong enumeration skills across network services, web technologies, authentication mechanisms, and enterprise protocols.**
