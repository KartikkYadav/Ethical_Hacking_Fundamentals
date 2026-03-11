# Domain Enumeration

Domain Enumeration is the process of identifying and mapping out the structure, users, groups, permissions, and relationships within an **Active Directory (AD)** environment.

This is a critical phase in both **penetration testing** and **red teaming**, as it helps attackers and defenders understand the **attack surface and privilege paths** within a domain.

---

# Tools for Domain Enumeration

## 1. Active Directory PowerShell Module

Built-in PowerShell module for interacting with Active Directory.

✔ Provides cmdlets for querying users, groups, computers, and permissions.

### Install & Import

```powershell
# Install the module (if needed)
Install-WindowsFeature -Name RSAT-AD-PowerShell

# Import the module
Import-Module ActiveDirectory
```

### Common Enumeration Cmdlets

```powershell
# Get all domain users
Get-ADUser -Filter *

# Get all domain computers
Get-ADComputer -Filter *

# Get all domain groups
Get-ADGroup -Filter *

# Get group members
Get-ADGroupMember -Identity "Domain Admins"

# Get information about a specific user
Get-ADUser -Identity username -Properties *
```

---

# 2. BloodHound

GUI-based tool for visualizing **Active Directory attack paths**.

✔ Uses a **Neo4j database** to map relationships between objects  
✔ Collects data using **SharpHound or BloodHound.py**

### Install BloodHound on Kali

```bash
apt install bloodhound
neo4j console
bloodhound
```

### Launch Neo4j (Default Credentials)

```
URL: http://localhost:7474
Username: neo4j
Password: neo4j (change after first login)
```

### Collect Data with SharpHound

```powershell
Import-Module .\SharpHound.ps1

Invoke-BloodHound -CollectionMethod All -Domain test.local -ZipFileName loot.zip
```

---

# 3. PowerView (Part of PowerSploit)

Pure PowerShell-based tool for domain enumeration.

✔ Can query AD objects, permissions, and relationships without needing admin rights.

### Download & Import

```bash
wget https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Recon/PowerView.ps1
```

```powershell
Import-Module .\PowerView.ps1
```

### Common Enumeration Commands

```powershell
# Get domain users
Get-NetUser

# Get domain groups
Get-NetGroup

# Get group members
Get-NetGroupMember -GroupName "Administrators"

# Get domain computers
Get-NetComputer -FullData

# Find domain trusts
Get-NetDomainTrust
```

---

# 4. SharpHound

C# ingestor for BloodHound (used on Windows).

✔ Faster and more flexible than PowerShell collectors.

### Collect Data with SharpHound

```powershell
Invoke-BloodHound -CollectionMethod All -Domain test.local -ZipFileName loot.zip
```

### Run Executable

```bash
.\SharpHound.exe -c All -d test.local -f loot.zip
```

---

# 5. BloodHound.py

Python-based ingestor for collecting AD data from **Linux/macOS**.

Useful for red teamers **without direct Windows access**.

### Example Command

```bash
bloodhound-python --dns-tcp -u admin -p password123 -ns 192.168.1.10 -d test.local -c All
```

---

# 6. CrackMapExec

Swiss Army knife for **Active Directory enumeration and exploitation**.

✔ Can dump credentials  
✔ Search shares  
✔ Identify misconfigurations

### Example Usage

```bash
crackmapexec smb 192.168.1.0/24 -u user -p password
```

---

# 7. LDAP Enumeration (Using ldapsearch)

Useful for **direct LDAP querying**.

Requires valid credentials or anonymous binding (if allowed).

### Example Command

```bash
ldapsearch -x -h 192.168.1.10 \
-D "CN=Admin,CN=Users,DC=test,DC=local" \
-w "Password123" \
-b "DC=test,DC=local"
```

---

# Enumeration Goals

• Identify **high-value targets** (Domain Admins, Service Accounts)  
• Discover **trust relationships and privilege escalation paths**  
• Understand **permissions and misconfigurations**  
• Map out the **attack surface for lateral movement and persistence**

---

# Pro Tips

• Use **BloodHound** to map attack paths visually  
• Use **PowerView** for fast AD object queries  
• Combine **SharpHound and BloodHound.py** for deeper insights  
• Automate **CrackMapExec** for quick network-wide enumeration

---

# LDAP Enumeration

## LDAP (Lightweight Directory Access Protocol) – Enumeration

---

## Default Ports

| Port | Description |
|-----|-------------|
| 389 | LDAP (unencrypted) |
| 636 | LDAP over SSL (LDAPS) |
| 3268 | Global Catalog (LDAP for Active Directory) |
| 3269 | Global Catalog over SSL |

---

# What is LDAP?

LDAP is a **lightweight protocol** used to access and manage directory information over a network.

Common uses include:

• User authentication  
• Centralized user management  
• Directory services like **Active Directory and OpenLDAP**

LDAP is a simplified version of the **X.500 Directory Access Protocol (DAP)** and communicates over **TCP/IP**.

---

# Common LDAP Implementations

| Platform | Description |
|--------|-------------|
| Microsoft AD | LDAP backend for Windows Domains |
| OpenLDAP | Open-source implementation |
| Novell eDirectory | Enterprise-grade LDAP directory |
| Apple Open Directory | macOS Server directory service |

---

# Authentication & Use Cases

LDAP is commonly used for:

• **Single Sign-On (SSO)**  
• **Central authentication (usernames, passwords)**  

Integration examples:

- Jenkins
- Docker
- Kubernetes
- OpenVPN
- Samba
- Linux PAM

Admins can enforce **user/group-based permissions using LDAP groups across systems**.

---

# Enumeration & Tools

## Goal of LDAP Enumeration

• Gather **user, group, computer, and domain information**  
• Identify potential **privilege escalation paths**  
• Map out the **Active Directory structure**

---

# CLI Tools for LDAP Enumeration

## ldapsearch (Linux-native, part of ldap-utils)

```bash
ldapsearch -x -h <IP> -b "dc=corp,dc=local"
```

Options:

```
-x  : simple authentication
-h  : LDAP server IP/hostname
-b  : base DN (distinguished name)
```

---

## Nmap LDAP Scripts

```bash
nmap -p 389 --script ldap-search <target-ip>
```

---

## enum4linux / enum4linux-ng

Legacy SMB/LDAP enumeration tool.

```bash
enum4linux-ng <target-ip>
```

---

# GUI Tool: JXplorer

Cross-platform **LDAP browser and editor**.

✔ Great for manually browsing directory trees  
✔ Supports SSL/TLS, authentication, and schema viewing

### Install

```bash
apt install jxplorer
```

Official site: https://jxplorer.org

---

# Helpful LDAP Resources

• SUSE LDAP Security Docs  
• Zytrax LDAP Reference Guide  
• JXplorer Website
