# 🧠 🔥 Most Common Nmap Scripts (Cheat Sheet)

A practical, pentester-focused list of the most commonly used Nmap NSE scripts, organized by workflow.

---

# 🌐 1. HTTP / Web Enumeration (VERY IMPORTANT)

```
http-title
http-headers
http-enum
http-methods
http-robots.txt
http-server-header
http-auth
http-open-proxy
http-git
http-config-backup
http-backup-finder
http-default-accounts
http-vhosts
http-trace
http-userdir-enum
http-errors
http-security-headers
```

👉 Used in **web pentesting / bug bounty / API recon**

---

# 🔓 2. SMB / Windows (HIGH VALUE)

```
smb-enum-shares
smb-enum-users
smb-enum-domains
smb-enum-groups
smb-os-discovery
smb-protocols
smb-security-mode
smb2-security-mode
smb2-capabilities
smb-vuln-ms17-010
smb-vuln-ms08-067
smb-brute
```

👉 Critical for **Active Directory & internal pentests**

---

# 🔑 3. Authentication / Brute Force

```
ssh-brute
ftp-brute
telnet-brute
http-brute
mysql-brute
rdp-brute
vnc-brute
snmp-brute
```

👉 Used for **weak credential discovery**

---

# 📁 4. FTP Enumeration

```
ftp-anon
ftp-syst
ftp-bounce
ftp-proftpd-backdoor
ftp-vsftpd-backdoor
```

---

# 🔐 5. SSH Enumeration

```
ssh-hostkey
ssh-auth-methods
ssh-brute
ssh2-enum-algos
```

---

# 🛢️ 6. Database Enumeration

## MySQL

```
mysql-info
mysql-databases
mysql-users
mysql-brute
mysql-empty-password
mysql-query
```

## MSSQL

```
ms-sql-info
ms-sql-brute
ms-sql-empty-password
ms-sql-config
```

## MongoDB

```
mongodb-info
mongodb-databases
```

---

# 📡 7. DNS / Network Discovery

```
dns-brute
dns-zone-transfer
dns-recursion
dns-cache-snoop
broadcast-dhcp-discover
broadcast-arp-discovery
```

---

# 🔍 8. General Enumeration

```
banner
service-info
nbstat
rpcinfo
snmp-info
snmp-walk
snmp-processes
snmp-sysdescr
```

---

# 🧨 9. Vulnerability Scripts (MOST USED)

```
vuln
vulners
http-sql-injection
http-xssed
http-csrf
http-dombased-xss
ssl-heartbleed
ssl-poodle
ssl-enum-ciphers
smb-vuln-ms17-010
rdp-vuln-ms12-020
```

👉 These are **gold for bug bounty + HTB + real pentests**

---

# 🔒 10. SSL / TLS Analysis

```
ssl-cert
ssl-enum-ciphers
ssl-heartbleed
ssl-poodle
ssl-dh-params
```

---

# 🧪 11. Misc Useful Scripts

```
whois-domain
traceroute-geolocation
upnp-info
ajp-methods
```

---

# ⚡ 🔥 Real-World Combos (Use This)

## 🚀 Web + API Recon

    nmap -p80,443 --script http* <target>

## 🔥 Full Recon

    nmap -sC -sV --script vuln <target>

## 🧠 Internal Pentest (AD)

    nmap --script smb* <target>

---

# 🎯 Pro Insight (Important)

Instead of remembering scripts:

👉 Think like this:

- Service → Script prefix  
  - HTTP → `http-*`  
  - SMB → `smb-*`  
  - FTP → `ftp-*`  

👉 Then use:

    ls /usr/share/nmap/scripts | grep http

---

# 🚀 Final Takeaway

- These ~70 scripts = **90% of real-world usage**
- Focus on:
  - `http-*` → web/API
  - `smb-*` → AD/internal
  - `vuln` → quick wins
- Combine with `-sC -sV` for maximum output
