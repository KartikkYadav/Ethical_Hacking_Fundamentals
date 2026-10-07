# Active Directory Security & Penetration Testing

A structured, hands-on knowledge base for **Active Directory (AD) security, Windows domain environments, enumeration, authentication, access control, lateral movement, and offensive security techniques**.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and is designed as a practical reference for learning, lab development, penetration testing, and red team fundamentals in authorized environments.

---

## Overview

Active Directory is a central identity and access management platform widely used in Windows enterprise environments. Understanding its architecture, authentication protocols, permissions, and administrative relationships is essential for both defensive security and authorized penetration testing.

This collection progresses from building an Active Directory lab to understanding domain architecture, enumeration, authentication, access control, lateral movement, and commonly studied offensive techniques.

---

## Learning Path

**Lab Setup → Windows & Domain Fundamentals → Active Directory Architecture → Enumeration → Remote Management → Access Control → Authentication → Lateral Movement → AD Attack Techniques → Advanced Practice**

---

## Contents

### 01. Active Directory Lab Setup

**[AD Lab Setup Installation](./01.%20AD%20Lab%20Setup%20Installation.md)**

Introduces the environment used for Active Directory security practice and lab-based testing.

### 02. Windows Activation

**[Microsoft Windows Activation](./02.%20Microsoft%20Windows%20Activation.md)**

Reference material related to Windows activation and preparing Windows systems for the laboratory environment.

### 03. Windows Defender & Windows Update

**[Disable Windows Defender and Windows Update](./03.%20Disable%20Windows%20Defender%20and%20Windows%20Update.md)**

Lab-specific configuration notes used to prepare an isolated practice environment.

> These configuration changes should be limited to intentionally isolated laboratory systems.

### 04. Windows Remote Management

**[Windows Remote Management (WinRM)](./04.%20Windows%20Remote%20Management%20(WinRM).md)**

Covers WinRM and its role in remote Windows administration and authorized security testing.

### 05. Domain Controller Setup

**[DC01 Active Directory Setup](./05.%20DC01%20Active%20Directory%20Setup.md)**

Practical notes for setting up a domain controller and building an Active Directory laboratory.

### 06. Remote Desktop Access

**[Remote Desktop Access to a Domain User](./06.%20Remote%20Desktop%20Access%20to%20a%20Domain%20User.md)**

Covers configuring and understanding RDP access for domain users within the lab environment.

### 07. Active Directory Fundamentals

**[Active Directory](./07.%20Active%20Directory.md)**

Core concepts covering Active Directory structure, components, and enterprise identity management.

### 08. Offensive AD Methodology

**[Offensive AD Attack Methodology](./08.%20Offensive%20AD%20%E2%80%93%20Attack%20Methodology.md)**

A structured approach to assessing Active Directory environments during authorized security engagements.

### 09. Evil-WinRM

**[Evil-WinRM](./09%3AEvil_Winrm.md)**

Reference material for Evil-WinRM and remote Windows management in controlled environments.

### 10. Domain Enumeration

**[Domain Enumeration](./10.%20Domain%20Enumeration.md)**

Covers discovery and enumeration of domain information, users, groups, systems, and related Active Directory resources.

### 11. CrackMapExec

**[CrackMapExec](./11.%20CrackMapExec.md)**

Reference material for CrackMapExec and Windows/SMB-oriented assessment workflows.

### 12. Lateral Movement

**[Lateral Movement](./12.Lateral_Movement.md)**

Covers concepts and techniques used to understand movement between systems in an Active Directory environment.

### 13. PowerView

**[PowerView](./13.PowerView.md)**

Reference material for PowerView and PowerShell-based Active Directory enumeration.

### 14. NetExec

**[NetExec](./14.NetExec.md)**

Covers NetExec and its role in network and Windows environment assessment.

### 15. PowerShell

**[PowerShell](./14.PowerShell.md)**

PowerShell fundamentals and practical usage relevant to Windows administration and security testing.

### 16. Access Control Models

**[Access Control Model](./15.Acess_Controll-Model.md)**

Introduces access control concepts relevant to Windows and Active Directory security.

### 17. DACL Lab

**[DACL Lab Setup](./16.DACL_LAB_Setup.md)**

Hands-on material focused on Discretionary Access Control Lists (DACLs) and permission relationships.

### 18. SharpHound & BloodHound

**[SharpHound & BloodHound](./16.Sharphound_&_Bloodhound.md)**

Covers collection and analysis concepts used to understand Active Directory relationships and attack paths.

### 19. BloodHound

**[BloodHound Reference](./17.BloodHound_(Recommended_Over_Sharphound).md.md)**

Additional BloodHound-focused material for analyzing domain relationships and potential privilege paths.

### 20. LDAP Enumeration

**[LDAP Enumeration](./18.LDAP%20Enumeration.md)**

Covers LDAP-based discovery of Active Directory objects and directory information.

### 21. SMB & Password Management

**[SMB Password Management](./20.SMB-Password-Management.md)**

Reference material covering SMB and password-related concepts within Windows environments.

### 22. Kerberos Authentication

**[Kerberos Authentication Protocol](./21Kerberos-Authentication-Protocol.md)**

Introduces Kerberos, a core authentication protocol used by Active Directory.

### 23. Kerberos Enumeration

