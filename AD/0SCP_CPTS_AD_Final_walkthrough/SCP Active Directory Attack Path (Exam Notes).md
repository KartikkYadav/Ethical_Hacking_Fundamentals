# 🎯 OSCP Active Directory Attack Path (Exam Notes)

---

# 📌 Offensive Active Directory Workflow

## 🔹 1. Lateral Movement
- Goal: Move from initial foothold → other systems/users
- Techniques:
  - Credential reuse
  - Pass-the-Hash
  - Token impersonation

---

## LDAP Enumeration

####  🧠 Purpose:
- Extract domain information
- Enumerate users, groups, and structure

### 🔧 Commands:

    ldapsearch -x -H ldap://<DC-IP> -D '' -w '' -b "DC=domain,DC=local"

    ldapsearch -x -H ldap://<DC-IP> \
    -D 'user@domain.local' -w 'Password123!' \
    -b "DC=domain,DC=local"

### 🎯 Key Findings:
- Users
- Groups
- Domain structure

---

## 🐧 Linux Enumeration

### Tools:
- enum4linux
- enum4linux-ng

### 🔧 Usage:

    enum4linux -a <target>
    enum4linux-ng <target>

### 🎯 Extract:
- Users
- Shares
- Password policy

---

## 🧠 2. BloodHound Enumeration

### Purpose:
- Visualize AD relationships
- Find attack paths

### 🔧 Tools:
- BloodHound
- SharpHound (data collector)

### 🎯 Output:
- Privilege escalation paths
- Kerberos abuse paths

---

## 🔐 3. Access Control Lists (ACL)

### Types:

### DACL (Discretionary ACL)
- Defines permissions
- Who can access what

### SACL (System ACL)
- Logging & auditing

### 🎯 Abuse:
- Write permissions
- GenericAll / GenericWrite

---

## 🔑 4. SMB Password Management

### Purpose:
- Password-related attacks via SMB

### Techniques:
- Password spraying
- Credential reuse

---

## 🔥 5. Kerberoasting Attack

### 🧠 Concept:
- Extract service account tickets (TGS)
- Crack offline

### 🔧 Tool:
- Impacket

### Command:

    GetUserSPNs.py domain.local/user:password -dc-ip <DC-IP> -request

### 🎯 Target:
- Service accounts with SPN

---

## 🔥 6. AS-REP Roasting Attack

### 🧠 Concept:
- Target users without Kerberos pre-auth

### 🔧 Tool:
- Impacket

### Command:

    GetNPUsers.py domain.local/ -dc-ip <DC-IP> -usersfile users.txt -no-pass

### 🎯 Output:
- Crackable hashes

---

## 🐧 7. Re-run Enumeration

- enum4linux / enum4linux-ng again after creds
- Look for:
  - New users
  - Shares
  - Privileges

---

## 💀 8. Mimikatz Usage

### Purpose:
- Extract credentials from memory

### Capabilities:
- Dump hashes
- Extract tickets
- Pass-the-Hash

---

## 🔥 9. Kerberos Abuse with Mimikatz

### Techniques:
- Kerberoasting via Mimikatz
- Ticket extraction

---

## 👑 10. Golden Ticket Attack

### 🧠 Concept:
- Forge Kerberos TGT using KRBTGT hash

### Requirements:
- Domain SID
- KRBTGT hash

### 🎯 Result:
- Full domain admin access

---

## 🧾 FINAL OSCP STRATEGY

### 🔄 Attack Flow:

1. Initial Foothold  
2. LDAP Enumeration  
3. SMB + enum4linux  
4. BloodHound Mapping  
5. Kerberoasting  
6. AS-REP Roasting  
7. Credential Dumping (Mimikatz)  
8. Lateral Movement  
9. ACL Abuse  
10. Golden Ticket (if possible)

---

## ⚠️ EXAM TIPS (IMPORTANT)

- Always:
  - Enumerate first
  - Re-enumerate after creds
- Save:
  - Users
  - Passwords
  - Hashes
- Focus on:
  - Misconfigurations
  - Weak permissions
- Don’t skip:
  - BloodHound
  - Kerberos attacks

--
**Enumerate → Abuse Kerberos → Dump Creds → Move Laterally → Escalate Privileges**

---