**[Kerberos Enumeration](./22.Kerberos-Enumeration%20.md)**

Practical reference material for enumerating Kerberos-related information.

### 24. Kerberoasting

**[Kerberoasting Attack](./23.Kerberoasting%20Attack.md)**

Lab-oriented study material covering the Kerberoasting technique and its security implications.

### 25. AS-REP Roasting

**[AS-REP Roasting Attack](./24.AS-REP%20Roasting%20Attack.md)**

Reference material for understanding AS-REP Roasting in Active Directory environments.

### 26. LLMNR & NBT-NS Poisoning

**[LLMNR / NBT-NS Poisoning](./25.%20LLMNR%20-%20NBT-NS%20Poisoning%20in%20Windows.md)**

Covers name-resolution protocols and their security implications in Windows networks.

### 27. OSCP Active Directory Attack Path

**[OSCP Active Directory Attack Path](./26.%20OSCP%20Active%20Directory%20Attack%20Path.md)**

Organized notes for studying Active Directory attack paths in a certification-oriented lab context.

### 28. Mimikatz

**[Mimikatz Usage & Execution](./27.Mimikatz%20Usage%20%26%20Execution.md)**

Reference material covering Mimikatz and credential-related security testing concepts in controlled environments.

### Additional Lab Resources

The directory also contains dedicated practice resources, including:

- [OSCP/CPTS AD Final Walkthrough](./0SCP_CPTS_AD_Final_walkthrough)
- [Main Tunneling Commands](./Main_Tunneling_Command)

---

## Key Security Domains

| Security Domain | Focus |
|---|---|
| AD Fundamentals | Domains, domain controllers, users, groups, and directory structure |
| Enumeration | Domain, LDAP, SMB, Kerberos, users, groups, and services |
| Authentication | Kerberos, NTLM, WinRM, RDP, and related Windows authentication concepts |
| Access Control | Permissions, ACLs, DACLs, and authorization relationships |
| Credential Security | Password-related weaknesses and credential-access concepts |
| Lateral Movement | Remote services and movement between domain systems |
| Attack Path Analysis | BloodHound and relationship-based privilege path analysis |
| Name Resolution | LLMNR and NBT-NS security considerations |
| Offensive Techniques | Kerberoasting, AS-REP Roasting, and other AD attack concepts |
| Windows Administration | PowerShell, WinRM, SMB, and remote management |

---

## Tools & Technologies

The notes in this section reference tools and technologies including:

- **BloodHound**
- **SharpHound**
- **PowerView**
- **NetExec**
- **CrackMapExec**
- **Evil-WinRM**
- **Mimikatz**
- **PowerShell**
- **LDAP**
- **SMB**
- **Kerberos**
- **RDP**
- **WinRM**

---

## Practical Active Directory Assessment Workflow

A structured AD assessment can be approached as:

**1. Understand the Environment**  
Identify domains, domain controllers, hosts, users, groups, trusts, and available services.

**2. Enumerate**  
Collect relevant information through authorized LDAP, SMB, Kerberos, Windows, and network enumeration.

**3. Analyze Authentication & Permissions**  
Review authentication mechanisms, account privileges, group memberships, ACLs, and delegation relationships.

**4. Identify Attack Paths**  
Use relationship analysis to understand possible privilege and lateral movement paths.

**5. Validate Security Weaknesses**  
Safely reproduce relevant findings within the agreed scope and minimize impact on production systems.

**6. Document & Remediate**  
Record evidence, affected assets, security impact, root cause, and remediation guidance.

---

## Active Directory Concepts to Understand

Before moving into advanced offensive techniques, build a strong foundation in:

- Domains and forests
- Domain Controllers
- Users and security groups
- Organizational Units (OUs)
- Group Policy
- LDAP
- SMB
- Kerberos
- NTLM
- WinRM
- RDP
- ACLs and DACLs
- Privileged groups
- Trust relationships
- Authentication and authorization
- Lateral movement concepts

---

## Study Strategy

For a structured progression, study the material in this order:

**Lab Setup → AD Fundamentals → Domain Enumeration → LDAP/SMB Enumeration → PowerShell → WinRM/RDP → Access Control & DACLs → BloodHound → Kerberos → Kerberoasting → AS-REP Roasting → LLMNR/NBT-NS → Lateral Movement → Advanced AD Practice**

The dedicated walkthrough and lab resources can then be used to consolidate the concepts in a controlled environment.

---

## Lab Safety

Some notes in this directory describe configurations or techniques that can weaken security controls or expose credentials when used incorrectly.

Use such material only in:

- Isolated Active Directory laboratories
- Intentionally vulnerable training environments
- Systems you own or are explicitly authorized to assess

Avoid disabling security controls or applying offensive techniques to production infrastructure unless explicitly permitted by the organization's rules of engagement.

---

## Responsible Use

This section is intended for **education, authorized penetration testing, red team training, and defensive security research**.

Do not use Active Directory attack techniques, credential-access tools, or lateral movement methods against systems without explicit authorization.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Additional repository areas cover networking, enumeration, file transfer, privilege escalation, tunneling and port forwarding, wireless security, and information security.

---

## Author

**Kartik Yadav**

Cybersecurity | Active Directory Security | Penetration Testing

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ This section is continuously updated with Active Directory concepts, lab notes, enumeration techniques, security tools, and penetration testing references.
